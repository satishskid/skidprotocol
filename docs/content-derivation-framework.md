# Content Derivation Framework — Role-Based Protocol Layers

**Purpose:** Define how the same clinical truth is expressed at three
depth levels for three audiences, all derived from the single-source
protocol library. Nothing is authored independently at any layer —
every claim traces back to a specific section of a specific protocol.

**Last updated:** 2026-05-01

---

## The three layers

```
┌─────────────────────────────────────────────────────────┐
│  LAYER 1: CLINICAL PROTOCOL (source of truth)           │
│  Audience: SKIDS pediatrician                            │
│  Language: Medical, specific, evidence-cited              │
│  Depth: Full — doses, thresholds, differentials, §7      │
│  Location: protocols/*/PROTOCOL.md                        │
├─────────────────────────────────────────────────────────┤
│  LAYER 2: MANAGER OPERATIONS GUIDE (derived)             │
│  Audience: SKIDS clinic manager                           │
│  Language: Operational, plain, no medical jargon          │
│  Depth: What the condition is, what tier it maps to,     │
│         parent objection scripts, enrolment workflow      │
│  Source: Derived from §1, §3, §10, §11 of each protocol │
├─────────────────────────────────────────────────────────┤
│  LAYER 3: PARENT SUPPORT PROGRAMME (derived)             │
│  Audience: Parents / caregivers                           │
│  Language: Everyday, empathetic, culturally sensitive     │
│  Depth: What the condition is, what SKIDS does about it, │
│         what the parent does at home, when to worry       │
│  Source: Derived from §1, §10, §10.4, §10.5              │
└─────────────────────────────────────────────────────────┘
```

**The derivation rule:** Layer 2 and Layer 3 content is always derived
FROM Layer 1. If a Layer 2 or Layer 3 document makes a claim that
cannot be traced to a specific section of a Layer 1 protocol, that
claim is unauthorised and must be removed. This is the institutional
discipline that prevents SKIDS from overpromising in marketing.

---

## Layer 1: Clinical Protocol (existing — complete)

**Audience:** Junior SKIDS pediatrician (MD Paeds)
**Voice:** Senior pediatrician to junior — confident, specific, no padding
**Content depth:**

| Content type | Example | Where in protocol |
|---|---|---|
| Drug doses | "Amoxicillin 50 mg/kg/day PO in 2 divided doses × 10 days" | §6 |
| Severity thresholds | "SCORAD ≥ 40 = severe; FEV1 < 60% = severe persistent" | §5 |
| Referral triggers | "SpO₂ < 92% → §7.1 ER within 1 hour" | §7 |
| Differential diagnosis | "Chronic cough: CVA vs PBB vs post-nasal drip vs TB vs foreign body" | §4 |
| Evidence citations | "[GINA-2024], [AAP-2017-HBP], [IAP-IDA-2021]" | §2 |
| Companion screens | "Screen 3: Examination form with auto-calculated severity" | §9 |

**This layer exists and is complete (27 protocols, 15,830 lines).**

---

## Layer 2: Manager Operations Guide (to be derived)

**Audience:** SKIDS clinic manager (non-medical; business/operations background)
**Voice:** Supportive colleague — clear, structured, action-oriented
**Content depth:**

| Content type | Derived from | What changes |
|---|---|---|
| Condition summary | §1 "What this clinic does" | Remove medical detail; keep service description in 2–3 sentences |
| Parent language | §3 presenting concerns table | Keep the "parent language" column; drop the "clinical translation" column |
| Subscription match | §11.2 | Keep the tier → condition mapping table |
| Parent objections | §11.3 | Keep all 5 objection/response scripts verbatim |
| Follow-up cadence | §8.1 | Simplify to: condition → next visit date → re-engagement trigger |
| Enrolment workflow | §11.4–§11.6 | Keep digital and in-person scripts |
| What NOT to say | (new) | Add a "do not promise" list derived from §1 "What this clinic does not do" |

**What managers do NOT see:**
- Drug doses, formulations, or prescribing details
- Severity grading thresholds or clinical scales
- §7 referral trigger specifics (managers see "doctor referred to specialist" not the clinical criteria)
- Evidence citations
- Companion Doctor Module screens

### Derivation template for Layer 2

For each protocol, produce a Manager Operations Card:

```markdown
# [Protocol Name] — Manager Card

## What this clinic does (2–3 sentences)
[Derived from §1, first paragraph, simplified]

## What parents say when they arrive
[Derived from §3 — parent language column only]

## Subscription tier match
| Condition pattern | Recommended tier |
|---|---|
[Derived from §11.2]

## Top parent objections (use these scripts)
[Derived from §11.3 — verbatim]

## Follow-up schedule (for scheduling)
| Condition | Next visit | Re-engage if missed by |
|---|---|---|
[Derived from §8.1, simplified]

## What we do NOT promise
[Derived from §1 "What this clinic does not do" — reframed as
"We do not offer [X] at this clinic; those cases go to a specialist"]

## Escalation
If the doctor flags a §7 referral, the Manager Console will show:
- Child's name and the specialist type needed
- Contact details for the SKIDS-T3 partner
- Your job: coordinate the appointment and follow up
```

---

## Layer 3: Parent Support Programme (to be derived)

**Audience:** Parents / caregivers (varied literacy, varied medical knowledge)
**Voice:** Warm, plain, respectful of intelligence, culturally aware
**Content depth:**

| Content type | Derived from | What changes |
|---|---|---|
| Condition explainer | §10.1 scripted explanations | Expand scripts into 150–300 word parent articles; add "What you might notice" and "What we do about it" |
| Home-care guide | §6 (Light tier) + §10 | Extract parent-actionable items: "Give the medicine at bedtime", "Use the spacer like this", "Limit juice to one small cup" |
| When-to-worry guide | §7.1 + §7.2 (parent-safe subset) | Translate emergency triggers into parent language: "Call us immediately if [child] stops breathing normally, turns blue, or cannot be woken" |
| FAQ | §10.5 cultural sensitivities | Turn each cultural-sensitivity point into a Q&A: "Q: Will my child become dependent on the inhaler? A: No. The preventer inhaler is not addictive..." |
| App content triggers | §10.4 | Each trigger ("new asthma diagnosis") activates a specific article/video in the parent app |

**What parents do NOT see:**
- Clinical scales, scores, or severity grading numbers
- Drug doses (parents see "the medicine the doctor prescribed" not "amoxicillin 50 mg/kg/day")
- §7 referral trigger criteria (parents see "the doctor has referred [child] to a specialist" not "FEV1 < 60%")
- Competitor comparisons or marketing language
- Anything that isn't derived from a protocol

### Derivation template for Layer 3

For each protocol, produce a Parent Support Pack:

```markdown
# Understanding [Condition] — For Parents

## What is [condition]?
[Derived from §10.1, expanded to 100–150 words, no jargon]

## What does SKIDS do about it?
[Derived from §1 "What this clinic does" + §6 Light/Standard tiers,
reframed as "Here's how we help [child]"]

## What you can do at home
[Derived from §6 parent-applied interventions + §10 home-care guidance]
- [Specific action 1]
- [Specific action 2]
- [Specific action 3]

## When to call us
[Derived from §7.1/§7.2, translated to parent language]
Call SKIDS immediately if:
- [Parent-language trigger 1]
- [Parent-language trigger 2]

## Common questions
[Derived from §10.5 cultural sensitivities, reframed as Q&A]

Q: [Common concern from §10.5]
A: [Response from §10.5, expanded]

## What happens next
[Derived from §8 follow-up schedule, simplified]
Your next visit is in [timeframe]. At that visit, we will [check X].
```

---

## How to derive (workflow)

### Step 1: One protocol at a time

Start with the highest-volume protocols:
1. A1 Screening (every family sees this)
2. B1-22 Vaccination (every family)
3. B1-05 Skin (highest commercial signal)
4. B1-01 Vision (high parent demand)
5. B1-09 Nutrition (high cross-reference)

### Step 2: Extract, don't rewrite

Open the Layer 1 protocol. Copy the source sections. Transform the
language — do NOT add new clinical claims. If you need to say something
that isn't in the protocol, stop and ask: "Should this be in the
protocol first?"

### Step 3: Trace every claim

Every sentence in a Layer 2 or Layer 3 document should be traceable:

```
Layer 3 sentence: "The inhaler medicine stays in the airways and
does not affect your child's growth."

Traced to: B1-14 §10.1 steroid-concerns script + B1-14 §6.5
contraindications ("ICS growth velocity reduction minimal at
low-medium doses")
```

If you cannot trace it, delete it.

### Step 4: Review cycle

```
Protocol author writes Layer 1
        ↓
Derivation author extracts Layer 2 + Layer 3
        ↓
Protocol author reviews Layer 2 + Layer 3 for accuracy
        ↓
Cultural reviewer checks Layer 3 for tone and sensitivity
        ↓
Published to Companion (Manager Console / Parent App)
```

---

## Language transformation rules

### Clinical → Manager

| Clinical (Layer 1) | Manager (Layer 2) |
|---|---|
| "Atopic dermatitis, SCORAD ≥ 40" | "Severe eczema" |
| "Initiate low-dose ICS (beclometasone 100 mcg/day)" | "Doctor starts a preventer inhaler" |
| "§7.3 to SKIDS-T3 pediatric cardiology" | "Doctor referred to heart specialist" |
| "PMNE with alarm therapy programme" | "Bedwetting programme with alarm device" |
| "Rome IV functional constipation" | "Chronic constipation (functional — not caused by a disease)" |
| "HbA1c 5.7–6.4% = pre-diabetes" | "Blood sugar is in the warning zone — not diabetes yet, but needs action" |

### Clinical → Parent

| Clinical (Layer 1) | Parent (Layer 3) |
|---|---|
| "Atopic dermatitis, SCORAD ≥ 40" | "Your child has eczema — the skin barrier doesn't hold moisture well, which makes it itchy and red" |
| "Bronchodilator reversibility positive" | "The breathing test showed that the medicine opens up the airways — this confirms asthma" |
| "tTG-IgA positive" | "The blood test suggests your child's body reacts to gluten — we need to confirm this" |
| "§7.1 emergency referral" | "We need to get [child] to the hospital right now — I'll explain why on the way" |
| "Pharmacotherapy for ADHD" | "A medicine that helps [child]'s brain focus — like glasses help eyes see" |

### Words to NEVER use in Layer 2 or Layer 3

| Never use | Use instead |
|---|---|
| "Protocol" | "Our care plan" / "the programme" |
| "§7 referral" | "specialist referral" / "the doctor referred to..." |
| "Tier 1 / Tier 2 / Tier 3" | "our clinic" / "a specialist" / "a hospital partner" |
| "SKIDS-T3" | "our [specialist type] partner" |
| "Severity grading" | "how serious it is" |
| "Contraindicated" | "not safe for [child] because..." |
| "Comorbidity" | "related condition" / "[child] also has..." |
| "Compliance / adherence" | "following the plan" / "taking the medicine as prescribed" |

---

## File structure (when derived content is produced)

```
skids-protocol-library/
├── protocols/                    ← Layer 1 (clinical, complete)
│   ├── A1-skids-screening/
│   │   └── PROTOCOL.md
│   ├── B1-01-vision/
│   │   └── PROTOCOL.md
│   └── ...
│
├── derived/                      ← Layer 2 + Layer 3 (to be built)
│   ├── manager-cards/
│   │   ├── A1-manager-card.md
│   │   ├── B1-01-manager-card.md
│   │   └── ...
│   ├── parent-packs/
│   │   ├── A1-parent-pack.md
│   │   ├── B1-01-parent-pack.md
│   │   └── ...
│   └── parent-app-content/
│       ├── articles/
│       ├── videos/              ← scripts derived from §10
│       └── trackers/            ← specs derived from §9.4
│
├── docs/
│   ├── how-to-use-this-library.md
│   ├── content-derivation-framework.md  ← this file
│   ├── tech-team-review-guide.md
│   └── citation-verification-guide.md
│
└── shared/
    └── citations.bib
```

---

## Derivation traceability matrix

Every derived document must include a traceability header:

```markdown
---
derived_from: B1-14-pulmonology-asthma/PROTOCOL.md
layer: 2 (manager) | 3 (parent)
sections_used: §1, §3, §10, §11
derived_by: [author name]
derived_date: YYYY-MM-DD
reviewed_by: [protocol owner]
review_date: YYYY-MM-DD
---
```

This header is what makes the derivation discipline auditable. If a
parent reads "SKIDS cures asthma" on the parent app and no protocol
says that, the traceability matrix reveals the unauthorised claim
immediately.

---

## Summary

| Layer | Audience | Depth | Derives from | Produces |
|---|---|---|---|---|
| 1 | Pediatrician | Full clinical | Evidence base | PROTOCOL.md (done) |
| 2 | Manager | Operational | §1, §3, §10, §11 | Manager cards (to build) |
| 3 | Parent | Plain language | §1, §10, §10.4, §10.5 | Parent packs + app content (to build) |

The protocol library is the spine. Everything else hangs off it.
Nothing is authored independently. This is the institutional
commitment that stops SKIDS from overpromising in marketing.
