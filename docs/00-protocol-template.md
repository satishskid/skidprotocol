# PROTOCOL TEMPLATE — SKIDS Clinical Protocol Library

**This is the template every SKIDS protocol inherits.** Copy this file
to `protocols/B1-XX-name/PROTOCOL.md`, fill in each section per the
guidance below, and remove the italicised author guidance once content
is written. Refer to `SPECS.md` for the editorial bar each section
must meet.

---

```yaml
---
protocol_id: B1-XX-name              # e.g., B1-05-skin
protocol_name: SKIDS [Service] Clinic
tier: 1                              # 1 | 2 | 3
status: NOT_STARTED                  # see §5 of SPECS.md for valid states
version: 0.1
authored: 2026-MM-DD
last_updated: 2026-MM-DD
next_review: 2027-MM-DD
protocol_owner: Dr. [Name], [Subspecialty Credential]
editorial_reviewer: pending
companion_module_status: not_specified
---
```

---

# SKIDS [Service Name] Clinic

> One-sentence positioning of this clinic — what it does, for whom, how
> it differs from a generalist visit. Roughly 25–40 words.

---

## §1 Service definition

*Author guidance: 200–400 words. State plainly what this clinic does and
what it does not do. The "does not do" is as important as the "does" —
it defines the boundary that protects the patient and the platform.*

**What this clinic does:**
- [Specific clinical activities, not marketing language]

**What this clinic does not do:**
- [Specific exclusions — these escalate to §7 hard referral triggers]

**Age range covered:** [exact years, e.g., 6 months – 18 years]

**SKIDS subscription tier(s):**
- Basic ₹2,999 — [what this service offers Basic subscribers]
- Advanced ₹6,999 — [what Advanced subscribers get additionally]
- Premium ₹12,999 — [what Premium subscribers get additionally]

**SKIDS clinical tier:** Tier 1 / Tier 2 / [if Tier 1, note the
complex tier escalation path to Tier 2 or Tier 3]

---

## §2 Evidence base

*Author guidance: 300–500 words. List every guideline this protocol
follows, with version and year. Name the protocol owner — the subspecialist
responsible for quarterly governance review. Flag any departures from
cited guidelines and justify them.*

This protocol governs [service]. It follows the most current
recommendations from:

- [Citation tag] — [Full citation with year]
- [Citation tag] — [Full citation with year]
- [...]

**Last updated:** YYYY-MM-DD
**Next scheduled review:** YYYY-MM-DD
**Protocol owner:** Dr. [Name], [Credential] — quarterly case review

**Departures from cited guidelines:**
[If this protocol deviates from any cited guideline — e.g., a more
conservative threshold than AAP recommends due to Indian antimicrobial
resistance patterns — state the deviation clearly and justify it. If
none, write "No material departures from cited guidelines."]

---

## §3 Presenting concerns

*Author guidance: 400–700 words. List 8–15 specific reasons a child
arrives at this clinic. For each, write the parent-language version
("the way the parent describes it") and the clinical-language version
("what the pediatrician hears"). Then explain the routing logic — how
to know this concern belongs to this protocol vs. a different one.*

A child arrives at the SKIDS [Service] Clinic via one of these paths:

| Parent language | Clinical language | Likely routing |
|---|---|---|
| "[How a parent describes it]" | [Clinical translation] | This protocol / Other protocol if [condition] |
| ... | ... | ... |

**Routing decisions:**
- If [condition], this is the right protocol because [reason]
- If [condition], route to [other protocol] because [reason]
- If [condition], escalate per §7 hard referral triggers

**Coming from SKIDS Screening (A1):**
The following A1 screening flags route automatically to this clinic:
- [Flag name and threshold]
- [Flag name and threshold]

---

## §4 Diagnostic workflow

*Author guidance: 700–1,200 words. The longest practical section.
Specify exactly what the SKIDS pediatrician does, in what order, with
what tools, to reach a diagnosis severity grade. This is the protocol
the Companion Doctor Module will render at the point of care.*

### 4.1 Structured history

Ask, in this order:
1. [Specific question with rationale]
2. [Specific question with rationale]
...

Red flags to elicit:
- [Specific finding]
- [Specific finding]

### 4.2 Examination

Examine for:
- [Specific finding to check, with technique]
- [Specific finding to check, with technique]

### 4.3 Scales and questionnaires

Use the [named scale]. Cutoffs:
- Score 0–X: [interpretation]
- Score Y–Z: [interpretation]
- Score >Z: [interpretation]

### 4.4 In-clinic device tests

Required:
- [Device] — [what it measures, how to interpret]

Optional (if clinically warranted):
- [Device] — [indication]

### 4.5 Laboratory and imaging

Order:
- [Test] if [specific indication and threshold]
- [Test] if [specific indication and threshold]

Do not order routinely:
- [Test] — [reason]

### 4.6 Decision tree

```
Initial presentation
    ↓
History + exam + screening scale
    ↓
    ├── If [criteria A] → severity grade [X], proceed to §6 [tier]
    ├── If [criteria B] → severity grade [Y], proceed to §6 [tier]
    └── If [criteria C] → §7 hard referral triggered
```

---

## §5 Severity grading [SACRED SECTION]

*Author guidance: 300–500 words. This section is sacred. Use a named
severity classification from the literature (e.g., GINA, SCORAD,
M-CHAT-R severity bands). If no clean classification exists, define the
SKIDS-specific operational severity grade explicitly with full
justification. Map severity to intervention tier (Light/Standard/
Intensive) and to subscription tier.*

This protocol uses the [named scale] to grade severity.

| Severity grade | Threshold | Intervention tier | Subscription tier |
|---|---|---|---|
| **Mild** | [Specific numeric/categorical threshold] | Light | Basic ₹2,999 |
| **Moderate** | [Specific numeric/categorical threshold] | Standard | Advanced ₹6,999 |
| **Severe** | [Specific numeric/categorical threshold] | Intensive | Premium ₹12,999 |
| **Beyond Tier 1** | [Specific numeric/categorical threshold] | §7 referral | — |

**Boundary rules:**
- Borderline between Mild/Moderate: [tie-breaking rule]
- Re-grading after intervention: [when to re-grade]
- Severity progression triggers: [what counts as escalation requiring
  protocol re-entry]

---

## §6 Therapeutic options

*Author guidance: 800–1,400 words. The most operationally important
section. Specify drugs with weight-based pediatric dosing tables.
Specify behavioural and lifestyle protocols with techniques. Specify
parent-applied interventions with instructions. Specify allied-staff-
delivered components with named roles. List the in-clinic dispensary
stock that this protocol relies on.*

### 6.1 Light tier (Mild severity)

**Pharmacological:**
| Drug | Indication | Pediatric dose | Duration |
|---|---|---|---|
| [Drug] | [Indication] | [mg/kg/day, route, frequency] | [Duration] |

**Behavioural / Lifestyle:**
- [Specific instruction with technique]

**Parent-applied:**
- [Specific instruction with frequency and technique]

**Allied staff:**
- [Role] delivers [intervention] [frequency]

**Dispensary stock:**
- [Item] — [supplier, package size, restocking cycle]

**Expected timeline to improvement:** [specific weeks]

### 6.2 Standard tier (Moderate severity)

[Same structure as 6.1]

### 6.3 Intensive tier (Severe severity)

[Same structure as 6.1]

### 6.4 Contraindications and precautions

| Therapeutic | Contraindication | Action |
|---|---|---|
| [Drug] | [Condition] | [Substitute drug or refer per §7] |

### 6.5 Tapering and stopping

[How to step down once condition controlled]

---

## §7 Hard referral triggers [SACRED SECTION]

*Author guidance: 400–600 words. This section is sacred. Each trigger
must be non-negotiable, specific, and tied to a named referral
destination. Vague triggers fail editorial review. Time-sensitivity
must be clear: emergency vs. urgent vs. routine.*

The case escalates out of this protocol's scope when ANY of the
following is true:

### 7.1 Emergency referral (same day)

- [ ] [Specific finding] → [Named partner / hospital] within [time]
- [ ] [Specific finding] → [Named partner / hospital] within [time]

### 7.2 Urgent referral (within [N days])

- [ ] [Specific finding] → [Named subspecialist / partner] within [N days]
- [ ] [Specific finding] → [Named subspecialist / partner] within [N days]

### 7.3 Routine referral (next available appointment)

- [ ] [Specific finding] → [Named subspecialist / partner]
- [ ] [Specific finding] → [Named subspecialist / partner]

### 7.4 Handoff communication

When referring, the SKIDS pediatrician must send the receiving clinician:
1. [Specific data point]
2. [Specific data point]
3. [Specific data point]

This packet is auto-generated by Companion when the §7 trigger fires.

---

## §8 Follow-up schedule

*Author guidance: 300–500 words. Specify follow-up frequency by severity
tier. Specify what to recheck at each visit (specific findings, not
"review progress"). Define treatment success with specific endpoints.
Specify step-down and step-up criteria.*

### 8.1 Follow-up frequency

| Severity tier | First follow-up | Subsequent | Annual review |
|---|---|---|---|
| Mild (Light) | [N weeks] | [Frequency] | Yes |
| Moderate (Standard) | [N weeks] | [Frequency] | Yes |
| Severe (Intensive) | [N weeks] | [Frequency] | Yes |

### 8.2 What to recheck at each follow-up

- [Specific finding 1]
- [Specific finding 2]
- [Specific scale to re-administer]

### 8.3 Treatment success criteria

The intervention is considered successful when:
- [Specific endpoint with threshold]
- [Specific endpoint with threshold]

### 8.4 Step-down criteria

Reduce intervention intensity when:
- [Specific criteria]

### 8.5 Step-up criteria (within Tier 1)

Escalate intensity (Light → Standard → Intensive) when:
- [Specific criteria]

### 8.6 Step-out criteria

Escalate beyond Tier 1 (§7 hard referral) when:
- [Specific criteria — these should match §7 triggers]

---

## §9 Companion software workflow

*Author guidance: 500–800 words. This is the engineering specification
for the Companion Doctor Module. Specify, screen by screen, what the
Doctor Module renders during a consult for this clinic. Specify the
data fields that get logged. Specify what triggers alerts to the
manager. Do not defer this to "engineering will figure it out."*

### 9.1 Doctor Module screens

**Screen 1: Pre-consult summary**
The Doctor Module presents (auto-populated from PHR):
- [Field 1]
- [Field 2]
- [Field 3]

**Screen 2: History intake**
The Doctor Module renders the §4.1 structured history as a form with:
- [Field with input type]
- [Field with input type]

**Screen 3: Examination findings**
[Form fields for §4.2 findings]

**Screen 4: Severity grading (auto-calculated)**
The Doctor Module presents the calculated severity grade with the
underlying scores visible. Doctor can override with documented reason.

**Screen 5: Therapeutic plan**
The Doctor Module pre-fills the §6 tier matched to the severity grade.
Doctor approves or modifies. Approval auto-generates:
- Prescription
- Dispensary order
- Parent-facing summary
- Manager alert (if subscription enrolment indicated)

**Screen 6: Follow-up scheduling**
[Auto-suggests follow-up date per §8.1]

### 9.2 Data logged to PHR

Each consult logs:
- [Field, structured]
- [Field, structured]

### 9.3 Alerts

| Trigger | Alert recipient | Channel |
|---|---|---|
| §7 hard referral fired | Manager + receiving clinician | Companion alert + WhatsApp |
| Subscription enrolment opportunity | Manager | Companion alert |
| Follow-up missed | Manager + parent | WhatsApp |

### 9.4 Parent app rendering

The post-consult parent app shows:
- [Item from §10 Parent-facing communication]
- [Activated HABITS / Practice content]

---

## §10 Parent-facing communication

*Author guidance: 400–600 words. Write the actual scripts the
pediatrician uses to explain diagnosis and intervention to the parent.
Plain English. No jargon unless explicitly defined. Include cultural
sensitivities. Specify what parent.skids.clinic content gets activated.*

### 10.1 Scripted diagnosis explanation

When grading is Mild:
> "[150 words or fewer of plain-English explanation that respects the
> parent's intelligence and time]"

When grading is Moderate:
> "[Same constraint]"

When grading is Severe:
> "[Same constraint]"

When §7 referral fires:
> "[How to explain the referral without alarming the parent
> unnecessarily, while conveying urgency where required]"

### 10.2 Scripted intervention tier explanation

> "[100 words explaining what the parent will do, what the clinic will
> do, and what to expect over the next [N weeks]]"

### 10.3 Post-visit summary template

Auto-fills in the parent's PHR:
```
[Template with fillable fields, written in parent-friendly language]
```

### 10.4 parent.skids.clinic content activated

After this consult, the family's account on parent.skids.clinic
unlocks:
- [Specific Learn article]
- [Specific Grow body-system page]
- [Specific Practice habit programme]

### 10.5 Cultural sensitivities

[Any context-specific framing needed for Indian families. Examples:
mental health stigma, generational dietary norms, school-vs-home
communication, etc.]

---

## §11 Manager handoff

*Author guidance: 400–600 words. The manager-asset spine. Specify what
the Manager Console surfaces from this protocol. Include the
subscription tier match, top 5 parent objections with responses, and
both digital and in-person enrolment scripts.*

### 11.1 Manager Console renders

After the doctor consult fires the manager alert, the Manager Console
shows:
- Child's name and age
- Diagnosis (in parent-friendly form)
- Recommended subscription tier
- Recommended intervention tier within that subscription
- Pricing reference
- Parent contact details
- Suggested next action (in-person enrolment / digital follow-up)

### 11.2 Subscription tier match

| Severity grade | Recommended subscription | Rationale |
|---|---|---|
| Mild | Basic ₹2,999 | [Why this tier matches] |
| Moderate | Advanced ₹6,999 | [Why this tier matches] |
| Severe | Premium ₹12,999 | [Why this tier matches] |

### 11.3 Top parent objections and responses

| Objection | Manager response |
|---|---|
| "[Common objection 1]" | "[One-line response anchored in protocol]" |
| "[Common objection 2]" | "[Response]" |
| ... (5 total) | ... |

### 11.4 Digital enrolment flow (QR-scan parents)

[Step-by-step digital onboarding for parents arriving via post-screening
QR scan]

### 11.5 In-person enrolment script (walk-in parents)

[Step-by-step manager script for walk-in conversion at the clinic
front desk]

### 11.6 Follow-up cadence (manager-driven)

| Touchpoint | Channel | Trigger |
|---|---|---|
| Welcome | WhatsApp | Same day as enrolment |
| Reminder | WhatsApp | 24h before follow-up |
| Re-engagement | Phone | Missed follow-up |

---

## §12 Quality and audit

*Author guidance: 200–400 words. Specify the metrics that define this
protocol working well. Specify the quarterly case review process.
Specify the SKIDS Fellowship pathway for advancing into the credentialed
subspecialty tier (if applicable).*

### 12.1 Outcome metrics

This protocol is working well when:
- [Specific outcome with target rate, e.g., "≥80% of Standard-tier
  patients reach treatment success by 8 weeks"]
- [Specific outcome with target rate]
- [Specific outcome with target rate]

### 12.2 Quarterly case review

Every quarter, the protocol owner (named in §2) reviews:
- A random sample of [N] cases from this clinic
- All §7 referrals made
- Any patient-reported concerns or outcomes worse than expected

Review output: a 1-page report submitted to SKIDS clinical operations,
with any recommended protocol updates flagged for the next version.

### 12.3 Pediatrician certification on this protocol

To deliver this clinic, a SKIDS pediatrician must:
- Complete the protocol onboarding chapter (4 hours)
- Pass a structured case-vignette assessment (10 cases)
- Maintain a minimum case load of [N] per quarter
- Complete annual continuing education ([N] hours)

### 12.4 The SKIDS Fellowship pathway

[Where applicable: how a SKIDS pediatrician can advance from Tier 1
delivery of this protocol to Tier 2 credentialed subspecialty practice
(in Endocrine, Neurology, or Rheumatology). Reference the formal
fellowship pathway with partner institution. See
`docs/06-the-skids-fellowship.md`.]

---

## End of protocol

*This protocol governs the SKIDS [Service] Clinic. It is internal IP
of SKIDS Health Technologies. Last reviewed: YYYY-MM-DD by Dr. [Name],
[Credential]. Next review due: YYYY-MM-DD.*
