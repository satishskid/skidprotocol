# SPECS.md

**Editorial specification for the SKIDS Clinical Protocol Library**
v1.0 · 2026-04-29

This document defines the quality bar for the SKIDS protocol library.
It is the contract between authors and editorial reviewers. If a
protocol does not meet every specification below, it is not "v1.0
approved" — regardless of how complete it appears.

---

## 1. Document anatomy

Every protocol has exactly 12 sections, in this order, with these names:

```
§1   Service definition
§2   Evidence base
§3   Presenting concerns
§4   Diagnostic workflow
§5   Severity grading
§6   Therapeutic options
§7   Hard referral triggers
§8   Follow-up schedule
§9   Companion software workflow
§10  Parent-facing communication
§11  Manager handoff
§12  Quality and audit
```

Section names are not negotiable. Adding sections is not allowed without
updating `docs/00-protocol-template.md` first. Skipping sections is not
allowed. Reordering sections is not allowed.

---

## 2. Section depth requirements

### §1 Service definition (target: 200–400 words)
Must specify:
- What this clinic does (one sentence)
- What this clinic explicitly does not do (one sentence)
- Age range covered (specific years)
- Subscription tier(s) it sits in (Basic / Advanced / Premium with rationale)
- Tier classification (Tier 1 / Tier 2 / complex tier of Tier 1)

### §2 Evidence base (target: 300–500 words)
Must include:
- Full bibliography of governing guidelines with version/year
- Last updated date for the protocol itself
- Next scheduled review date (typically 12 months)
- Named protocol owner (subspecialist responsible for governance)
- Any departures from cited guidelines must be flagged and justified

### §3 Presenting concerns (target: 400–700 words)
Must include:
- 8–15 reasons a child arrives at this clinic
- Each presented in *both* parent-language and clinical-language
- Routing logic: which screening flag or symptom maps to this protocol vs. another

### §4 Diagnostic workflow (target: 700–1,200 words)
Must include:
- Structured history-taking template (specific questions)
- Examination checklist (specific findings to elicit)
- Named questionnaires/scales used with cutoff thresholds
- In-clinic device tests required
- Laboratory/imaging investigations with thresholds for ordering
- Decision tree showing what each finding means for §5 severity grading

### §5 Severity grading (target: 300–500 words)
**This section is sacred.** It must include:
- The named severity classification used (e.g., GINA steps, SCORAD, M-CHAT-R)
- Explicit numeric or categorical thresholds for each tier
- Mapping from severity tier to intervention tier (Light / Standard / Intensive)
- Mapping from severity tier to subscription tier
- The threshold above which §7 (Hard referral) triggers

If the established medical literature does not provide a clean severity
grading for this condition, the protocol must explicitly say so and
provide the SKIDS-specific operational severity definition with full
justification.

### §6 Therapeutic options (target: 800–1,400 words)
Must include:
- Drug list with weight-based pediatric dosing tables
- Behavioural and lifestyle protocols with specific instructions
- Parent-applied interventions with technique descriptions
- Allied-staff-delivered interventions with named staff role
- In-clinic dispensary stock list (what SKIDS keeps on shelf)
- Contraindications and precautions for each therapeutic
- Expected timeline to clinical improvement for each intervention

### §7 Hard referral triggers (target: 400–600 words)
**This section is sacred.** It must include:
- Non-negotiable rules for case escalation, written as a checklist
- The named partner / subspecialist each trigger refers to
- The handoff communication required (what the SKIDS ped sends with the referral)
- Time-sensitivity: which triggers are emergency vs. urgent vs. routine

A protocol fails editorial review if §7 is vague. "Refer if not improving"
is not a hard trigger. "Refer if SCORAD remains >40 after 4 weeks of
optimised topical therapy" is.

### §8 Follow-up schedule (target: 300–500 words)
Must include:
- Frequency of follow-up by severity tier
- What to recheck at each follow-up (specific findings, not "review progress")
- Definition of treatment success (specific endpoints)
- Step-down criteria (when to reduce intensity of intervention)
- Step-up criteria (when to escalate within Tier 1 or refer to Tier 2/3)

### §9 Companion software workflow (target: 500–800 words)
Must specify, screen by screen:
- What the Doctor Module renders at each step of the consult
- Which fields are mandatory entry vs. optional
- What gets logged to the child's PHR
- What gets shown to the parent (in real time and in the post-visit summary)
- What triggers a manager alert
- What auto-populates the prescription / dispensary order

This is a hard specification for SKIDS Engineering, not a wish list.
If you cannot specify a screen layout, write the data fields and let
the engineering team design the screen.

### §10 Parent-facing communication (target: 400–600 words)
Must include:
- A scripted parent explanation of the diagnosis (in plain English, ≤150 words)
- A parent explanation of the chosen intervention tier (≤100 words)
- The post-visit summary template (what auto-fills in the parent's PHR)
- Which HABITS / Practice content (on parent.skids.clinic) is activated
  for this family
- Talking points for cultural sensitivities (e.g., mental health stigma)

### §11 Manager handoff (target: 400–600 words)
Must include:
- What the Manager Console surfaces from this protocol
- The matching subscription tier with pricing reference
- The intervention tier within that subscription (Light / Standard / Intensive)
- Top 5 parent objections specific to this service with one-line responses
- Digital onboarding flow for QR-scan parents
- In-person enrolment script for walk-in parents

### §12 Quality and audit (target: 200–400 words)
Must include:
- Metrics that define this protocol working well (specific outcomes)
- Quarterly case review trigger (sample size, what reviewer looks for)
- Minimum case load to maintain ped certification on this protocol
- Continuing-education requirement (hours/year, named courses if any)
- The SKIDS Fellowship pathway for advancing into the credentialed tier

---

## 3. Citation discipline

Every clinical claim must have at least one citation. Citation format
(see `docs/02-citation-conventions.md` for full rules):

```
[IAP-IIS-2024]      = IAP Immunisation Schedule, 2024-25
[AAP-2013-AOM]      = AAP Otitis Media Clinical Practice Guideline, 2013
[GINA-2024]         = GINA Asthma Management Strategy, 2024
[NELSON-21]         = Nelson Textbook of Pediatrics, 21st edition
[IAP-TB-6E]         = IAP Textbook of Pediatrics, 6th edition
[Cochrane-XXXXX]    = Cochrane Review identifier
[PMID:XXXXXXXX]     = PubMed ID
```

Citations appear in-text as bracket tags and are aggregated in `§2 Evidence base`.

Acceptable density: roughly 1 citation per 200–300 words of clinical content.
Sparser than that suggests under-cited claims. Denser than that often
suggests citation-padding without specificity.

---

## 4. Voice requirements

See `docs/01-voice-and-style-guide.md` for full rules. Summary:

- Senior pediatrician writing for a junior pediatrician
- No padding, no marketing, no exclamation marks
- No "we" or "our" except when describing SKIDS-specific protocols
- Active voice for clinical instructions
- Specific over general always (numbers, not "some")
- Decisions over discussions ("Use amoxicillin 50 mg/kg/day in 3 divided
  doses for 5 days" not "Antibiotic therapy is sometimes considered")
- The reader is medically intelligent and time-pressed; respect that

---

## 5. Status states

Every protocol's `STATUS.md` must declare exactly one of these states:

```
NOT_STARTED              — Stub directory exists, no PROTOCOL.md
IN_PROGRESS              — PROTOCOL.md exists, sections being written
DRAFT_COMPLETE           — All 12 sections drafted, ready for editorial pass
EDITORIAL_IN_PROGRESS    — A senior reviewer is actively editing
APPROVED                 — Editorial pass complete, ready for Companion deployment
DEPLOYED                 — Live in Companion software at SKIDS clinics
```

Transitions require updating both the protocol's `STATUS.md` and the
`§4 STATUS TRACKER` in `CLAUDE.md`.

---

## 6. Editorial review checklist

A protocol passes editorial review only if all of the following are true:

- [ ] All 12 sections present and at target depth
- [ ] §5 severity grading thresholds are specific and numeric
- [ ] §7 hard referral triggers are non-negotiable and specific
- [ ] Every clinical claim has at least one valid citation
- [ ] Drug doses are weight-based with explicit pediatric ranges
- [ ] Cultural caveats (Indian context, antimicrobial stewardship,
      mental health stigma) are addressed where relevant
- [ ] Companion §9 specification is implementable, not aspirational
- [ ] Manager §11 handoff is tested or testable
- [ ] No `[NEEDS EXPANSION]` markers remain
- [ ] Protocol owner (subspecialist) has signed off on §2, §5, §7
- [ ] Ready for SKIDS Engineering integration into Companion

---

## 7. Honest stubs over dishonest completeness

If a section is under-developed, mark it
`[NEEDS EXPANSION IN EDITORIAL PASS]` rather than padding it. The
editorial reviewer's time is better spent expanding flagged stubs than
catching hidden thinness. A protocol with 3 honest stubs is closer to
v1.0 than a protocol with 0 stubs and 3 vague paragraphs.

---

## 8. The non-negotiable bar

Repeating from `CLAUDE.md` because this is the most important sentence
in the entire SPECS.md:

> The quality bar is "good enough to defend in front of a medical council
> if a case goes wrong." Every protocol should read as though it could
> appear in IAP's published guidance without embarrassment.

If you wouldn't stake your medical license on what's written in §5, §6,
or §7 — keep editing.
