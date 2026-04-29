# SKIDS CLINICAL PROTOCOL LIBRARY

> **READ THIS FILE FIRST, EVERY SESSION, BEFORE DOING ANYTHING ELSE.**
> Last updated: 2026-04-29 · v0.1 · Gate 1 (bootstrap)

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
- A1 — SKIDS Screening (drafted 2026-04-29)

### Drafting now
- (none — between sessions)

### Stubbed (project structure exists, no PROTOCOL.md yet)
- B1-01 Vision · B1-02 Hearing & Ear · B1-03 Throat & Airway
- B1-04 Oral Health · B1-05 Skin · B1-06 Allergy
- B1-07 Sleep · B1-08 Behavioural · B1-09 Nutrition & Growth
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

**Recommended next protocol to write: B1-05 Skin**

Why:
- Highest commercial signal under the prevalence × felt-need × dispensable
  rubric (top tier on all three filters)
- Most diverse therapeutic kit (topicals, orals, behavioural, parent-applied)
  — sets the pattern for every other protocol
- Visible problem → visible solution arc demonstrates the SKIDS model
- Once Skin is locked, Vision, Allergy, Sleep, Behavioural, Nutrition all
  inherit the established pattern with ~40% less authoring time

Alternative if Skin is blocked: Vision (next-strongest exemplar).

---

## §6 HOW TO WORK ON THIS PROJECT

### When opening a fresh Claude Code session

1. Read this file (`CLAUDE.md`) end-to-end.
2. Read `docs/01-voice-and-style-guide.md` if you haven't recently.
3. Read the most recently completed protocol as a voice anchor — currently
   `protocols/A1-skids-screening/PROTOCOL.md`.
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
2026-04-29  v0.1  Gate 1 bootstrap. CLAUDE.md, README.md, SPECS.md,
                  protocol template, voice guide, citation conventions,
                  tier system, referral discipline, fellowship doc,
                  workflows, GSD integration, future-tools bookmarks,
                  A1 SKIDS Screening protocol drafted.
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
