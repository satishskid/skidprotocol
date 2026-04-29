# Status: B1-08 Behavioural Clinic

**Current state:** DRAFT_COMPLETE
**Author:** Claude (AI first draft)
**Date created:** 2026-04-29
**Date started:** 2026-04-29
**Date drafted:** 2026-04-29
**Estimated completion:** 12 of 12 sections drafted

## What was drafted

All 12 sections per `SPECS.md` §1 are present at or near target depth.
B1-08 is the fifth protocol in the library and the deepest test of
the LISSUN external partnership integration, the adolescent privacy /
confidentiality framework inherited from A1, and the ADHD-pharmacotherapy
cardiac-screening preconditions documented as a CLAUDE.md gotcha.

This is a sensitive protocol. Suicidality §7.1 routing, mental-health
stigma cultural framing, and the cardiac-screen Companion hard-block
are the three most operationally consequential elements.

Domains covered:
- ADHD diagnosis + management (Vanderbilt-graded; Mild behavioural-first,
  Moderate / Severe with stimulant pharmacotherapy under cardiac-screen
  preconditions; refractory to §7.3).
- Autism screening (M-CHAT-R/F at 16–30m); formal diagnosis routes
  §7.3.
- Adolescent depression (PHQ-A) and anxiety (GAD-7); Mild CBT-only,
  Moderate SSRI + CBT, severe / suicidality / psychosis to §7.
- Disruptive behaviour / oppositional patterns; LISSUN parent-training
  programmes; conduct disorder severe to §7.2.
- OCD mild (counselling + observation); moderate-severe to §7.3.
- Tic disorders mild (counselling); moderate-severe / Tourette to §7.3.
- Adjustment / acute stress / mild PTSD with confirmed trauma; severe
  trauma to §7.3.
- Adolescent substance use (CRAFFT-graded brief intervention); severe
  SUD to §7.2.
- Behavioural sleep / feeding / school-refusal cross-care with B1-07
  / B1-09 / B1-13.

Critical operational elements established:
- LISSUN partnership integration: external therapy-network delivering
  CBT, parent training, family therapy, social-skills groups, trauma-
  focused CBT (within scope). LISSUN clinical lead countersigns §5 /
  §7 and participates in §12 quarterly review. LISSUN crisis arm
  available for §7.1 suicidality handoff per partnership SLA.
- ADHD pharmacotherapy cardiac-screen Companion hard-block: stimulant
  prescription does not generate without cardiovascular history,
  exam, ECG, family-history-of-sudden-cardiac-death documented and
  reviewed.
- Adolescent privacy framework: confidentiality discussion mandatory
  at every adolescent visit; private interview; consent-controlled
  parent-app summary filtering.
- Stigma-aware diagnostic-label discipline: functional framing at
  screening visit; formal diagnostic labels at confirmation visits
  with explicit consent; documented per visit.
- Suicidality §7.1 protocol with safety plan + lethal-means
  counselling + LISSUN psychiatrist pre-notification + child-not-
  discharged-unaccompanied retention rule.

§7 sacred section drafted with explicit thresholds:
- §7.1 Emergency: active suicidality (any PHQ-A item 9 positive),
  active psychosis, active mania, severe self-harm, abuse / exploitation
  disclosure, substance acute intoxication / withdrawal, severe eating
  disorder with crisis features, acute behavioural change with
  neurological features, acute aggression with risk to self / others.
- §7.2 Urgent (≤ 7 days): severe depression PHQ-A 20–27, severe
  anxiety GAD-7 15–21 not responding, suspected pediatric bipolar,
  adolescent eating disorder rapid weight loss without crisis, severe
  SUD, severe disruptive / conduct, acute behavioural deterioration.
- §7.3 Routine (≤ 4 weeks): M-CHAT-R/F positive for formal autism
  assessment, refractory ADHD, OCD moderate-severe, Tourette suspicion,
  persistent functional impairment despite 12 weeks of LISSUN therapy,
  complex trauma / PTSD beyond brief CBT, suspected ID / cognitive
  impairment, suspected pediatric epilepsy with behavioural
  presentation, family caregiver mental health emergency, family
  request for second opinion.

Citation density meets the SPECS target. New citations added to
`shared/citations.bib`: AAP-Anxiety-2020, AAP-Depression-2018,
AAP-Suicide-2024, IAP-Behaviour-2022, WHO-mhGAP-2023, NICE-ADHD-2018,
Robins-MCHATR-2014, Wolraich-Vanderbilt, Goodman-SDQ-2001,
PHQ-A-Validation.

## Open clinical questions for editorial review

Marked in the protocol body with `[NEEDS EXPANSION IN EDITORIAL PASS]`.
Specifically:

1. **§2 IAP Behaviour position statement (`[IAP-Behaviour-2022]`)** —
   confirm exact title, year, and reconcile with most current IAP
   publication on pediatric behavioural health.

2. **§2 Departure 3 — LISSUN partnership scope across SKIDS clinic
   locations.** The protocol assumes LISSUN coverage at every SKIDS
   clinic. Currently LISSUN is named for SKIDS Bangalore (per CLAUDE.md
   §7.3). Confirm partnership scope plan and the per-location named
   LISSUN clinical lead for editorial pass.

3. **§2 Permanent protocol owner and LISSUN clinical-lead
   countersignature requirement** — confirm both are operationally
   feasible and named by editorial pass.

## Judgement calls the editorial reviewer should re-check

- **ADHD pharmacotherapy initiation in primary care.** Departure
  from many Indian centres (which restrict initiation to specialist).
  Defended on access grounds and strong AAP-2019 evidence base.
  Re-check given local pediatric psychiatry capacity context.

- **Universal pre-stimulant ECG.** Conservative; AAP-2019 does not
  mandate universal ECG (only with positive history). The protocol
  universalises ECG given Indian-population family-history under-
  disclosure. Operational implications: B1-08 needs ECG capability
  or B1-16 same-day cardiology partnership. Re-check feasibility.

- **SSRI initiation in primary care for moderate adolescent
  depression.** GLAD-PC supports it; many Indian primary-care
  practices defer to psychiatry. The protocol follows GLAD-PC with
  LISSUN psychiatrist availability for joint-care. Re-check given
  local capacity.

- **Adolescent privacy framework.** More restrictive on parent-
  disclosure than typical Indian primary-care practice. Confirm
  this is the right ethical and operational position for SKIDS.
  Particular question: how is the parent-app filtering enforced
  technically, and what happens if the parent demands disclosure
  beyond the consent boundary?

- **Mental-health stigma diagnostic-label discipline.** Functional
  framing at screening, formal labels at confirmation with consent.
  Confirm this works operationally with insurance / school-
  accommodation requirements that need formal diagnostic codes.

- **Diagnostic-label parent-app filtering.** The Companion is asked
  to filter the post-visit summary based on adolescent privacy
  consent. Technically non-trivial; confirm engineering feasibility
  in §9 spec.

- **LISSUN partnership SLA for §7.1 crisis arm 24/7.** Confirm with
  LISSUN that the crisis-arm SLA is contractually established for
  the SKIDS partnership.

## Voice anchor reference

Voice inherited from A1 + B1-05 + B1-01 + B1-09. Sections re-read
for voice consistency informally during authoring; a formal full-
document voice-pass has not been done. Adolescent-facing scripted
explanations in §10 are deliberately matter-of-fact and serious in
register, particularly the suicidality §7.1 script.

## Subsequent next item

Per the workflow priority order, the next protocols are B1-06 Allergy
OR B1-07 Sleep OR B1-13 Adolescent OR B1-22 Vaccination.

Recommendation: **B1-06 Allergy** next — direct cross-care with B1-05
(AD with food / aeroallergen triggers), with B1-09 (CMPA), with B1-14
(asthma — though B1-14 not yet drafted). Tests the cross-protocol
shared-management pattern most thoroughly. B1-06 also locks in the
adrenaline auto-injector + anaphylaxis action plan operational
pattern that affects A1 §7.1 (anaphylaxis without action plan).

Alternative: B1-13 Adolescent — the natural follow-on from B1-08,
inheriting privacy framework, HEEADSSS, contraception counselling
cultural complexity. B1-13 deepens what B1-08 starts on the
adolescent-specific dimension.
