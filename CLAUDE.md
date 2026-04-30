# SKIDS CLINICAL PROTOCOL LIBRARY

> **READ THIS FILE FIRST, EVERY SESSION, BEFORE DOING ANYTHING ELSE.**
> Last updated: 2026-04-30 · v1.7 · 16 protocols drafted (A1 + B1-01 – B1-10 + B1-13 – B1-15 + B1-22 + B1-23)

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
- A1 — SKIDS Screening (drafted 2026-04-29; DRAFT_COMPLETE)
- B1-01 — Vision Clinic (drafted 2026-04-29; DRAFT_COMPLETE)
- B1-05 — Skin Clinic (drafted 2026-04-29; DRAFT_COMPLETE)
- B1-06 — Allergy Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-07 — Sleep Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-08 — Behavioural Clinic (drafted 2026-04-29; DRAFT_COMPLETE)
- B1-09 — Nutrition & Growth Clinic (drafted 2026-04-29; DRAFT_COMPLETE)
- B1-02 — Hearing & Ear Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-03 — Throat & Airway Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-04 — Oral Health Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-10 — Obesity & Metabolic Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-13 — Adolescent Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-14 — Pulmonology / Asthma Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-15 — Gastrointestinal Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-22 — Vaccination Clinic (drafted 2026-04-30; DRAFT_COMPLETE)
- B1-23 — Developmental Surveillance (drafted 2026-04-30; DRAFT_COMPLETE)

### Drafting now
- (none — between sessions)

### Stubbed (project structure exists, no PROTOCOL.md yet)
- B1-11 Speech & Language · B1-12 Learning
- B1-16 Cardiac · B1-17 Kidney & Urology · B1-18 Blood
- B1-19 Infections · B1-20 Bedwetting · B1-21 Constipation
- B2-01 Endocrine · B2-02 Neurology · B2-03 Rheumatology

### Editorial pass complete, awaiting deployment
- (none yet)

---

## §5 NEXT WORK ITEM

**Recommended next protocol to write: B1-20 Bedwetting**

Why:
- Sixteen protocols now drafted (59.3%). B1-15 GI closes the
  GI-nutrition-obesity axis (B1-09 + B1-10 + B1-15). The B1-15/
  B1-21 boundary is defined (functional constipation → B1-21;
  organic/refractory → B1-15).
- B1-20 Bedwetting and B1-21 Constipation are operationally
  simpler single-condition protocols. Drafting them clears two
  protocol slots efficiently.
- B1-20 crosses with B1-07 (sleep), B1-08 (psychosocial impact),
  and B1-17 Kidney (renal cause exclusion).

Alternatives in priority order:
- B1-21 Constipation (paired with B1-20; defined by B1-15 boundary).
- B1-11 Speech & Language (cross with B1-02, B1-23).
- B1-12 Learning (cross with B1-08, B1-23).
- B1-16 Cardiac.

When starting B1-20: read B1-07 (sleep/bedwetting overlap),
B1-08 (psychosocial impact), A1 (elimination history), and
AAP/ICCS enuresis guidelines.

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

2026-04-30  v0.8   B1-07 Sleep Clinic drafted (DRAFT_COMPLETE). Seventh
                   protocol. Slightly compressed style at some sections
                   but all 12 sections present at usable depth. Establishes
                   melatonin cautious-use framework per CLAUDE.md §7.2.
                   Domains: BIC, sleep-onset insomnia, OSA screening,
                   parasomnia, RLS, adolescent delayed sleep-phase. New
                   citations: AAP-Sleep-2016, AASM-OSA-2012,
                   IAP-Sleep-2020, AAP-Melatonin-2022, Mindell-Sleep-2017.

2026-04-30  v0.7   B1-06 Allergy Clinic drafted (DRAFT_COMPLETE). Sixth
                   protocol; closes A1 §7.1 anaphylaxis-without-action-
                   plan loop. Establishes adrenaline auto-injector
                   dispensing pattern (weight-banded), action plan
                   generation pattern, in-clinic OFC low-risk pattern
                   with resuscitation-kit hard-block, SLIT initiation
                   in primary care for monosensitised cases. Five
                   [NEEDS EXPANSION] markers + six judgement calls.
                   New citations: ARIA-2020, NIAID-Food-2010,
                   NIAID-Peanut-2017, EAACI-Food-2014,
                   WAO-Anaphylaxis-2020, EAACI-Urticaria-2022,
                   ICON-Rhinitis-2017, IAP-Allergy-2022,
                   Cochrane-CD001936, LEAP-2015. §5 NEXT WORK ITEM
                   now points to B1-07 Sleep.

2026-04-30  v1.7   B1-15 Gastrointestinal Clinic drafted
                   (DRAFT_COMPLETE). Sixteenth protocol (59.3%).
                   Closes GI-nutrition-obesity axis. Establishes Rome IV
                   FAPD classification, GORD management with PPI
                   stewardship (4–8 week limit), coeliac screening
                   (tTG-IgA + no-biopsy pathway), H. pylori test-and-
                   treat (dyspeptic symptoms only), chronic diarrhoea
                   structured differential, GI bleeding triage, NAFLD
                   hepatological workup (with B1-10), and B1-15/B1-21
                   constipation boundary. Three [NEEDS EXPANSION] markers
                   + five judgement calls. New citations: Rome-IV-2016,
                   NASPGHAN-GORD-2018, ESPGHAN-Coeliac-2020,
                   NASPGHAN-Hp-2017, IAP-GI-2021.
                   §5 NEXT WORK ITEM now points to B1-20 Bedwetting.

2026-04-30  v1.6   B1-23 Developmental Surveillance drafted
                   (DRAFT_COMPLETE). Fifteenth protocol (55.6%).
                   Establishes ASQ-3 + Trivandrum DST dual-track
                   developmental screening, DASII for Indian infants,
                   VSMS adaptive-behaviour assessment, five-domain
                   developmental assessment, early-intervention
                   initiation before formal diagnosis, developmental-
                   regression §7.2 bridge to neurology, established-
                   diagnosis monitoring programmes (Down syndrome, CP,
                   ASD), and shared DBP governance with B1-08. One
                   [NEEDS EXPANSION] marker + five judgement calls.
                   New citations: AAP-DevScreen-2020, IAP-Development-2020,
                   DASII, VSMS.
                   §5 NEXT WORK ITEM now points to B1-15 Gastrointestinal.

2026-04-30  v1.5   B1-04 Oral Health Clinic drafted
                   (DRAFT_COMPLETE). Fourteenth protocol (51.9%);
                   past the halfway mark. Completes head-and-neck
                   domain (B1-01 + B1-02 + B1-03 + B1-04). Establishes
                   pedodontist Tier 3 partner pattern, AAPD CAT caries-
                   risk assessment, fluoride varnish by pediatrician
                   (from first eruption, 2–4×/year), dietary-sugar
                   counselling for caries, WSL remineralisation,
                   dental-trauma triage per IADT, malocclusion screening,
                   oral mucosal management, and habit-cessation programme.
                   Three [NEEDS EXPANSION] markers + five judgement calls.
                   New citations: AAPD-Caries-2023, AAPD-Fluoride-2023,
                   AAP-Fluoride-2020, IADT-2020, IAP-OralHealth-2019,
                   WHO-OralHealth-2022.
                   §5 NEXT WORK ITEM now points to B1-23 Dev Surveillance.

2026-04-30  v1.4   B1-10 Obesity & Metabolic Clinic drafted
                   (DRAFT_COMPLETE). Thirteenth protocol (48.1%).
                   Establishes SKIDS Healthy Weight Programme (12-week
                   structured family-based lifestyle intervention),
                   metabolic-risk screening (fasting glucose, HbA1c,
                   lipids, ALT, TSH), pre-diabetes management within
                   B1-10, dyslipidaemia dietary trial, NAFLD lifestyle
                   trial, SKIDS dietitian-led dietary modification
                   (calorie-appropriate not restrictive), motivational
                   interviewing, and multi-protocol cross-care (B1-09
                   nutrition, B1-13 adolescent PCOS, B1-14 asthma-
                   obesity, B2-01 T2DM routing). One [NEEDS EXPANSION]
                   marker + five judgement calls. New citations:
                   AAP-Obesity-2023, IAP-Obesity-2022, AAP-T2DM-2013,
                   AAP-Lipid-2011, NASPGHAN-NAFLD-2017.
                   §5 NEXT WORK ITEM now points to B1-04 Oral Health.

2026-04-30  v1.3   B1-03 Throat & Airway Clinic drafted
                   (DRAFT_COMPLETE). Twelfth protocol (44.4%);
                   completes ENT domain (B1-02 + B1-03). Establishes
                   RADT-guided GAS pharyngitis management with RF
                   prevention (9-day window), McIsaac scoring, Brodsky
                   tonsillar grading, Paradise criteria for tonsillectomy
                   candidacy, Westley croup scoring with dexamethasone +
                   nebulised adrenaline protocol, peritonsillar cellulitis
                   management, RF secondary prophylaxis (benzathine
                   penicillin G 3-weekly), stridor assessment and
                   epiglottitis §7.1, and post-tonsillectomy follow-up.
                   Two [NEEDS EXPANSION] markers + five judgement calls.
                   New citations: AAP-GAS-2012, AAP-Tonsillectomy-2011,
                   AAP-Croup-2021, IAP-RF-2008, WHO-RF-2004.
                   §5 NEXT WORK ITEM now points to B1-10 Obesity.

2026-04-30  v1.2   B1-02 Hearing & Ear Clinic drafted
                   (DRAFT_COMPLETE). Eleventh protocol (40.7%).
                   Establishes OAE-based hearing surveillance aligned
                   with JCIH 1-3-6, tympanometry and pure-tone
                   audiometry, AOM management per AAP 2013 (watchful
                   waiting for non-severe ≥ 2y), OME 3-month watchful
                   waiting with grommet routing, cerumen management,
                   hearing-loss classification (WHO) and hearing-aid /
                   cochlear-implant candidacy routing, and ENT surgical-
                   partner handoff pattern (grommets, adenoidectomy,
                   cochlear implant). One [NEEDS EXPANSION] marker +
                   six judgement calls. New citations: JCIH-2019,
                   AAO-HNS-2016-OME, WHO-Hearing-2021, IAP-Hearing-2020.
                   §5 NEXT WORK ITEM now points to B1-03 Throat & Airway.

2026-04-30  v1.1   B1-14 Pulmonology / Asthma Clinic drafted
                   (DRAFT_COMPLETE). Tenth protocol (37.0%); closes
                   the atopic-march triad (B1-05 AD + B1-06 allergy +
                   B1-14 asthma). Establishes GINA 2024 stepwise
                   management (Steps 1–4 in Tier 1; Step 5 → §7.3),
                   spirometry / peak-flow device protocol, pre/post-
                   bronchodilator reversibility testing, asthma action
                   plan generation (traffic-light format), spacer
                   technique training, acute exacerbation in-clinic
                   management, mAPI for recurrent wheeze in under-5s,
                   chronic cough workup (cough-variant asthma, PBB,
                   post-nasal drip, TB), and B1-06 asthma_status PHR
                   communication object. Shared governance with B1-06.
                   Three [NEEDS EXPANSION] markers + six judgement calls
                   in protocols/B1-14-pulmonology-asthma/STATUS.md.
                   New citations: IAP-Asthma-2021, GINA-U5-2024.
                   §5 NEXT WORK ITEM now points to B1-02 Hearing & Ear.

2026-04-30  v1.0   B1-22 Vaccination Clinic drafted (DRAFT_COMPLETE).
                   Ninth protocol (33.3%); most operationally dense
                   in the library. Establishes IAP IIS 2024-25
                   reconciliation workflow, catch-up scheduling per
                   IAP minimum intervals, cold-chain management
                   protocol, HPV programme delivery (2-dose / 3-dose
                   per age; boys and girls), travel-vaccine counselling,
                   AEFI documentation and WHO-classification reporting,
                   vaccine-hesitancy motivational-interviewing framework,
                   special-population modified schedules (preterm,
                   immunocompromised, post-transplant), and anaphylaxis
                   management at vaccination station. Five [NEEDS
                   EXPANSION] markers + six judgement calls flagged in
                   protocols/B1-22-vaccination/STATUS.md. New citations
                   added to shared/citations.bib: WHO-AEFI-2019,
                   IAP-AEFI-2020, IAP-IIS-HPV, WHO-HPV-2022,
                   IAP-Catch-Up, CDC-Travel-2024. §5 NEXT WORK ITEM
                   now points to B1-14 Pulmonology / Asthma.

2026-04-30  v0.9   B1-13 Adolescent Clinic drafted (DRAFT_COMPLETE).
                   Eighth protocol; most culturally complex in the
                   library. Establishes the HEEADSSS private-interview
                   framework, contraception counselling and provision
                   pattern (barrier + COC/POP/DMPA/EC; LARC routed to
                   gynaecology partner), STI testing and treatment
                   in primary care (uncomplicated gonorrhoea/chlamydia/
                   trichomoniasis per CDC-STI-2021), POCSO mandatory-
                   reporting confidentiality override, adolescent-
                   private Companion login, and menstrual-health
                   management (dysmenorrhoea, menorrhagia, amenorrhoea,
                   PCOS workup routing). Five [NEEDS EXPANSION] markers
                   + seven judgement calls flagged in
                   protocols/B1-13-adolescent/STATUS.md. New citations
                   added to shared/citations.bib: IAP-Adolescent-2023,
                   POCSO-2012, WHO-Adolescent-2024, CDC-STI-2021,
                   ACOG-Adolescent-2017, ICMR-NMHS-2016, NCERT-AEP.
                   §5 NEXT WORK ITEM now points to B1-22 Vaccination.

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
