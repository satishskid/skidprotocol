# Setting up GSD for the SKIDS Protocol Library

GSD (Get Shit Done) is a context-engineering and spec-driven workflow
harness for Claude Code. It solves exactly the multi-session, long-
context, resumable-work problem that the SKIDS protocol library
requires.

This document explains why we use GSD, how to install it, and how its
commands map onto SKIDS protocol authoring.

---

## Why GSD for this project

Writing 27 textbook-grade protocols across 15+ focused sessions is the
exact work GSD was built for. Specifically:

- **Persistent state.** GSD's `.planning/` directory holds milestone,
  phase, and progress state across sessions. A fresh Claude Code session
  reads it and instantly knows where work stands.
- **Phase discipline.** GSD's `/gsd-discuss-phase` → `/gsd-plan-phase`
  → `/gsd-execute-phase` loop forces explicit scope-locking before
  work, which prevents the "drift mid-protocol" failure mode.
- **Quality gates.** GSD has built-in scope-reduction detection (the
  planner silently dropping requirements), schema-drift detection, and
  context-window-aware prompt thinning.
- **Forensics.** When something goes wrong, `/gsd-forensics` produces
  a diagnostic report — much better than re-reading entire transcripts
  to figure out what happened.

GSD is open source, MIT licensed, maintained by TÂCHES, and at v1.35+
(as of April 2026) has stable Claude Code skills-based integration.

---

## Installation

### Pre-requisites

- Claude Code 2.1.88+ installed and working
- Node.js + npm (for the installer)
- A local copy of this protocol library directory

### Install GSD globally

```bash
npx get-shit-done-cc --claude --global
```

This installs GSD to `~/.claude/skills/gsd-*/SKILL.md` (the modern
skills location). Older Claude Code versions install to
`~/.claude/commands/gsd/`. The installer handles both formats
automatically.

Verify install:

```bash
ls ~/.claude/skills/ | grep gsd
```

You should see `gsd-discuss`, `gsd-plan`, `gsd-execute`, `gsd-progress`
and other gsd-* directories.

### Initialise GSD for the protocol library

From inside the protocol library directory:

```bash
cd ~/path/to/skids-protocol-library
```

Open Claude Code in this directory, then in Claude Code:

```
/gsd-new-project
```

This creates the `.planning/` directory with milestone and phase
structure, anchored to the protocol library project.

### First-time configuration

In Claude Code, run:

```
/gsd-set-profile balanced
```

The "balanced" profile is appropriate for SKIDS protocol authoring.
Use "quality" if you want maximum thoroughness (slower, more tokens).
Use "budget" if iterating cheaply on bootstrap structure.

---

## Daily workflow

### Starting a new session

```
1. Open Claude Code in the skids-protocol-library/ directory
2. Run: /gsd-progress
   (GSD reads .planning/ state and tells you exactly where work stands)
3. GSD recommends the next action
```

That's it. No re-briefing. No context loss. The .planning/ files
persist between sessions; GSD reads them and orients Claude Code.

### Authoring a new protocol

```
1. /gsd-discuss-phase
   GSD asks adaptive questions about the next protocol to scope it
   (e.g., "which subspecialty? which severity scale? which IAP/AAP
   guidelines govern?")
2. /gsd-plan-phase
   GSD writes an explicit plan with 2-3 max tasks per phase
3. /gsd-execute-phase
   GSD runs the plan with quality gates active
4. At natural break, run: /gsd-progress
   This checkpoints state before stopping
```

### Stopping mid-work

GSD persists state automatically. Just close Claude Code. Next session
starts with `/gsd-progress` and resumes cleanly.

### When something goes wrong

```
/gsd-forensics
```

Produces a diagnostic report in `.planning/forensics/` showing what
failed, why, and recommended remediation steps.

### Capturing learnings

After completing a phase (typically a single protocol):

```
/gsd-extract-learnings
```

This captures patterns that worked well into project-local skills.
Useful for converging on voice and structure across protocols.

---

## Integration with our project structure

GSD's `.planning/` directory is added to `.gitignore` — it's
session-local state, not source content.

The `.gsd-conventions.md` file in the project root tells Claude Code
how GSD phases map to SKIDS protocol work (see that file).

The `protocols/_index.md` master tracker is the source of truth for
"what's done, what's next." GSD's `.planning/` directory is the
session-local working state. They serve different purposes; both are
valuable.

---

## When NOT to use GSD

GSD adds workflow ceremony. For small tasks (fixing a typo, adding a
single citation, updating a STATUS.md), GSD is overkill — just edit
directly.

GSD is right for:
- Authoring a new protocol from scratch
- Major revisions to existing protocols
- Editorial review of a complete draft
- Generating a manager-asset derivative

GSD is wrong for:
- Single-line edits
- Citation additions
- Status updates

Use judgement. The friction of `/gsd-discuss-phase` for a one-line fix
is much higher than its value.

---

## Updating GSD

GSD evolves fast. Update periodically:

```bash
npx get-shit-done-cc --claude --global
```

The installer detects existing installs and upgrades in place.

---

## If you don't want to use GSD

GSD is recommended but not required. The protocol library can be
authored and reviewed without it — just follow the workflows in
`workflows/` and use STATUS.md files for between-session state.

The trade-off is that you do the orientation work manually each
session (read CLAUDE.md, read STATUS.md, calibrate voice, identify
next action) instead of running `/gsd-progress` and getting it for
free.

For a 17-session project, GSD pays back its setup cost within the
first 3 sessions. Recommended.
