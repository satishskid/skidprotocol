# Status: A1 SKIDS Screening

**Current state:** DRAFT_COMPLETE
**Author:** Claude (AI first draft)
**Date created:** 2026-04-29
**Date started:** 2026-04-29
**Date drafted:** 2026-04-29
**Estimated completion:** 12 of 12 sections drafted

## Why this protocol matters

A1 is the front door of the SKIDS clinical system. It is the screening
protocol that runs at every SKIDS clinic, generates the PHR, identifies
flags, and routes children to the appropriate Tier 1 specialty clinic.
Every B1 protocol assumes a child arriving has been through A1. A1's
§5 flag-tier vocabulary (Green / Yellow / Orange / Red) and §9 Companion
spec are reused by every B1 protocol, so getting these right here saves
substantial authoring time on the rest of the library.

## What was drafted

All 12 sections per `SPECS.md` §1 are present at or near target depth.
The protocol adapts the standard B1 disease-protocol template for a
universal screening protocol — §3 is reframed as a routing matrix, §5
is flag-tiering rather than disease severity, §6 is anticipatory
guidance + B1 routing rather than therapy, and §7 is the screening Red
flag set. §9 Companion spec is the most operationally detailed in the
library so far because A1 touches every domain.

Citation density meets the SPECS target. New citations added to
`shared/citations.bib`: AAP-BF-4E, AAP-Period-2024, IAP-Period-2024,
Owens-2005-BEARS, CDC-Milestones-2022, RBSK-2013.

## Open clinical questions for editorial review

Marked in the protocol body with `[NEEDS EXPANSION IN EDITORIAL PASS]`.
Specifically:

1. **§1 protocol_owner** — interim is Dr. Satish Prasad Rath, MD
   Paediatrics. Permanent should be a developmental-behavioural
   pediatrician given A1's domain spread. Confirm assignment.

2. **§7.1 child-protection retention protocol** — the protocol states
   that a child with suspected NAI / sexual abuse is not discharged to
   the suspected-perpetrator caregiver and is retained in clinic until
   ER transfer. Confirm SKIDS clinic legal/operational protocol with
   Dr. Rath; confirm Indian-context legal authority for this retention
   and the documentation/reporting pathway under POCSO and JJ Act.

3. **§8.3 outcome metric thresholds** — the 85% periodicity-attendance
   target is a placeholder. Confirm with operational data once initial
   SKIDS clinic data is available.

4. **§10.5 dietary template variants** — the parent app's nutrition
   guidance has dietary-practice variants (vegetarian / Jain / halal /
   kosher / regional). Confirm the actual content set with the B1-09
   Nutrition team before Companion deployment.

5. **§12.1 conversion rate target and parent-app activation target**
   — placeholders pending operational data and content team baseline.

## Judgement calls the editorial reviewer should re-check

- **§5 flag tiers (Green / Yellow / Orange / Red).** Four-tier system
  chosen over a three-tier (mild / moderate / severe) because A1's
  Yellow tier needs a distinct semantic — "monitor with parent
  education and recheck, do not specialty-refer" — that doesn't fit
  cleanly into a B1-style severity grade. The four-tier vocabulary
  is intended to propagate to every B1 protocol's §5; an editorial
  decision against it here would force a re-author of every B1 §5
  later.

- **A1 follows IAP visit cadence (21 visits over 18 years), not AAP
  Bright Futures cadence (33 visits).** Justified in §2 departures.
  Re-check that the IAP cadence is operationally sound for SKIDS — if
  SKIDS wants to differentiate on cadence (more visits for premium
  tier, e.g.), this needs reopening.

- **§6.3 Orange-flag B1 intake windows.** The 2-week / 4-week / 6-week
  windows are clinically reasonable defaults but operations may need
  to adjust based on B1 capacity once SKIDS clinics are running.

- **§7.1 PHQ-A item 9 → automatic Red.** This is a deliberate
  no-judgement-call rule (any item 9 positivity, regardless of total
  PHQ-A score, fires §7.1). Re-check with the named LISSUN partner
  that this is the right escalation policy and that LISSUN can absorb
  the resulting volume.

- **§11 subscription tier matching.** The matching logic between flag
  profile and recommended subscription tier is non-coercive and the
  pediatrician is required to explicitly state in §10.2 that clinical
  care does not change with subscription tier. This protects the
  platform's credibility but may underperform on conversion vs. a
  more sales-driven model. The trade-off is intentional — re-check
  that operations agree.

## Voice anchor

A1 is now the voice anchor for B1 protocol authoring. When starting
B1-05 Skin (the recommended next protocol), read `protocols/A1-skids-screening/PROTOCOL.md`
in addition to `docs/01-voice-and-style-guide.md` and `shared/voice-samples.md`.

## What remains for the author before editorial pass begins

The workflow doc (`workflows/how-to-write-a-protocol.md`) recommends a
voice-consistency re-read of the full protocol after all sections are
drafted. This re-read has not been done. Recommended next-session
action *if* the same author resumes A1: do the re-read pass and tighten
any sentences that drift from the voice samples. *If* the editorial
reviewer wants to start now, they may — the [NEEDS EXPANSION] markers
plus this STATUS.md should give them sufficient guidance.

## Subsequent next item

Per CLAUDE.md §5 NEXT WORK ITEM, the next protocol after A1 is
**B1-05 Skin** — highest commercial signal under the prevalence ×
felt-need × dispensable rubric.
