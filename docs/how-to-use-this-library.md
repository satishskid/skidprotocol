# How to Use the SKIDS Clinical Protocol Library

**Audience:** SKIDS pediatricians, clinic managers, SKIDS Tech Team
**Last updated:** 2026-05-01

---

## What this library is

The SKIDS Clinical Protocol Library is a structured, version-controlled
collection of 27 clinical protocols — one per pediatric specialty service
that SKIDS clinics deliver. It is the single source of truth for:

- What a SKIDS pediatrician does for each condition
- What devices, drugs, and scales are used
- When to refer (and to whom)
- What the parent sees and hears
- What the Companion software should render

Every protocol follows the same 12-section structure. Once you learn
the structure for one protocol, you can navigate all 27.

---

## For SKIDS Pediatricians

### Finding the right protocol

```
protocols/
├── A1-skids-screening/PROTOCOL.md        ← the front door (every child)
├── B1-01-vision/PROTOCOL.md              ← Vision Clinic
├── B1-02-hearing-and-ear/PROTOCOL.md     ← Hearing & Ear
├── B1-03-throat-and-airway/PROTOCOL.md   ← Throat & Airway
├── ...
├── B1-23-developmental-surveillance/PROTOCOL.md
├── B2-01-endocrine/PROTOCOL.md           ← Tier 2 (Fellowship required)
├── B2-02-neurology/PROTOCOL.md           ← Tier 2
└── B2-03-rheumatology/PROTOCOL.md        ← Tier 2
```

The master index is at `protocols/_index.md` — it lists every protocol
with its current status.

### The 12-section structure (every protocol)

| Section | What it answers | When you need it |
|---|---|---|
| **§1 Service definition** | What does this clinic do / not do? | When deciding if a child belongs here |
| **§2 Evidence base** | Which guidelines govern this protocol? | When justifying a clinical decision |
| **§3 Presenting concerns** | How does the child arrive? (parent language → clinical translation) | At the front desk / during triage |
| **§4 Diagnostic workflow** | What to ask, examine, test, and in what order | During the consult |
| **§5 Severity grading** | How bad is it? (with specific thresholds) | After assessment, before treatment |
| **§6 Therapeutic options** | What to prescribe / do / refer (with doses) | Treatment decision |
| **§7 Hard referral triggers** | When does this case leave my scope? | The most important section — safety |
| **§8 Follow-up schedule** | When do I see this child again? | End of consult |
| **§9 Companion software** | What screens does the Doctor Module show? | For tech team (see below) |
| **§10 Parent communication** | What do I say to the parent? (scripted) | During explanation to family |
| **§11 Manager handoff** | What does the manager need to know? | After consult, for enrolment |
| **§12 Quality and audit** | How do we know this is working? | Quarterly review |

### Quick-reference workflow

**At the point of care, you need these sections in this order:**

1. **§3** → confirms this is the right protocol for this child
2. **§4** → tells you what to ask, examine, and test
3. **§5** → tells you how severe it is (with numbers, not adjectives)
4. **§7** → tells you whether this case stays with you or refers out
5. **§6** → tells you what to prescribe (if it stays with you)
6. **§10** → gives you the words to explain to the parent
7. **§8** → tells you when to schedule the follow-up

### Understanding referral labels

The protocols use `SKIDS-T3` labels for referral partners:

- `SKIDS-T3 pediatric ENT surgeon` → the ENT partner at your clinic
- `SKIDS-T3 pediatric ER` → the partner ER in your city
- `SKIDS-T3 pediatric cardiology` → the cardiology partner

These map to actual names in Companion. When a §7 trigger fires,
Companion shows you the partner's name, phone, and address for your
specific clinic location.

### Understanding severity tiers

Every protocol maps severity to intervention:

```
Mild       → §6.1 Light tier     → Basic subscription
Moderate   → §6.2 Standard tier  → Advanced subscription
Severe     → §6.3 Intensive tier → Premium subscription
Beyond T1  → §7 Hard referral    → Out of SKIDS scope
```

The subscription tier is operational (what's included in the bundle),
not clinical (every child gets the same clinical assessment regardless
of their subscription).

### Items marked [TO BE DECIDED BY SKIDS PEDIATRICIAN]

These are operational decisions that require your clinical judgement —
things like whether your clinic stocks a particular device, which
drug formulation is available locally, or how to price a specific
service. Search for them:

```bash
grep -rn "TO BE DECIDED" protocols/
```

Resolve each one based on your clinic's reality, then remove the marker.

---

## For SKIDS Clinic Managers

### What you need from the protocols

Your primary sections are:

- **§11 Manager handoff** — what the Manager Console shows after a
  doctor consult, subscription tier recommendations, parent objection
  scripts
- **§1** — what the clinic does / doesn't do (for parent conversations)
- **§8** — follow-up schedule (for scheduling and re-engagement)
- **§10** — parent-facing communication (scripts you can reference)

### Loss-to-follow-up alerts

Every protocol defines which children are highest-priority for
re-engagement if they miss a follow-up. The priority order:

1. §7.1 emergency referrals not completed
2. NICU graduates and developmental-regression cases (B1-23)
3. RF prophylaxis (B1-03) — missed injections = RF recurrence
4. Nephrotic syndrome on steroids (B1-17)
5. All other active-treatment children

---

## For SKIDS Tech Team (Companion Development)

### How protocols become software specs

**§9 of every protocol IS the Companion software specification.** It
defines, screen by screen, what the Doctor Module renders during a
consult. The tech team builds from §9.

### Architecture overview

```
┌─────────────────────────────────────────────────┐
│                  COMPANION                       │
│                                                  │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐    │
│  │  Doctor   │   │  Manager │   │  Parent  │    │
│  │  Module   │   │  Console │   │   App    │    │
│  └────┬─────┘   └────┬─────┘   └────┬─────┘    │
│       │               │               │          │
│       └───────────┬───┘               │          │
│                   │                   │          │
│              ┌────┴────┐        ┌────┴────┐     │
│              │   PHR   │        │ Content │     │
│              │ (child) │        │  (app)  │     │
│              └─────────┘        └─────────┘     │
│                                                  │
│  ┌──────────────────────────────────────────┐    │
│  │  SKIDS-T3 Partner Directory              │    │
│  │  (maps role → name/phone per clinic)     │    │
│  └──────────────────────────────────────────┘    │
└─────────────────────────────────────────────────┘
```

### What to build from each protocol section

| Protocol section | Companion component | Build artefact |
|---|---|---|
| §4 (Diagnostic workflow) | Doctor Module Screen 2–4 | Form fields, auto-calculations, scale scoring |
| §5 (Severity grading) | Doctor Module Screen 5 | Auto-classification logic from §4 inputs |
| §6 (Therapeutic options) | Doctor Module Screen 6 | Weight-based dosing calculator, prescription generator |
| §7 (Hard referral triggers) | Doctor Module Screen 7 | **Hard-blocks** that prevent proceeding without action |
| §8 (Follow-up schedule) | Doctor Module Screen 8 | Auto-suggested follow-up dates |
| §9 (Companion workflow) | ALL screens | **The primary spec** — screen-by-screen definition |
| §9.2 (Data logged to PHR) | Database schema | Field names, types, frequencies |
| §9.3 (Alerts) | Notification engine | Trigger conditions, recipients, channels |
| §9.4 (Parent app) | Parent app rendering | Post-visit cards, trackers, content activation |
| §9.5 (Auto-generated outputs) | PDF generator | Certificates, action plans, referral packets |
| §9.6 (Edge cases) | Error handling | Offline mode, device failure, consent gating |
| §10 (Parent communication) | Parent app content | Article/video activation triggers per condition |
| §11 (Manager handoff) | Manager Console | Post-consult display, enrolment workflow |

### Hard-blocks (safety-critical — build first)

These are Companion features that **prevent a clinician from proceeding**
unless a safety condition is met. They are the highest-priority build
items:

| Protocol | Hard-block | Logic |
|---|---|---|
| B1-08 | Cardiac screen before stimulant | `IF prescribing methylphenidate AND cardiac_screen_documented = false → BLOCK` |
| B1-19 | G6PD before primaquine | `IF prescribing primaquine AND g6pd_status ≠ "normal" → BLOCK` |
| B1-06 | Resuscitation kit before OFC/SPT | `IF procedure = "OFC" OR "SPT" AND resus_kit_confirmed = false → BLOCK` |
| B1-22 | Observation timer post-vaccination | `IF vaccines_given.length > 0 AND observation_timer_complete = false → BLOCK visit closure` |
| B2-02 | Valproate in adolescent girls | `IF prescribing valproate AND patient.sex = "F" AND patient.age ≥ 10 → WARNING + require documented override reason` |
| B2-03 | MAS emergency | `IF ferritin > 684 AND mas_criteria_count ≥ 2 → FORCE §7.1 workflow, NO OVERRIDE` |
| B1-21 | Hirschsprung alarm features | `IF alarm_features.any = true → FORCE §7.3, BLOCK functional-constipation management` |

### Cross-protocol data reads

Some protocols read data written by other protocols. These require
cross-protocol PHR field access:

| Reader protocol | Field read | Writer protocol |
|---|---|---|
| B1-06 Allergy | `asthma_status.fev1_percent` | B1-14 Asthma |
| B1-06 Allergy | `asthma_status.control_level` | B1-14 Asthma |
| B1-03 Throat | `b1_07_psq_score` | B1-07 Sleep |
| B1-03 Throat | `b1_02_audiometry` | B1-02 Hearing |
| B1-20 Bedwetting | `constipation_status` | B1-21 Constipation |
| B1-10 Obesity | `bp_log` | B1-16 Cardiac |
| B1-17 Kidney | `bp_log` | B1-16 Cardiac |
| All B1 protocols | `growth_metrics` | A1 Screening |
| All B1 protocols | `vaccination_status` | B1-22 Vaccination |

### SKIDS-T3 Partner Directory

The protocols use role-based labels (`SKIDS-T3 pediatric ENT surgeon`,
`SKIDS-T3 pediatric ER`, etc.) instead of specific names. Companion
needs a **per-clinic partner directory** that maps:

```
role (from protocol) → partner name + phone + address (per clinic location)
```

When a §7 trigger fires:
1. Protocol specifies the role (e.g., `SKIDS-T3 pediatric cardiology`)
2. Companion looks up the role in the partner directory for this clinic
3. Referral packet auto-populates with the partner's contact details
4. Doctor sees the actual name and phone number on screen

The partner directory is a separate admin module — not in the protocols.

### Suggested build order

1. **A1 Screening** — every child uses it; most cross-references
2. **Hard-blocks** (7 items above) — safety-critical
3. **B1-08 Behavioural** — most complex safety logic (suicidality §7.1)
4. **B1-22 Vaccination** — operationally dense; cold-chain + timers
5. **B1-14 Asthma** — cross-protocol asthma_status field (read by B1-06)
6. **B1-13 Adolescent** — privacy architecture (separate adolescent login)
7. **Remaining B1 protocols** — in numerical order
8. **B2-01, B2-02, B2-03** — Tier 2; credential-gated activation

### Review guide

A detailed tech team review guide is at `docs/tech-team-review-guide.md`
with screen-by-screen feasibility checklists, PHR field mapping, alert
routing requirements, and edge-case specifications.

---

## For AI/LLM Integration

### Using protocols as context for AI features

The protocol library can serve as the knowledge base for AI features
in Companion:

**1. Clinical decision support**
Feed the child's PHR data + the relevant protocol's §4/§5/§7 into an
LLM to generate:
- Severity classification suggestions
- §7 trigger alerts ("This child's SpO₂ is 91% — §7.1 trigger fires")
- Drug-dose calculations verified against §6

**2. Parent communication generation**
Use §10 scripted explanations as few-shot examples to generate
personalised parent summaries in the parent's language.

**3. Cross-protocol routing**
When a child has multi-domain concerns, use §3 (presenting concerns)
across all protocols to identify which B1 clinics are relevant and
generate a coordinated care plan.

**4. Audit and quality**
Use §12 metrics as targets for automated quality dashboards.

### API-style protocol access

For programmatic access, each protocol can be parsed as structured
markdown with predictable section headers:

```python
# Pseudocode for protocol parsing
protocol = read_markdown("protocols/B1-14-pulmonology-asthma/PROTOCOL.md")

# Extract sections by header
section_5 = protocol.get_section("§5 Severity grading")
section_7 = protocol.get_section("§7 Hard referral triggers")

# Extract tables
severity_table = section_5.get_tables()[0]
referral_triggers = section_7.get_checklists()

# Use in clinical decision support
for trigger in referral_triggers:
    if trigger.matches(patient_data):
        fire_alert(trigger.urgency, trigger.destination)
```

### Fetching protocol content for a specific condition

To find which protocol covers a specific condition:

```bash
# Find which protocol covers "asthma"
grep -rl "asthma" protocols/*/PROTOCOL.md

# Find the severity grading for asthma
grep -A 20 "§5 Severity grading" protocols/B1-14-pulmonology-asthma/PROTOCOL.md

# Find all §7.1 emergency triggers across the library
grep -A 2 "§7.1 Emergency" protocols/*/PROTOCOL.md

# Find all drug doses for a specific drug
grep -i "amoxicillin" protocols/*/PROTOCOL.md

# Find all protocols that cross-reference B1-06 Allergy
grep -l "B1-06" protocols/*/PROTOCOL.md
```

### Keeping protocols in sync with software

The protocol library is version-controlled in git. When a protocol
changes:

1. The git diff shows exactly what changed
2. The tech team maps the change to the affected Companion screens
3. The change is implemented in Companion
4. The protocol version is updated

The protocol is the **source of truth**. If Companion behaviour
differs from the protocol, the protocol wins — Companion is updated
to match, not the other way around.

---

## Quick reference card

| I need to... | Go to... |
|---|---|
| Find which protocol covers a condition | `protocols/_index.md` or `grep -rl "[condition]" protocols/` |
| Know what to do for a specific severity | Protocol §5 (severity) → §6 (treatment) |
| Know when to refer | Protocol §7 (sacred section — non-negotiable) |
| Know what to say to the parent | Protocol §10 (scripted explanations) |
| Know what Companion should show | Protocol §9 (screen-by-screen spec) |
| Know what data to store | Protocol §9.2 (PHR field definitions) |
| Know which alerts to fire | Protocol §9.3 (alert trigger table) |
| Know the quality targets | Protocol §12 (outcome metrics) |
| Find all unresolved decisions | `grep -rn "TO BE DECIDED" protocols/` |
| Find the citation for a clinical claim | `shared/citations.bib` |
| Review tech implementation checklist | `docs/tech-team-review-guide.md` |
| Review citation verification status | `docs/citation-verification-guide.md` |
