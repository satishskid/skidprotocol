# SKIDS CLINICAL PROTOCOL LIBRARY

> **READ THIS FILE FIRST, EVERY SESSION, BEFORE DOING ANYTHING ELSE.**
> Last updated: 2026-04-29 · v0.6 · A1 + B1-01 + B1-05 + B1-08 + B1-09 drafted

This is the project memory for the SKIDS Clinical Protocol Library — a
multi-session, multi-author work spanning roughly 17 focused sessions to
produce 26 textbook-grade clinical protocols, plus the doctor and manager
asset derivatives that follow.

The whole point of this file is that **a fresh Claude Code session, opened
weeks after the last one, can be productive within 60 seconds** by reading
just this document. If you find yourself re-litigating decisions that are
already locked here, stop and re-read this file.

---

## §1 PROJECT MISSION

The SKIDS Clinical Protocol Library is the institutional clinical brain of
SKIDS Health Technologies. It is a structured, version-controlled, evidence-
grounded collection of clinical protocols — one per pediatric specialty
service that SKIDS clinics deliver — written by senior pediatricians for
junior pediatricians.

Every protocol defines:
- what conditions the SKIDS pediatrician is qualified to manage
- what diagnostic devices and protocols are used
- what therapeutics are dispensed in-clinic
- when (and to whom) the case must be referred
- how the parent experiences this, end to end
- how the manager handles subscription enrolment for this service

The library lives inside the SKIDS Companion software (AWS + Cloudflare).
It is internal IP, not parent-facing. Parent-facing material is *derived
from* the protocol library — never authored independently. This derivation
discipline is the central institutional commitment of the project: it is
what stops SKIDS from overpromising in marketing.

### Why this project exists

Most pediatric clinic chains have a marketing layer disconnected from a
clinical layer. They claim "world-class allergy care" because their
marketer wrote those words, not because their protocols define what that
phrase means. By the time the parent shows up, the gap is visible.

SKIDS is built the other way around: protocols define the truth, and
every parent-facing claim must trace back to a specific section of a
specific protocol. The library is therefore not a documentation
afterthought — it is the spine of the company.

---

## §2 NON-NEGOTIABLES (READ EVERY SESSION)

These are locked. Do not relitigate. Do not soften. Do not work around.

### 2.1 Voice
Senior pediatrician writing for a junior pediatrician. Confident, specific,
no padding, no marketing language, no exclamation marks. Assumes the reader
is medically intelligent and time-pressed. See `docs/01-voice-and-style-guide.md`.

### 2.2 Evidence base
Every clinical claim must cite at least one of:
- IAP (Indian Academy of Pediatrics) guidelines
- AAP (American Academy of Pediatrics) policy statements or clinical reports
- NASPGHAN, GINA, AAFP, AAO-HNS, AAD, AAPD, CDC, ICMR, NTEP guidelines
- Nelson Textbook of Pediatrics (current edition)
- IAP Textbook of Pediatrics (6th edition is the SKIDS reference)
- Ghai's Essential Pediatrics (current edition)
- Cochrane systematic reviews
- High-quality RCTs / meta-analyses indexed in PubMed
See `docs/02-citation-conventions.md` for citation format.

### 2.3 §5 (Severity grading) and §7 (Hard referral triggers) are sacred
These two sections of every protocol are the medico-legal spine of the
platform. They are what lets a SKIDS pediatrician practise broadly without
practising unsafely. Treat them as the most important sections in the
document. Never under-specify them. Never make their thresholds vague.
See `docs/05-referral-trigger-discipline.md`.

### 2.4 Audience
- **Primary author voice:** senior pediatrician
- **Primary reader:** junior SKIDS pediatrician (MD Paeds, possibly with
  one subspecialty credential)
- **Governing reader:** the credentialed subspecialist who owns this
  protocol's quarterly case-review (named in §2 of each protocol)
- **Derived audiences:** SKIDS managers (read manager-asset chapter),
  parents (read parent-summary derivative), investors (read library index)

### 2.5 Storage and access
The protocol library lives inside SKIDS Companion software, hosted on
AWS + Cloudflare. It is internal IP. Parent-facing material is *derived*
from protocols, never published verbatim. The Companion Doctor Module
renders protocol §4-§9 at the point of care.

### 2.6 Quality bar
Medical-society protocol library, not blog post. The bar is "good enough
to defend in front of a medical council if a case goes wrong." Every
protocol should read as though it could appear in IAP's published guidance
without embarrassment.

### 2.7 Author humility
The author of this library is Claude (an AI assistant) producing first
drafts. Every protocol must pass an editorial review by a senior SKIDS
pediatrician before being marked "v1.0 approved" and deployed into
Companion. Drafts are clearly marked `STATUS: draft awaiting editorial pass`.

---

## §3 TIER MAP (LOCKED)

The complete SKIDS clinical service catalogue. Do not modify without
explicit approval from project owner (Dr. Satish Prasad Rath).

### Tier 1 — every SKIDS pediatrician delivers under protocol (23 services)

The SKIDS pediatrician runs these directly using the protocol, the
in-clinic diagnostic device, the in-clinic dispensary, and the allied
team. A credentialed subspecialist provides protocol governance and
quarterly case-review oversight, not personal delivery.

```
A1 — SKIDS Screening                  (the front door)

B1-01 Vision                          B1-13 Adolescent
B1-02 Hearing & Ear                   B1-14 Pulmonology / Asthma
B1-03 Throat & Airway                 B1-15 Gastrointestinal
B1-04 Oral Health                     B1-16 Cardiac
B1-05 Skin                            B1-17 Kidney & Urology
B1-06 Allergy                         B1-18 Blood
B1-07 Sleep                           B1-19 Infections
B1-08 Behavioural                     B1-20 Bedwetting
B1-09 Nutrition & Growth              B1-21 Constipation
B1-10 Obesity & Metabolic             B1-22 Vaccination
B1-11 Speech & Language               B1-23 Developmental Surveillance
B1-12 Learning
```

### Tier 2 — Fellowship-credentialed pediatrician required (3 services)

Cannot be delivered by protocol alone. Requires a pediatrician with
formal subspecialty credential. SKIDS clinics activate these as their
pediatricians complete The SKIDS Fellowship in the relevant specialty.

```
B2-01 Endocrine Clinic
B2-02 Neurology Clinic
B2-03 Rheumatology Clinic
```

Each Tier 1 service also has a *complex tier* that escalates to the
Tier 2 subspecialist or to a Tier 3 partner — the protocol's §7 (Hard
referral triggers) defines the boundary.

### Tier 3 — partnership / referral, leads given by SKIDS

```
Pedodontist (restoration, orthodontics, surgical dental)
ENT surgeon (tonsillectomy, adenoidectomy, grommets, cochlear)
Pediatric ophthalmologist (strabismus, cataract, retinal)
Pediatric surgeon (hernia, hydrocele, undescended testis)
Pediatric orthopaedic (bracing, complex deformity)
Pediatric oncology (tertiary)
Pediatric ICU (hospital-based)
```

For full rationale and qualification framework see `docs/04-tier-system.md`.

---

## §4 STATUS TRACKER

Auto-stamped on every commit. Update this section every time a protocol
moves between states.

### v1.0 approved (in Companion)
- (none yet)

### v1.0 complete, awaiting editorial pass
- A1 — SKIDS Screening (drafted 2026-04-29; DRAFT_COMPLETE; see protocols/A1-skids-screening/STATUS.md for editorial-pass questions)
- B1-01 — Vision Clinic (drafted 2026-04-29; DRAFT_COMPLETE; see protocols/B1-01-vision/STATUS.md for editorial-pass questions)
- B1-05 — Skin Clinic (drafted 2026-04-29; DRAFT_COMPLETE; see protocols/B1-05-skin/STATUS.md for editorial-pass questions)
- B1-08 — Behavioural Clinic (drafted 2026-04-29; DRAFT_COMPLETE; see protocols/B1-08-behavioural/STATUS.md for editorial-pass questions)
- B1-09 — Nutrition & Growth Clinic (drafted 2026-04-29; DRAFT_COMPLETE; see protocols/B1-09-nutrition-and-growth/STATUS.md for editorial-pass questions)

### Drafting now
- (none — between sessions)

### Stubbed (project structure exists, no PROTOCOL.md yet)
- B1-02 Hearing & Ear · B1-03 Throat & Airway
- B1-04 Oral Health · B1-06 Allergy
- B1-07 Sleep
- B1-10 Obesity & Metabolic · B1-11 Speech & Language · B1-12 Learning
- B1-13 Adolescent · B1-14 Pulmonology / Asthma · B1-15 Gastrointestinal
- B1-16 Cardiac · B1-17 Kidney & Urology · B1-18 Blood
- B1-19 Infections · B1-20 Bedwetting · B1-21 Constipation
- B1-22 Vaccination · B1-23 Developmental Surveillance
- B2-01 Endocrine · B2-02 Neurology · B2-03 Rheumatology

### Editorial pass complete, awaiting deployment
- (none yet)

---

## §5 NEXT WORK ITEM

**Recommended next protocol to write: B1-06 Allergy**

Why:
- A1 and four B1 protocols (B1-01, B1-05, B1-08, B1-09) are now
  drafted. Five at this point cover the screening, device-driven,
  dispensary-driven, allied-staff-driven, external-partnership
  (LISSUN), and adolescent-privacy patterns.
- B1-06 Allergy is the deepest test of the cross-protocol shared-
  management pattern in the library:
    * Co-manages atopic dermatitis with food / aeroallergen triggers
      with B1-05 (B1-05 §3 / §6 already references this).
    * Co-manages CMPA with B1-09 (B1-09 §5.6 / §6.2 already
      references this).
    * Will co-manage asthma triggers with B1-14 Pulmonology when
      B1-14 is drafted.
- Locks in the adrenaline auto-injector + anaphylaxis action plan
  operational pattern that affects A1 §7.1 (anaphylaxis without
  action plan is a §7.1 trigger; B1-06 is the protocol that ensures
  every at-risk family has an action plan in place).
- Establishes specific IgE testing, skin-prick testing, and oral-
  food-challenge workflows — important new device-and-allied-staff
  patterns.

Alternatives in priority order:
- B1-13 Adolescent (natural follow-on from B1-08; inherits privacy
  framework; HEEADSSS and contraception counselling cultural
  complexity).
- B1-07 Sleep (cross-care with B1-08 behavioural sleep; BEARS scale
  already in A1; melatonin cautious-use per CLAUDE.md §7.2).
- B1-22 Vaccination (operationally dense; reconciles IAP IIS with
  every periodic A1 visit).
- B1-14 Pulmonology / Asthma (closes the atopic march triad once
  B1-06 done — AD, food allergy, asthma).

When starting B1-06: read A1, B1-05 (for AD cross-care), B1-09 (for
CMPA cross-care), and B1-08 (for the LISSUN partnership-style
external-resource pattern, applicable here for severe / complex
allergy referral to pediatric allergy specialists). The §7
adrenaline-auto-injector pattern should be drafted carefully — it
affects A1 §7.1 and so the cross-protocol consistency check at
editorial pass will scrutinise it.

---

## §6 HOW TO WORK ON THIS PROJECT

### When opening a fresh Claude Code session

1. Read this file (`CLAUDE.md`) end-to-end.
2. Read `docs/01-voice-and-style-guide.md` if you haven't recently.
3. Read the most recently completed protocol as a voice anchor —
   currently `protocols/A1-skids-screening/PROTOCOL.md` (DRAFT_COMPLETE).
4. Check `§4 STATUS TRACKER` above to confirm what's done and what's next.
5. Open the relevant protocol's STATUS.md to see if there are notes from
   the previous session.
6. If using GSD (recommended): run `/gsd-progress` first, then proceed
   with `/gsd-execute-phase` against the next protocol.

### When writing a new protocol

1. Copy `docs/00-protocol-template.md` to `protocols/B1-XX-name/PROTOCOL.md`.
2. Read `workflows/how-to-write-a-protocol.md`.
3. Author all 12 sections in the order they appear.
4. Mark `STATUS: draft` in the front-matter until editorial pass is complete.
5. Update `§4 STATUS TRACKER` in this file when done.
6. Commit.

### When stopping mid-protocol

Write a clear continuation note in `protocols/B1-XX-name/STATUS.md`:
- which sections are complete
- which section is in progress (and where you stopped within it)
- any open clinical questions you flagged for the editorial reviewer
- any judgement calls you made that the next session should re-check

The next session should be able to resume with no information loss.

---

## §7 GOTCHAS / KNOWN ISSUES

Real lessons learned, persistent across sessions. Add to this section
whenever you discover something the next session needs to know.

### 7.1 Citation discipline
- IAP Textbook of Pediatrics 6th edition is the SKIDS reference, not older
  editions. When citing IAP guidelines, name the document and year explicitly
  (e.g., "IAP IIS 2024-25" not "IAP guidelines").
- AAP citations should include the policy statement number and reaffirmation
  date if relevant.

### 7.2 Specific clinical caveats — handle with explicit cautious-use language
- **Melatonin in Sleep protocol** — IAP cautious-use applies; do not present
  as first-line; reserve for specific sleep-onset insomnia phenotypes.
- **Adolescent contraception counselling** — culturally complex in India;
  follow the documented position in the Adolescent protocol when written;
  do not freelance.
- **Oral antibiotics for moderate acne in Skin protocol** — within AAP /
  AAD primary-care scope but flag for editorial review on Indian
  antimicrobial-stewardship considerations.
- **Pharmacotherapy for ADHD in Behavioural protocol** — must include
  explicit cardiac screening preconditions and weight-based dosing.

### 7.3 Named partnerships
- **LISSUN** is named in Behavioural and Adolescent protocols as the
  external therapy partner for SKIDS Bangalore. Reference but do not
  market — protocols are internal.
- **The SKIDS Fellowship** is the credential pathway by which junior
  pediatricians earn Tier 2 subspecialty credentials. Reference in §12
  (Quality and audit) of every Tier 1 protocol where relevant — the
  protocol governance subspecialist is named, and the Fellowship is the
  pathway to becoming one.

### 7.4 Companion software constraints
- Protocol §9 (Companion software workflow) must specify the screens and
  fields the Doctor Module renders, not just the clinical content.
- Protocol §11 (Manager handoff) must specify what the Manager Console
  surfaces from this protocol after the doctor consult.
- Both §9 and §11 must be written by the protocol author, not deferred
  to "the engineering team will figure it out."

### 7.5 Tier discipline
- Tier 1 = SKIDS ped delivers using protocol (no subspecialty credential).
- Tier 2 = Requires named subspecialty credential. Three services only:
  Endocrine, Neurology, Rheumatology.
- Tier 3 = Partner referral.
- The complex tier *within* a Tier 1 service escalates to Tier 2 or Tier 3
  via the §7 hard referral triggers. Do not blur these lines.

### 7.6 Honest stubs over dishonest completeness
If a section is under-developed, mark it
`[NEEDS EXPANSION IN EDITORIAL PASS]` rather than padding it. The editorial
reviewer's time is better spent expanding flagged stubs than catching
hidden thinness.

---

## §8 TOOLING INTEGRATION

### Active integrations
- **GSD (Get Shit Done)** — recommended Claude Code workflow harness for
  multi-session protocol authoring. See `setup-gsd.md` for installation
  and `.gsd-conventions.md` for how GSD phases map onto our work.

### Bookmarked for future use
- **Frontend Slides (zarazhangrui/frontend-slides)** — for Layer 2B
  manager marketing assets (social posts, in-clinic signage, decks)
  derived from completed protocols. Install when starting manager
  asset work.
- **Graphify (safishamsi/graphify)** — for once 10+ protocols are
  written. Run over the corpus to map cross-protocol relationships and
  feed Companion's knowledge layer.

See `docs/future-tools.md` for full notes.

---

## §9 CHANGE LOG

```
2026-04-29  v0.1   Gate 1 bootstrap. CLAUDE.md, README.md, SPECS.md,
                   protocol template, voice guide, citation conventions,
                   tier system, referral discipline, fellowship doc,
                   workflows, GSD integration, future-tools bookmarks.
                   (Initial copy claimed A1 SKIDS Screening was drafted;
                   that was incorrect — see v0.1.1.)

2026-04-29  v0.1.1 Bootstrap correction. §4 STATUS TRACKER and §5 NEXT
                   WORK ITEM had pre-marked A1 SKIDS Screening as
                   "drafted" and recommended B1-05 Skin as next, but
                   protocols/A1-skids-screening/ contains only STATUS.md
                   (NOT_STARTED), no PROTOCOL.md. Reverted A1 to the
                   Stubbed list, set §5 NEXT WORK ITEM to A1, and
                   corrected the v0.1 log entry above.

2026-04-29  v0.2   A1 SKIDS Screening drafted (DRAFT_COMPLETE). All 12
                   sections at or near target depth. Establishes the
                   four-tier flag vocabulary (Green / Yellow / Orange /
                   Red) and the Companion §9 conventions for every B1
                   protocol to inherit. Five [NEEDS EXPANSION] markers
                   for the editorial pass — see
                   protocols/A1-skids-screening/STATUS.md. New citations
                   added to shared/citations.bib: AAP-BF-4E,
                   AAP-Period-2024, IAP-Period-2024, Owens-2005-BEARS,
                   CDC-Milestones-2022, RBSK-2013. §5 NEXT WORK ITEM
                   now points to B1-05 Skin.

2026-04-29  v0.3   B1-05 Skin Clinic drafted (DRAFT_COMPLETE). All 12
                   sections at or near target depth. First B1-tier
                   protocol; establishes the three-tier severity grading
                   inheritance pattern (Mild / Moderate / Severe / §7
                   Refractory) for the rest of the B1 library. Covers
                   atopic dermatitis (SCORAD), acne (IGA-Acne), common
                   pediatric infectious dermatoses (impetigo, scabies,
                   tinea, pediculosis, candidal intertrigo), reactive
                   dermatoses, and lesion surveillance. Embeds an
                   antimicrobial-stewardship 3-month-cap on oral
                   antibiotics for acne. Six [NEEDS EXPANSION] markers
                   plus six judgement-calls flagged in
                   protocols/B1-05-skin/STATUS.md. New citations added
                   to shared/citations.bib: AAD-2024-AD, AAD-2024-Acne,
                   IAP-Atopic-2023, IADVL-Scabies-2021, CDC-Scabies-2024,
                   AAD-Tinea-2014, Cochrane-CD003871, Cochrane-CD009864,
                   Stevens-2014-IDSA. §5 NEXT WORK ITEM now points to
                   B1-01 Vision.

2026-04-29  v0.4   B1-01 Vision Clinic drafted (DRAFT_COMPLETE). All 12
                   sections at or near target depth. First device-and-
                   allied-staff-driven B1 protocol; establishes the
                   in-clinic optometrist dependency pattern, the
                   in-clinic spectacle dispensing pattern, and the
                   IMI-2021-aligned myopia-control programme (low-dose
                   atropine 0.01% / 0.05% with documented progression
                   criteria). Covers refractive error (Mild / Moderate
                   / High), progressive myopia, allergic conjunctivitis,
                   bacterial conjunctivitis, convergence insufficiency,
                   colour-vision testing, and external lid disease. §7
                   includes leukocoria as a hard §7.1 trigger. Five
                   [NEEDS EXPANSION] markers plus six judgement-calls
                   flagged in protocols/B1-01-vision/STATUS.md. New
                   citations added to shared/citations.bib:
                   AAP-AAO-2016-Vision, AAPOS-Vision-2024, IMI-2021,
                   AAO-Conj-2018, AAP-Conj-2013, IAP-Vision-2022,
                   NPCB-2017, Cochrane-CD009078, PEDIG-Amblyopia. §5
                   NEXT WORK ITEM now points to B1-09 Nutrition &
                   Growth.

2026-04-29  v0.5   B1-09 Nutrition & Growth Clinic drafted
                   (DRAFT_COMPLETE). All 12 sections at or near target
                   depth. Highest A1 cross-reference density protocol:
                   inherits A1 §6.1 prophylactic supplementation, A1 §5
                   growth and MUAC flag thresholds, A1 vaccination-
                   visit POC Hb. Establishes the SKIDS dietitian
                   allied-staff dependency pattern (parallel to B1-01
                   optometrist) that B1-08, B1-10, and B1-13 will
                   reuse. Covers growth faltering, IDA, vitamin D / A
                   / B12 / zinc deficiency, picky eating / behavioural
                   feeding, CMPA management (joint with B1-06),
                   secondary lactose intolerance, breastfeeding and
                   complementary-feeding programmes, and adolescent
                   nutrition. SAM is hard out-of-scope to §7.1 partner
                   SAM ward; severe IDA to §7.1 / §7.2; refractory
                   faltering at 12 weeks to §7.3 pediatric GI. Four
                   [NEEDS EXPANSION] markers plus six judgement-calls
                   flagged in protocols/B1-09-nutrition-and-growth/STATUS.md.
                   New citations added to shared/citations.bib:
                   WHO-SAM-2013, WHO-IYCF-2023, IAP-Growth-2015,
                   IAP-IDA-2021, IAP-VitaminD-2017, ICMR-RDA-2020,
                   ESPGHAN-CF-2017, Cochrane-CD009085. §5 NEXT WORK
                   ITEM now points to B1-08 Behavioural.

2026-04-29  v0.6   B1-08 Behavioural Clinic drafted (DRAFT_COMPLETE).
                   All 12 sections at or near target depth. Most
                   sensitive protocol so far — establishes the LISSUN
                   external-therapy-partnership integration pattern,
                   the ADHD-pharmacotherapy cardiac-screen Companion
                   hard-block, the adolescent privacy / confidentiality
                   framework operational depth, and the suicidality
                   §7.1 protocol (safety plan + lethal-means counselling
                   + LISSUN psychiatrist pre-notification + child-not-
                   discharged-unaccompanied retention rule). Covers
                   ADHD (Vanderbilt-graded), autism screening (M-CHAT-
                   R/F to §7.3), adolescent depression and anxiety
                   (PHQ-A / GAD-7 with SSRI initiation per GLAD-PC),
                   disruptive behaviour, OCD / tic mild, adjustment /
                   PTSD, adolescent substance use (CRAFFT brief
                   intervention). Mental-health stigma cultural
                   framing applies functional language at screening
                   visits and formal diagnostic labels at confirmation
                   with consent. Three [NEEDS EXPANSION] markers plus
                   seven judgement-calls flagged in
                   protocols/B1-08-behavioural/STATUS.md. New citations
                   added to shared/citations.bib: AAP-Anxiety-2020,
                   AAP-Depression-2018, AAP-Suicide-2024,
                   IAP-Behaviour-2022, WHO-mhGAP-2023, NICE-ADHD-2018,
                   Robins-MCHATR-2014, Wolraich-Vanderbilt,
                   Goodman-SDQ-2001, PHQ-A-Validation. §5 NEXT WORK
                   ITEM now points to B1-06 Allergy.
```

---

## §10 PROJECT OWNER AND CONTACT

- **Project owner:** Dr. Satish Prasad Rath, Founder, SKIDS Health Technologies
- **Editorial reviewer:** Dr. Satish Prasad Rath (interim) + named
  subspecialist per protocol
- **Engineering integration:** SKIDS Tech Team (Shahid, Raghab Panda)
- **External therapy partner:** LISSUN (Behavioural / Adolescent)

---

*End of CLAUDE.md. If you have read this file, you are ready to work
on the SKIDS protocol library. Begin.*
