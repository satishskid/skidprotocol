# How to Resume a Stalled Protocol

The session-start checklist when you're picking up a protocol that was
left mid-draft.

---

## Why this workflow exists

Protocols are 6+ hours of focused authoring. They will not be written
in single sittings. Multiple Claude Code sessions, possibly weeks apart,
will contribute to the same protocol. Resuming cleanly — without
re-litigating decisions or losing voice consistency — is what makes the
multi-session model work.

---

## Step 1: Read the project memory

```
1. Read CLAUDE.md (the project memory file)
2. Read CLAUDE.md §4 STATUS TRACKER carefully — find the protocol marked
   "Drafting now"
3. Read CLAUDE.md §7 GOTCHAS — there may be new entries since the last
   session
```

If no protocol is currently marked "Drafting now," there is nothing to
resume — start a fresh protocol via `how-to-write-a-protocol.md`.

---

## Step 2: Read the protocol's STATUS.md

Open the relevant `protocols/B1-XX-name/STATUS.md`. The previous session
should have left:

- Which sections are complete
- Which section is in progress (and where stopped within it)
- Open clinical questions for the editorial reviewer
- Judgement calls the next session should re-check

If STATUS.md is empty or unclear, the previous session did not close
out properly. In that case, scan the protocol PROTOCOL.md and identify
where it stops mid-flow, then proceed.

---

## Step 3: Read the current PROTOCOL.md

Read the entire draft, top to bottom, slowly. Two purposes:

1. **Voice calibration.** Your draft must continue in the same voice.
   If you notice the previous session was using a particular phrasing
   pattern, match it.

2. **Internal consistency.** Earlier sections inform later ones. If
   §5 defines three severity tiers, §6 must have therapeutic plans for
   exactly those three. If you write §6 without re-reading §5, you'll
   introduce inconsistencies.

Look specifically for:
- The named severity scale used in §5
- The thresholds defined in §5
- The drug names and doses already in §6 (don't duplicate)
- The cited tags already used (be consistent in citation style)
- Any `[NEEDS EXPANSION IN EDITORIAL PASS]` markers — these are
  intentional flags to leave alone, not omissions to fix

---

## Step 4: Look at the most recently completed protocol

Voice anchors come from the most recently completed full protocol. As of
v0.1, this is `protocols/A1-skids-screening/PROTOCOL.md`. As more
protocols complete, the most recent one becomes the anchor.

Read at least one section of the anchor protocol to recalibrate voice
before continuing.

---

## Step 5: Resume

Pick up at the section where the previous session stopped. Use the
`<!-- STOPPED HERE: [date] [what's next] -->` marker if present.

Apply the same discipline as `how-to-write-a-protocol.md`:
- Stay in voice
- Cite at point of claim
- Slow down at §5 and §7
- Mark stubs honestly

---

## Step 6: At your own break

When you stop again — at a section boundary, ideally — close out the
session properly:

1. Save the in-progress file
2. Update or create the `<!-- STOPPED HERE -->` comment with current state
3. Update STATUS.md notes section
4. Update CLAUDE.md §4 STATUS TRACKER if status changed
5. Commit (if using git)

---

## When STATUS.md is missing or stale

Sometimes the previous session crashed or stopped abruptly without
updating STATUS.md. Recovery procedure:

1. Open PROTOCOL.md and find the last section with content
2. Identify the last complete sentence within that section
3. Anything beyond that is stale or empty — clean it up
4. Write a fresh STATUS.md noting:
   - Sections that are complete (you can tell because they end cleanly
     with no half-thoughts)
   - The section currently in progress (where the cleanup ended)
   - Best-guess open questions based on the content so far

This recovery should take 10–15 minutes. Do it before resuming
authoring; do not try to resume from a confused state.

---

## When you realise the previous session made a structural error

Sometimes you'll read a draft and realise the previous session
miscategorised the severity tiers, used the wrong scale, or applied a
non-current guideline. Three responses depending on severity:

**Minor inconsistency** (e.g., a citation tag is malformed): fix in
place and continue.

**Moderate problem** (e.g., a §6 dosing recommendation looks wrong):
flag in STATUS.md as a question for the editorial reviewer, leave the
existing content, and continue. The reviewer will resolve.

**Structural problem** (e.g., the wrong severity scale was used in §5
and now §6 doesn't match clinical literature): stop. Update STATUS.md
to flag the issue. Notify the project owner via STATUS.md notes. Do
not continue building on a broken foundation.

The cost of building on a broken foundation is much higher than the
cost of stopping and resolving the structural issue first.

---

## When in doubt, ask via STATUS.md

STATUS.md is the project's asynchronous communication channel. If
you're unsure about a clinical or operational decision, write the
question into STATUS.md "open clinical questions" rather than guessing.
The next session — or the editorial reviewer — will see it and
respond.

The library improves precisely because these uncertainties are
captured and resolved in writing rather than papered over silently.
