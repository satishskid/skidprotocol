# How to Write a Protocol

The session-start checklist for authoring a new SKIDS clinical protocol.

---

## Before you start

Read these in order:
1. `CLAUDE.md` — the project memory file
2. `SPECS.md` — the editorial specification
3. `docs/01-voice-and-style-guide.md` — the voice
4. `docs/02-citation-conventions.md` — citation format
5. `docs/05-referral-trigger-discipline.md` — the §7 bar
6. The most recently completed protocol — current voice anchor (start
   with `protocols/A1-skids-screening/PROTOCOL.md` until others are done)

If you skip any of the above, the protocol you write will need to be
rewritten. The reading is cheap. Do it.

---

## Decide which protocol to write

Open `CLAUDE.md` §4 STATUS TRACKER and §5 NEXT WORK ITEM. Confirm
which protocol is recommended next. If no recommendation is current,
the priority order is:

```
A1 SKIDS Screening (front door, do first)
B1-05 Skin (highest commercial signal, first B1)
B1-01 Vision · B1-09 Nutrition · B1-08 Behavioural · B1-06 Allergy
B1-07 Sleep · B1-02 Hearing · B1-03 Throat · B1-04 Oral Health
[remaining B1 protocols in any order]
B2-01, B2-02, B2-03 (last — these need credentialed-subspecialist input)
```

---

## Set up the protocol directory

```bash
cd protocols/
mkdir -p B1-XX-name           # e.g., B1-05-skin
cp ../docs/00-protocol-template.md B1-XX-name/PROTOCOL.md
```

Create the STATUS.md:

```markdown
# Status: B1-XX [Service Name]

**Current state:** IN_PROGRESS
**Author:** Claude (AI first draft)
**Date started:** YYYY-MM-DD
**Estimated completion:** [Y sections done of 12]

## Notes for the next session
[If you stop mid-protocol, leave clear notes here on where you stopped
and what's next.]

## Open clinical questions for editorial review
[Mark any spots where you made a judgement call the senior reviewer
should specifically check.]
```

---

## Write the sections in order

The 12 sections are deliberately sequenced. Earlier sections inform
later ones. Skipping ahead introduces inconsistency.

### Suggested time per section

| Section | Estimated time |
|---|---|
| §1 Service definition | 15 min |
| §2 Evidence base | 30 min (most of this is finding citations) |
| §3 Presenting concerns | 30 min |
| §4 Diagnostic workflow | 60 min (longest section) |
| §5 Severity grading | 30 min (sacred, slow down) |
| §6 Therapeutic options | 60 min (with dosing tables) |
| §7 Hard referral triggers | 30 min (sacred, slow down) |
| §8 Follow-up schedule | 20 min |
| §9 Companion software workflow | 45 min |
| §10 Parent-facing communication | 30 min |
| §11 Manager handoff | 30 min |
| §12 Quality and audit | 15 min |

Total: ~6 hours of focused authoring per protocol.

This will rarely fit in one session. Plan to break at natural section
boundaries (after §4, after §7) and resume in the next session.

---

## Discipline at sacred sections

When you reach §5 and §7, slow down deliberately. Re-read
`docs/05-referral-trigger-discipline.md` before writing.

For §5:
- Use a named scale from the literature where possible
- Define numeric or categorical thresholds for every tier
- Map every threshold to an intervention tier and subscription tier
- Define re-grading criteria after intervention

For §7:
- Each trigger must be specific (numeric or named criterion)
- Each trigger must be time-bound (emergency / urgent / routine)
- Each trigger must name the receiving clinician by role
- Specify the handoff packet that auto-fires

If you can't write a §5 threshold or a §7 trigger with confidence,
mark it `[NEEDS EXPANSION IN EDITORIAL PASS]` and flag the question
in `STATUS.md`. Do not pad these sections to look complete.

---

## Citation discipline as you write

Open `shared/citations.bib` in a second window. Every clinical claim
gets a tag at the end of the sentence. If you use a tag that's not
yet in `citations.bib`, add the full citation there immediately —
do not defer it.

Citation density target: roughly one tag per 200–300 words of clinical
content. Sparser usually means under-cited claims; denser usually means
citation-padding without specificity.

---

## Cross-protocol references

If this protocol overlaps with another (e.g., Allergy with
Pulmonology/Asthma, Behavioural with Adolescent), reference the other
protocol explicitly:

> Children meeting GINA step 4 criteria are managed by this protocol
> in coordination with B1-14 Pulmonology / Asthma.

Use the `B1-XX-name` protocol_id for cross-references; do not duplicate
content between protocols. The cross-reference tells the reader where
to look.

---

## When you finish a section

Save the file. If using GSD, run `/gsd-progress` to log progress. Update
the STATUS.md "estimated completion" line. Take a break if needed.

When you finish all 12 sections:

1. Re-read the entire protocol top to bottom for voice consistency
2. Check every `[NEEDS EXPANSION]` marker — either expand or confirm
   it's intentionally flagged for the editorial reviewer
3. Update the YAML frontmatter `status` field to `DRAFT_COMPLETE`
4. Update STATUS.md to `DRAFT_COMPLETE`
5. Update `CLAUDE.md` §4 STATUS TRACKER to move this protocol from
   "Drafting now" to "v1.0 complete, awaiting editorial pass"
6. Commit (if using git): `git commit -m "B1-XX: draft complete"`

---

## When you stop mid-protocol

This will happen. Plan for it.

1. Mark the section you stopped in: leave a comment
   `<!-- STOPPED HERE: [date] [what's next] -->`
2. Update STATUS.md notes section with:
   - Which sections are complete
   - Which section is in progress (and where within it)
   - Any open clinical questions you need to resolve
   - Any judgement calls the next session should re-check
3. If using GSD, run `/gsd-progress` to checkpoint state

The next session — possibly a different Claude Code instance, possibly
weeks later — should be able to resume from STATUS.md and the in-line
comment with no information loss.

---

## When the protocol is genuinely difficult

If you find yourself stuck on a clinical question — say, the precise
threshold for SCORAD-driven escalation in a SKIDS context — you have
three options:

1. **Mark and move on.** Add `[NEEDS EXPANSION IN EDITORIAL PASS]`,
   note the specific question in STATUS.md, and continue with the rest
   of the protocol. The senior reviewer will resolve the question.

2. **Research it.** Check the cited guidelines, the textbook references,
   and recent Cochrane reviews. If the literature gives a clean answer,
   write it with citation.

3. **Ask the project owner.** Some questions require Dr. Satish Prasad
   Rath's specific clinical or operational decision. STATUS.md is the
   right place to record these so they get answered before editorial
   pass.

Do not invent thresholds. Do not paper over uncertainty. The library's
defensibility depends on every clinical claim being either cited or
flagged.
