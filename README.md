# SKIDS Clinical Protocol Library

The institutional clinical brain of SKIDS Health Technologies.

**Status:** Bootstrap (Gate 1 complete) · v0.1 · 2026-04-29

---

## What this is

This repository holds the SKIDS Clinical Protocol Library — a structured,
version-controlled collection of clinical protocols, one per pediatric
specialty service that SKIDS clinics deliver. Each protocol is written
by a senior pediatrician for a junior pediatrician and defines, in
exact terms, what conditions can be managed in a SKIDS OPD, what
diagnostics to run, what therapeutics to dispense, and when to refer.

The library serves four downstream audiences:

| Audience | What they read |
|---|---|
| **Junior SKIDS pediatrician** | The full protocol — uses it at the point of care via SKIDS Companion |
| **Subspecialist protocol owner** | The full protocol — does quarterly case-review against it |
| **SKIDS clinic manager** | A derived chapter — uses it for subscription enrolment and parent communication |
| **Parents** | A heavily derived summary — never the protocol itself |

The library is **internal IP**. It lives inside SKIDS Companion software
on AWS + Cloudflare. Parent-facing material is *derived from* protocols,
never authored independently.

---

## Why this matters

Most clinic chains have a marketing layer disconnected from a clinical
layer. They claim "world-class care" because their marketer wrote those
words, not because their protocols define what that phrase means. By the
time the parent shows up, the gap is visible.

SKIDS is built the other way around: protocols define the clinical truth,
and every parent-facing claim must trace back to a specific section of a
specific protocol. The library is therefore not a documentation
afterthought — it is the spine of the company.

---

## What's in this folder

```
skids-protocol-library/
│
├── CLAUDE.md                ← The project memory file. AI sessions read this first.
├── README.md                ← This file. Humans read this first.
├── SPECS.md                 ← Editorial specification (what makes a protocol "v1.0 complete")
│
├── docs/                    ← Reference documentation
│   ├── 00-protocol-template.md          The 12-section anatomy every protocol inherits
│   ├── 01-voice-and-style-guide.md      How protocols read
│   ├── 02-citation-conventions.md       How to cite IAP / AAP / etc.
│   ├── 03-companion-spec-format.md      How §9 (Companion workflow) is written
│   ├── 04-tier-system.md                Tier 1 / Tier 2 / Tier 3 definitions
│   ├── 05-referral-trigger-discipline.md  Why §7 is sacred
│   ├── 06-the-skids-fellowship.md       The credential pathway
│   └── future-tools.md                  Bookmarked tools (Frontend Slides, Graphify)
│
├── protocols/               ← The actual protocols
│   ├── _index.md            Master index of all 26 protocols with status
│   ├── A1-skids-screening/
│   │   ├── PROTOCOL.md      ← v1.0 draft, awaiting editorial pass
│   │   └── STATUS.md
│   ├── B1-01-vision/
│   │   └── STATUS.md        ← stub: not started
│   ├── ... (22 more B1 stubs)
│   └── B2-01-endocrine/ ... (3 B2 stubs)
│
├── shared/                  ← Cross-protocol reference content
│   ├── voice-samples.md     Good and bad voice examples
│   ├── glossary.md          Clinical abbreviations used
│   └── citations.bib        Bibliography (Markdown citation format)
│
├── workflows/               ← How to do the work
│   ├── how-to-write-a-protocol.md
│   ├── how-to-review-a-protocol.md
│   └── how-to-resume-a-stalled-protocol.md
│
├── setup-gsd.md             ← Installing and using the GSD harness
└── .gsd-conventions.md      ← How GSD phases map onto SKIDS protocol work
```

---

## How to use this repository

### If you're a Claude Code session

Read `CLAUDE.md` first. It tells you everything you need to know to be
productive in this project, including the current status of every
protocol and what to work on next.

### If you're a senior SKIDS pediatrician doing editorial review

1. Read `SPECS.md` to understand what "v1.0 approved" means.
2. Open the protocol marked "awaiting editorial pass" in `§4 STATUS TRACKER`
   of `CLAUDE.md`.
3. Use `workflows/how-to-review-a-protocol.md` as your editorial checklist.
4. Mark approval in the protocol's `STATUS.md` and update
   `CLAUDE.md §4 STATUS TRACKER`.

### If you're a SKIDS engineer integrating into Companion

Each protocol's §9 (Companion software workflow) specifies the doctor-module
UI requirements for that service. Each §11 (Manager handoff) specifies the
manager-console requirements. Build against these specs.

### If you're new to the project

Read in this order:
1. This README
2. `CLAUDE.md`
3. `docs/04-tier-system.md` — the clinical service map
4. `docs/00-protocol-template.md` — the anatomy
5. `protocols/A1-skids-screening/PROTOCOL.md` — the first complete example

---

## Project scale

| Metric | Number |
|---|---|
| Total protocols when complete | 27 (1 A1 + 23 B1 + 3 B2) |
| Estimated word count per protocol | 3,000–5,000 words |
| Estimated total library size | ~100,000 words |
| Estimated authoring sessions | 15–17 focused sessions |
| Estimated editorial review time | 2–4 hours per protocol |
| Estimated time to v1.0 complete library | 4–6 weeks part-time |

This is a serious institutional document, not a quick deliverable. The
quality bar is "would not embarrass IAP if published in their journal."

---

## What "complete" looks like

A protocol is **v1.0 approved** when:

- All 12 sections are written at full depth (no stubs)
- Every clinical claim has at least one citation from the approved evidence base
- §5 (Severity grading) and §7 (Hard referral triggers) have been
  specifically reviewed by a subspecialist named as protocol owner
- §9 (Companion workflow) has been signed off by SKIDS Engineering
- §11 (Manager handoff) has been tested with at least one SKIDS manager
- The protocol has been referenced successfully in at least 5 simulated
  patient cases without ambiguity

The library is **v1.0 complete** when all 27 protocols have reached
this state.

---

## Project owner

**Dr. Satish Prasad Rath**
Founder, SKIDS Health Technologies
satish@skids.health

---

## License and confidentiality

This protocol library is proprietary clinical IP of SKIDS Health Technologies.
It is not for external distribution. Derived parent-facing material may be
published on parent.skids.clinic; the protocols themselves remain internal.
