# How to Review a Protocol

The editorial review checklist for a senior SKIDS pediatrician taking a
DRAFT_COMPLETE protocol toward APPROVED status.

---

## Who does editorial review

The protocol's named **protocol owner** (a credentialed subspecialist)
performs the editorial pass. For Tier 1 protocols, the protocol owner
is named in §2 of the draft. For SKIDS Bangalore at v1.0, this is
typically Dr. Satish Prasad Rath, with subspecialist consultants as
they are recruited.

The editorial pass takes 2–4 hours per protocol of focused work. Schedule
accordingly.

---

## Before you start

Read in this order:
1. The draft protocol (top to bottom, no skipping)
2. `SPECS.md` editorial review checklist (§6)
3. `docs/05-referral-trigger-discipline.md` (the §7 bar)
4. The protocol's STATUS.md, especially "open clinical questions"

---

## The structured review pass

Go through each section in order with this checklist.

### §1 Service definition

- [ ] Is the "what this clinic does" specific and clinically precise?
- [ ] Is the "what this clinic does not do" honest and complete?
- [ ] Is the age range correct for the conditions covered?
- [ ] Are the subscription tier mappings sensible?
- [ ] Is the SKIDS clinical tier (1/2/3) correctly assigned?

### §2 Evidence base

- [ ] Is every cited guideline current (within last 5 years where possible)?
- [ ] Is the IAP citation present where Indian context is relevant?
- [ ] Is the protocol owner named with a real credential?
- [ ] Are guideline departures (if any) explicitly flagged and justified?
- [ ] Does the bibliography in this section match every tag used in the body?

### §3 Presenting concerns

- [ ] Are 8–15 presenting concerns listed?
- [ ] Is each in both parent-language and clinical-language?
- [ ] Is the routing logic clean (this protocol vs. another)?
- [ ] Are the A1 screening flags that route here listed?

### §4 Diagnostic workflow

- [ ] Is the structured history specific (named questions)?
- [ ] Is the examination checklist specific (named findings, named techniques)?
- [ ] Are scales / questionnaires named with cutoffs and citations?
- [ ] Are in-clinic device tests specified by device?
- [ ] Are lab / imaging investigations gated by indication, not routine?
- [ ] Is the decision tree from findings → severity grade unambiguous?

### §5 Severity grading [SACRED — slow down]

- [ ] Is the named severity classification from the literature?
- [ ] Are thresholds numeric or named-criterion based, never adjectival?
- [ ] Does each severity grade map to an intervention tier?
- [ ] Does each severity grade map to a subscription tier?
- [ ] Is the threshold for §7 escalation explicit?
- [ ] Are re-grading criteria defined?

If §5 contains any of: "severe enough," "in clinical judgement,"
"as appropriate," "in some cases" — send back to author for rewrite.

### §6 Therapeutic options

- [ ] Are pediatric doses weight-based (mg/kg/day)?
- [ ] Is route, frequency, and duration specified for every drug?
- [ ] Are contraindications named explicitly?
- [ ] Is the dispensary stock list realistic for an Indian SKIDS clinic?
- [ ] Are behavioural / lifestyle protocols specific (named techniques)?
- [ ] Is "expected timeline to improvement" given for each tier?
- [ ] Are tapering / step-down rules defined?

### §7 Hard referral triggers [SACRED — slowest section to review]

- [ ] Is every trigger specific (numeric or named criterion)?
- [ ] Is every trigger time-bound (emergency / urgent / routine)?
- [ ] Does every trigger name the receiving clinician by role?
- [ ] Is the handoff packet specified?
- [ ] Would two different SKIDS pediatricians, given the same patient,
      make the same referral decision based on §7?
- [ ] Are there any vague adjectives ("severe," "complex," "refractory")
      that haven't been replaced with specific criteria?

If §7 fails any of these tests, the entire protocol fails review.
Send back for rewrite. Do not approve §7 by exception.

### §8 Follow-up schedule

- [ ] Is follow-up frequency defined per severity tier?
- [ ] Are "what to recheck" items specific findings, not "review progress"?
- [ ] Are treatment success criteria specific (numeric endpoints)?
- [ ] Are step-down and step-up criteria defined?
- [ ] Do step-out (§7 escalation) criteria match §7 exactly?

### §9 Companion software workflow

- [ ] Are screens specified with named, typed input fields?
- [ ] Are auto-calculation rules unambiguous?
- [ ] Is doctor override capability explicit (where applicable)?
- [ ] Are §7 hard referral triggers wired into 9.3 alerts?
- [ ] Are §10 parent communication elements wired into 9.4?
- [ ] Are §11 manager handoff fields specified in 9.3 / 9.4?
- [ ] Are edge cases handled (offline, missing data, override, §7 fire)?
- [ ] Is the spec implementable as written? (consult engineering if unsure)

### §10 Parent-facing communication

- [ ] Are scripted explanations in plain English (≤150 words for diagnosis)?
- [ ] Is the post-visit summary template parent-readable?
- [ ] Are activated parent.skids.clinic content modules named?
- [ ] Are cultural sensitivities (mental health stigma, dietary norms) addressed?

### §11 Manager handoff

- [ ] Are Manager Console fields specified?
- [ ] Is the subscription tier match rationale clear?
- [ ] Are top 5 parent objections + responses listed?
- [ ] Are digital and in-person enrolment scripts both present?
- [ ] Is the manager follow-up cadence defined?

### §12 Quality and audit

- [ ] Are outcome metrics specific (with target rates)?
- [ ] Is quarterly case review process defined?
- [ ] Are pediatrician certification requirements specific?
- [ ] Is the SKIDS Fellowship pathway referenced (where applicable)?

---

## Open clinical questions

The author will have flagged questions in STATUS.md "open clinical
questions for editorial review." Resolve each one with:

- A specific clinical answer (with citation), OR
- A SKIDS operational decision (with rationale recorded in §2 departures), OR
- A referral to Dr. Satish Prasad Rath for project-owner decision

Do not approve the protocol with unresolved questions.

---

## After review

If the protocol passes every check:

1. Update the YAML frontmatter `status` to `APPROVED`
2. Add your name and date to the frontmatter `editorial_reviewer` field
3. Update STATUS.md to `APPROVED`
4. Update `CLAUDE.md` §4 STATUS TRACKER to move this protocol from
   "v1.0 complete, awaiting editorial pass" to "v1.0 approved (in Companion)"
5. Notify SKIDS Engineering that the protocol is ready for Companion
   integration
6. Notify SKIDS Operations that the protocol is ready for derived
   manager assets

If the protocol fails one or more checks:

1. Update the YAML frontmatter `status` to `EDITORIAL_IN_PROGRESS`
2. Update STATUS.md with specific feedback per failed checklist item
3. Notify the author (or schedule a fresh authoring session) to address
   the feedback
4. Re-review when the revised draft returns

---

## On disagreements

You may sometimes disagree with the protocol author's clinical judgement
in places where the literature is ambiguous. The hierarchy:

1. If literature is unambiguous, follow the literature.
2. If literature is ambiguous and you have stronger clinical experience,
   your judgement governs.
3. If the disagreement is over a SKIDS-specific operational decision,
   escalate to Dr. Satish Prasad Rath.
4. Document the resolution in §2 departures so future authors and
   reviewers see the precedent.

The library improves over time precisely because these disagreements
get resolved on the record rather than absorbed silently.
