# Companion Software §9 Review Guide — For SKIDS Tech Team

**Reviewers:** Shahid, Raghab Panda (SKIDS Tech Team)
**Scope:** §9 (Companion software workflow) of all 27 protocols
**Purpose:** Confirm every §9 specification is implementable in the current Companion architecture

---

## What §9 contains

Every protocol's §9 specifies:

1. **Doctor Module screens** (typically 7–8 per protocol) — the step-by-step consult flow rendered on the Doctor Module tablet/desktop during a patient visit.
2. **Data fields logged to PHR** — structured data written to the child's permanent health record after each visit.
3. **Alerts** — automated notifications triggered by specific clinical conditions (e.g., vaccination overdue, blood pressure elevated, platelet count critical).
4. **Parent app rendering** — what the parent sees on parent.skids.clinic after the visit.
5. **Auto-generated outputs** — documents the system produces (referral packets, vaccination certificates, action plans, prescriptions).
6. **Edge cases** — offline behaviour, device failure, data conflicts, consent-gated content.

---

## What to review for each protocol

For each protocol, answer these questions:

### Screens
- [ ] Can the Doctor Module render these screens in sequence?
- [ ] Are the form fields (dropdowns, checkboxes, free-text, numeric) supported by the current UI framework?
- [ ] Are auto-calculations feasible? (e.g., BMI from weight/height, BP percentile from age/height/sex tables, GINA control score from 4-item checklist, JADAS from joint count)
- [ ] Are hard-blocks implementable? A hard-block prevents the clinician from proceeding past a screen until a condition is met. Critical hard-blocks in the library:

| Protocol | Hard-block | Description |
|---|---|---|
| B1-08 | Cardiac screen before stimulant | Cannot prescribe methylphenidate without documented cardiac screen (BP, HR, ECG if indicated) |
| B1-19 | G6PD before primaquine | Cannot dispense primaquine without G6PD-normal result in PHR |
| B1-06 | Resuscitation kit before OFC/SPT | Cannot proceed to oral food challenge or skin-prick test without resuscitation-kit checklist confirmed |
| B1-22 | Observation timer | Visit cannot close until 30/60-minute post-vaccination observation timer completes |
| B2-02 | Valproate block for adolescent girls | Warning + override-with-documentation if valproate prescribed to female ≥ 10 years |
| B2-03 | MAS hard-block | If ferritin > 684 + ≥ 2 MAS criteria → §7.1 workflow fires with no override |
| B1-21 | Alarm-feature block | If Hirschsprung alarm features documented → §7.3 fires, blocks functional-constipation management |

### Data fields
- [ ] Do the PHR field names match the database schema? Key fields across protocols:

| Field name | Type | Used by |
|---|---|---|
| `growth_metrics` | object (weight, height, BMI, z_scores, centiles) | A1, B1-09, B1-10 |
| `vaccination_card_reconciled` | boolean | A1, B1-22 |
| `vaccinations_given` | array of objects | B1-22 |
| `asthma_status` | object (control_level, gina_step, meds, fev1, reliever_use) | B1-14, B1-06 (cross-read) |
| `caries_chart` | tooth-level array | B1-04 |
| `tonsillitis_episodes` | array of objects | B1-03 |
| `bp_three_readings` | array of objects with percentile | A1, B1-16, B1-17 |
| `enuresis_classification` | enum | B1-20 |
| `wet_dry_diary` | array of nightly entries | B1-20 |
| `constipation_rome_iv` | boolean | B1-21 |
| `ns_status` | object (phase, proteinuria, albumin, prednisolone_dose) | B1-17 |
| `itp_status` | object (platelet_trend, treatment, response) | B1-18 |
| `seizure_diary` | array with video upload | B2-02 |
| `jadas_score` | number | B2-03 |
| `sledai_score` | number | B2-03 |

- [ ] Are cross-protocol field reads supported? (e.g., B1-06 reading B1-14's `asthma_status`; B1-03 reading B1-07's PSQ score)

### Alerts
- [ ] Can alerts route to the correct recipients via the correct channels?
  - Companion in-app notification → doctor
  - Companion in-app notification → manager
  - WhatsApp → parent (requires WhatsApp Business API integration)
  - Phone call trigger → manager (for high-priority re-engagement)
- [ ] Can alerts fire on data thresholds? (e.g., Hb < 5 → immediate alert; vaccination overdue > 60 days → scheduled alert)

### Parent app
- [ ] Can the parent app render condition-specific content cards?
- [ ] Can adolescent-private content be gated from the parent feed? (B1-13 requires separate adolescent login with confidential content hidden from parent)
- [ ] Can digital trackers be rendered? (wet/dry night diary for B1-20; stool diary for B1-21; peak-flow graph for B1-14; food diary for B1-10)

### Auto-generated outputs
- [ ] Can the system generate printable PDFs? (vaccination certificates, asthma action plans, referral packets, school letters, dental trauma first-aid cards)
- [ ] Can referral packets auto-populate from PHR data? (§7.4 of every protocol specifies the handoff packet contents)

### SKIDS-T3 partner mapping
- [ ] Can Companion map "SKIDS-T3 pediatric ENT surgeon" → the actual partner name, phone, address per clinic location?
- [ ] Is the mapping configurable per SKIDS clinic (Bangalore vs. Hyderabad vs. Delhi will have different T3 partners)?
- [ ] When a §7 trigger fires and the referral packet is generated, does the system populate the T3 partner's contact details automatically?

---

## Priority order for review

1. **A1** — highest-volume protocol; every child uses it; most cross-references
2. **B1-08** — most safety-critical hard-block (cardiac screen before stimulants; suicidality §7.1 workflow)
3. **B1-22** — vaccination observation timer; cold-chain monitoring; most operationally complex
4. **B1-14** — asthma_status cross-protocol field read by B1-06
5. **B1-13** — adolescent-private login architecture
6. **All remaining B1 protocols** — in numerical order
7. **B2-01, B2-02, B2-03** — Tier 2; only at credentialed clinics

---

## Output expected

For each protocol, produce:
- **Feasible / Needs modification / Not feasible** per screen
- **Schema-matched / Needs new field / Needs migration** per data field
- **Implementable / Needs integration** per alert channel
- **Timeline estimate** for any "Needs modification" items

Deliver as a spreadsheet or structured document to Dr. Satish Prasad Rath and the protocol author.
