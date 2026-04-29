# Companion Software Spec Format

§9 of every protocol is the engineering specification for the SKIDS
Companion Doctor Module. This document defines what §9 must contain,
how it should be written, and how it integrates with the parent app
and Manager Console.

---

## What §9 is

A protocol's §9 specifies, **screen by screen and field by field**, what
the Companion Doctor Module renders during a consult for this clinic.
It is a hard specification for the SKIDS engineering team — not a wish
list, not a sketch, not "engineering will figure it out."

The protocol author writes §9. The engineering team builds against §9.
If §9 is vague, the build will be wrong.

---

## Structure of §9

§9 has six standard subsections. Use exactly these subsection names.

### 9.1 Doctor Module screens

The screens the Doctor Module renders, in the order they appear during
a consult. Each screen has:
- A name
- The data fields it reads (from PHR or screening flag)
- The data fields it writes (mandatory vs. optional input)
- Auto-calculation rules (where applicable)
- Doctor override capability (where applicable)

### 9.2 Data logged to PHR

The structured data fields that get written to the child's longitudinal
PHR after the consult. Include field names, data types, and any
derived/calculated values.

### 9.3 Alerts

The triggers that fire alerts to the Manager Console, the parent app,
or referral partners. Each alert specifies: trigger, recipient, channel,
and content.

### 9.4 Parent app rendering

What the family sees in their parent.skids.clinic account after the
consult — the post-visit summary, the activated content modules, and
any follow-up reminders.

### 9.5 Auto-generated outputs

Anything the Doctor Module generates automatically when the doctor
completes the consult: prescription, dispensary order, follow-up
appointment, manager alert, parent summary.

### 9.6 Edge cases and overrides

What happens when:
- The doctor disagrees with the auto-calculated severity grade
- A required field is missing or unverifiable
- The §7 hard referral trigger fires mid-consult
- Network connectivity is lost (offline behaviour)

---

## Writing style for §9

Same voice rules as the rest of the protocol (see
`docs/01-voice-and-style-guide.md`), but with two additional constraints:

**Be data-precise.** Field types matter. Specify "integer 0–100" not
"a score." Specify "ISO 8601 date" not "the date." Specify "enum:
mild | moderate | severe" not "the severity level."

**Be screen-precise.** Where a screen layout matters clinically (e.g.,
the severity score must appear above the therapeutic plan, not below),
specify the layout. Where it doesn't matter, write the data fields and
let engineering design the screen.

---

## Standard data field conventions

Across all protocols, use these field-naming conventions:

```
child_id                  string, UUID         (PHR identifier)
visit_id                  string, UUID         (this consult)
visit_date                ISO 8601 datetime
clinic_id                 string               (which SKIDS clinic)
ped_id                    string               (which pediatrician)
protocol_id               string               (e.g., "B1-05-skin")

severity_grade            enum                 (mild | moderate | severe)
severity_score            integer or float     (the underlying scale value)
severity_scale_used       string               (e.g., "SCORAD")

intervention_tier         enum                 (light | standard | intensive)
subscription_tier         enum                 (basic | advanced | premium)

dispensary_items          array of objects     (each: sku, qty, dose)
prescription_items        array of objects     (each: drug, dose, freq, duration)
referral_fired            boolean
referral_destination      string               (named partner / subspecialist)
referral_urgency          enum                 (emergency | urgent | routine)

next_followup_date        ISO 8601 date
parent_summary_text       string               (the §10 scripted explanation)
manager_alert_payload     object               (the §11 handoff data)
```

Protocol-specific fields are added per protocol but should follow the
same naming style: `snake_case`, prefixed by domain where helpful.

---

## Worked example structure

Below is the skeleton of a well-formed §9 for a hypothetical protocol.
Use this as a reference when authoring.

```markdown
## §9 Companion software workflow

### 9.1 Doctor Module screens

**Screen 1: Pre-consult summary** (auto-loaded when doctor opens the visit)

Reads from PHR:
- child_id, child_age_months, child_sex
- last 3 visits (dates, presenting concerns, outcomes)
- active medications
- A1 screening flags (with thresholds)
- parent-logged observations since last visit (last 30 days)

Renders:
- Two-panel layout: timeline (left), today's presenting concern (right)
- Active flags highlighted
- Doctor's "open §4 history" button

Writes:
- visit_started_at: timestamp
- ped_id: from auth session

---

**Screen 2: Structured history (§4.1)**

Renders the §4.1 questions as a form.

Mandatory fields:
- onset_duration_weeks: integer, 0–520
- triggers_identified: array of enum
- previous_treatments_tried: array of objects

Optional fields:
- family_history_atopy: boolean
- school_attendance_impact: enum (none | partial | significant)

Doctor cannot proceed to Screen 3 until all mandatory fields filled.

---

**Screen 3: Examination findings (§4.2)**

[continues for each screen...]

---

**Screen 4: Severity calculation (§5)**

Auto-calculates severity_score using the named scale (e.g., SCORAD).
Renders the score with the underlying inputs visible.

Auto-determines severity_grade per §5 thresholds:
- score 0–19: mild
- score 20–49: moderate
- score 50+: severe

Doctor override:
- Doctor may override severity_grade with a documented reason.
- Override reason is mandatory if used.
- Override is logged with ped_id and timestamp for §12 audit.

---

**Screen 5: Therapeutic plan (§6)**

Auto-pre-fills the §6 tier matched to severity_grade.

Renders editable fields for:
- prescription_items (pre-filled from §6.X tier)
- dispensary_items (pre-filled from §6.X tier)
- behavioural_instructions (pre-filled from §6.X tier)

Doctor approves or modifies. On approval:
- Auto-generates prescription PDF
- Auto-generates dispensary order to clinic stock
- Auto-generates parent summary text per §10
- Fires manager_alert if subscription enrolment indicated

---

**Screen 6: Follow-up scheduling (§8)**

Auto-suggests next_followup_date per §8.1.
Doctor confirms or modifies.

Writes:
- next_followup_date
- followup_actions (what to recheck)

---

### 9.2 Data logged to PHR

Each consult writes to the child's PHR:

| Field | Type | Source |
|---|---|---|
| visit_id | UUID | auto |
| protocol_id | string | "B1-XX-name" |
| severity_score | float | calculated |
| severity_grade | enum | calculated, doctor-overrideable |
| intervention_tier | enum | matched to severity_grade |
| dispensary_items | array | doctor-approved §6 |
| prescription_items | array | doctor-approved §6 |
| referral_fired | boolean | from §7 logic |
| ped_notes | string | optional free-text |

These fields become queryable for §12 quarterly audit.

---

### 9.3 Alerts

| Trigger | Recipient | Channel | Payload |
|---|---|---|---|
| §7 emergency referral fires | manager + ped_supervisor + receiving clinician | Companion + WhatsApp + SMS | child_id, ped_id, trigger fired, urgency=emergency |
| §7 urgent referral fires | manager + receiving clinician | Companion + WhatsApp | same, urgency=urgent |
| New subscription enrolment opportunity | manager | Companion only | child_id, recommended_tier, parent_contact |
| Follow-up missed (24h overdue) | manager + parent | WhatsApp to parent | child_id, missed_date, reschedule_link |

---

### 9.4 Parent app rendering

After this consult, the family's parent.skids.clinic account shows:

- Post-visit summary (auto-filled from §10.3 template)
- Activated Learn articles (per §10.4)
- Activated Grow body-system pages (per §10.4)
- Activated Practice habit programme (per §10.4)
- Next follow-up date with reminder set
- Subscription enrolment CTA (if not yet subscribed and §11.2 indicates)

---

### 9.5 Auto-generated outputs

On consult completion, the Doctor Module generates:

1. Prescription PDF (printable + digital, signed by ped)
2. Dispensary pick-list (sent to clinic stock module)
3. Parent summary (delivered to parent app + WhatsApp)
4. Manager alert (if §11 indicates enrolment opportunity)
5. Referral packet (if §7 fired) — includes severity_score, history,
   exam findings, treatments tried, current regimen
6. Follow-up appointment (auto-scheduled per §8.1)

---

### 9.6 Edge cases and overrides

**Doctor disagrees with auto-calculated severity_grade:**
Doctor uses override with mandatory reason. Override is logged and
flagged for §12 quarterly review.

**Required §4 field unverifiable:**
Doctor marks the field "unable to assess" with reason. The severity
calculation flags this and may downgrade confidence in the grade.
If the grade is downgraded to "uncertain," the protocol routes to
§7 hard referral as a precaution.

**§7 trigger fires mid-consult:**
Doctor Module immediately surfaces the §7.4 handoff communication
template and pauses the §6 therapeutic plan flow. Referral takes
precedence; the doctor can resume §6 only after acknowledging the
referral has been initiated.

**Offline behaviour:**
Doctor Module supports offline consults with local-only data. On
reconnection, data syncs to PHR, alerts fire, prescriptions and
dispensary orders queue. If an emergency §7.1 trigger fires offline,
the Doctor Module displays a hard-stop instructing the doctor to
make the referral by phone immediately.
```

---

## What §9 should NOT contain

- Visual design specifications (colour, typography, layout — engineering
  decides these from a design system, not from the protocol)
- Technology choices (React vs. native, REST vs. GraphQL — engineering
  chooses)
- Authentication / authorisation flows (handled cross-protocol)
- Logging / observability beyond what serves §12 audit
- Tests (engineering writes tests against the spec)

---

## Review checklist for §9

A §9 passes editorial review only if:

- [ ] Every screen has named, typed input fields
- [ ] Every screen has named, typed output fields
- [ ] Auto-calculation rules are unambiguous
- [ ] Override capabilities are explicit
- [ ] All §7 hard referral triggers from this protocol are wired into 9.3 alerts
- [ ] All §10 parent communication elements are wired into 9.4
- [ ] All §11 manager handoff payload is specified in 9.3 / 9.4
- [ ] Edge cases include doctor override, missing fields, §7 fire, offline
- [ ] Engineering team has reviewed and confirmed implementability
