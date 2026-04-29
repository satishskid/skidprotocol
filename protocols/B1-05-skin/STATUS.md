# Status: B1-05 Skin Clinic

**Current state:** DRAFT_COMPLETE
**Author:** Claude (AI first draft)
**Date created:** 2026-04-29
**Date started:** 2026-04-29
**Date drafted:** 2026-04-29
**Estimated completion:** 12 of 12 sections drafted

## What was drafted

All 12 sections per `SPECS.md` §1 are present at or near target depth.
B1-05 is the second protocol in the library (after A1) and the first
B1-tier disease protocol; it inherits the voice and the §9 Companion
conventions from A1 and uses the standard template's three-tier
severity grade structure (Mild / Moderate / Severe / Refractory) per
condition rather than A1's four-tier flag vocabulary.

Domains covered:
- Atopic dermatitis (SCORAD-graded; Mild / Moderate / Severe; with
  proactive maintenance and refractory-to-pedoderm pathway).
- Acne vulgaris (IGA-Acne graded; with the 3-month oral antibiotic
  cap embedded as an antimicrobial-stewardship constraint).
- Common pediatric infectious dermatoses: impetigo, scabies, tinea
  (corporis, capitis, cruris, pedis), candidal intertrigo,
  pediculosis, molluscum, warts.
- Reactive dermatoses: contact, urticaria (acute), drug eruption
  (mild morbilliform; SJS / TEN / DRESS to §7.1).
- Pigmentary and lesion-surveillance categories: nevi, café-au-lait
  with NF1 screening triggers, hemangiomas (high-risk-site to §7),
  vitiligo (to §7).

§7 sacred section drafted with explicit thresholds: SJS/TEN, SSSS,
DRESS, eczema herpeticum, anaphylaxis, NAI, cellulitis with systemic
features, necrotising fasciitis, erythroderma → §7.1 emergency. Cellulitis
without systemic features, crusted scabies, high-risk-site hemangiomas,
new-onset purpura, BP-with-skin → §7.2 urgent. Refractory AD (SCORAD
≥40 after 4 weeks of optimised §6.3), refractory or scarring acne,
vitiligo, café-au-lait NF1-screen-positive, ABCDE pigmented lesion,
suspected genodermatosis, CTD skin findings → §7.3 routine.

Citation density meets the SPECS target (~1 tag per 250 words of
clinical content). New citations added to `shared/citations.bib`:
AAD-2024-AD, AAD-2024-Acne, IAP-Atopic-2023, IADVL-Scabies-2021,
CDC-Scabies-2024, AAD-Tinea-2014, Cochrane-CD003871, Cochrane-CD009864,
Stevens-2014-IDSA.

## Open clinical questions for editorial review

Marked in the protocol body with `[NEEDS EXPANSION IN EDITORIAL PASS]`.
Specifically:

1. **§2 IAP Atopic Dermatitis position statement** — I have referenced
   `[IAP-Atopic-2023]` as the IAP Pediatric Allergy and Applied
   Immunology Chapter consensus. Confirm the exact governing
   IAP document and reconcile the citation with the most current IAP
   publication on atopic dermatitis.

2. **§2 Departure 2 — Indian antimicrobial-stewardship policy on
   tetracyclines for moderate acne.** Confirm whether the 3-month cap
   I have hard-coded into §6.2 / §6.3 / §12 is the correct
   stewardship-policy framing for SKIDS, or whether a stricter cap is
   warranted.

3. **§2 Permanent protocol owner** — interim is Dr. Satish Prasad
   Rath, MD Paediatrics. Pediatric dermatology subspecialty owner
   pending; this is the gap most relevant to §5 / §7 sign-off.

4. **§12.1 steroid-phobia-related under-treatment threshold** — the
   operational definition (< 100 g emollient/month for moderate AD,
   > 50% missed prescribed-days at adherence assessment) is a
   placeholder. Confirm with clinical operations.

## Judgement calls the editorial reviewer should re-check

- **First-line tinea capitis = griseofulvin.** Departure from AAD
  (terbinafine first-line in T. tonsurans-predominant US settings)
  defended in §2 on Indian-mixed-isolate grounds and IAP precedent.
  Re-check that this remains the right call given any recent shift
  in Indian pediatric dermatomycoses epidemiology.

- **Scabies ivermectin first-line for whole-household coverage.** Per
  IADVL 2021. AAD / CDC name permethrin first-line. The IADVL position
  emphasises compliance / coverage advantages of single-dose oral.
  Re-check at editorial pass.

- **Three-month oral antibiotic cap for acne.** Hard-coded into §6,
  §8, §9 (Companion alert at 100% of course), §12 (audit metric).
  AAD recommends "shortest duration possible," typically ≤ 3 months;
  this protocol makes that an enforced cap. Confirm.

- **§5 four-tier vs. three-tier severity grading.** B1-05 uses the
  template's three-tier (Mild / Moderate / Severe) plus a Refractory
  §7 routing tier. This deliberately diverges from A1's four-tier
  flag vocabulary because B1-05 grades clinical severity per condition,
  not screening flag tier. Confirm the divergence is the right
  inheritance pattern for the rest of the B1 library.

- **Wet-wrap therapy taught in clinic by clinic nurse.** Severe AD
  §6.3 prescribes in-clinic wet-wrap teaching. Confirm B1-05 clinic
  staffing includes a nurse trained in wet-wrap demonstration; if
  not, this needs an allied-staff onboarding addition.

- **Photographic capture mandated for every B1-05 visit.** Operational
  burden assessment: this is a real ask of the clinic workflow. Confirm
  Companion implementation supports it efficiently.

## Voice anchor reference

Voice inherited from A1. Sections re-read for voice consistency
informally during authoring; a formal full-document voice-pass has
not been done.

## Subsequent next item

Per the workflow priority order in `workflows/how-to-write-a-protocol.md`,
the next protocols are B1-01 Vision OR B1-09 Nutrition & Growth OR
B1-08 Behavioural OR B1-06 Allergy — these inherit B1-05's pattern
with ~40% less authoring time. The recommended next protocol depends
on which inheritance path the project owner wants to validate next:

- **B1-01 Vision** — device-driven workflow (Welch Allyn Spot already
  referenced from A1 §4.4); simplest therapeutic kit; tests the
  device-protocol pattern.
- **B1-09 Nutrition & Growth** — high A1 cross-reference density
  (A1 already routes growth Yellow / Orange flags here); tests the
  A1-to-B1 hand-off pattern most thoroughly.
- **B1-08 Behavioural** — tests the LISSUN partnership, the
  M-CHAT-R and Vanderbilt scales already referenced from A1, and
  the §10 cultural-sensitivities pattern around mental-health stigma
  most thoroughly.
- **B1-06 Allergy** — direct co-management with B1-05 for AD with
  food-trigger or aeroallergen-trigger; tests the cross-protocol
  shared-management pattern.

Recommendation: B1-01 Vision next (simplest exemplar; locks in the
device-protocol pattern before tackling the more complex behavioural
or allergy clinics).
