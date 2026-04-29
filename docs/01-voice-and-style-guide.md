# Voice and Style Guide

The voice of the SKIDS Clinical Protocol Library is **a senior pediatrician
writing for a junior pediatrician.** Not an institutional document. Not a
marketing brochure. A specific person at the top of their craft, talking
to a specific person early in theirs.

Hold this voice through every protocol. The rest of this guide is operational
detail that flows from this single principle.

---

## What this voice does

Respects the reader's intelligence. Junior pediatricians are competent
clinicians who completed a difficult residency. They do not need
hand-holding, encouragement, or motivational language. They need clear,
specific guidance.

Saves the reader's time. Every sentence does work. Padding (transitions,
restatements, framing language) is removed in editing. If a paragraph
can be a bullet list, make it a bullet list. If a sentence can be five
words instead of fifteen, make it five.

Prefers decisions to discussions. "Use amoxicillin 50 mg/kg/day in three
divided doses for five days" is the right register. "Antibiotic therapy
may be considered in some cases depending on severity" is the wrong
register. The reader is asking what to do, not what to think about.

Specific over general, always. Numbers, not "some." Named drugs, not
"appropriate medication." Defined thresholds, not "as clinically
indicated." If the literature is genuinely uncertain, say so explicitly
and provide the SKIDS-specific operational rule.

---

## What this voice does not do

Does not market. No "world-class," "comprehensive," "holistic," "innovative."
Protocols are internal IP, not customer-facing copy. The clinical truth
sells itself if it is true.

Does not pad. No "It is important to note that..." (just say the thing).
No "It should be remembered that..." (the reader remembers if you say it
once). No "In conclusion..." sections.

Does not over-hedge. Hedging is appropriate where the literature genuinely
disagrees ("evidence is mixed; we recommend X based on Y rationale") and
inappropriate where the literature is clear ("most authorities suggest..."
when AAP and IAP both unambiguously recommend the thing).

Does not exclaim. No exclamation marks anywhere. The seriousness of
pediatric medicine carries the weight; punctuation does not need to.

Does not preach. No paragraphs explaining why pediatrics matters or why
the protocol exists. The reader is a pediatrician. They know.

Does not first-person plural casually. "We" is reserved for SKIDS-specific
choices ("at SKIDS we use SCORAD over POEM because..."). Generic medical
"we" should be replaced by passive or imperative voice.

---

## Sentence-level rules

**Active voice for clinical instructions.**

> Examine the tympanic membrane with pneumatic otoscopy.

Not:

> The tympanic membrane should be examined using pneumatic otoscopy.

**Imperative mood for protocol steps.**

> Order ferritin if Hb is below the WHO age-specific threshold.

Not:

> Ferritin testing may be ordered when haemoglobin levels are below
> normal thresholds.

**Numbers, ranges, and thresholds, never adjectives.**

Yes:
> SCORAD ≥40 with intolerance to topical therapy after 4 weeks.

No:
> Severe eczema not responding adequately to standard therapy.

**Drug doses by weight, always with route and frequency.**

Yes:
> Amoxicillin 50 mg/kg/day PO in 3 divided doses × 5 days.

No:
> Amoxicillin at standard pediatric doses.

**Cite at the point of claim.**

Yes:
> Watchful waiting is acceptable for non-severe AOM in children
> ≥2 years [AAP-2013-AOM].

No:
> AAP recommends watchful waiting in some cases.

---

## Paragraph-level rules

**One idea per paragraph.** If a paragraph contains two ideas, split it.

**Lead with the action.** If the paragraph tells the reader what to do,
the action goes in the first sentence. Background and rationale follow.

**End on the decision.** If the paragraph builds toward a clinical
choice, the choice is the last sentence. Do not append qualifying
language after the decision.

**Lists where lists belong.** Sequential steps, parallel options, and
checklists are lists. Do not write them as prose.

---

## Structural rules

**Sections in the locked order** defined in `SPECS.md`. Twelve sections,
named exactly as specified. No additions. No omissions.

**Headings are descriptive, not clever.** "§5 Severity grading" is the
right register. "§5 The art of knowing how bad it is" is wrong.

**Tables for any structured data with three or more parallel rows.**
Drug dosing tables, severity grading tables, referral trigger checklists
all belong in tables.

**Code blocks for decision trees, scripts, and templates.** Anything
the engineering team needs to render verbatim sits in a code block.

**Bracket tags for citations.** Every clinical claim ends with at least
one bracket tag (`[IAP-IIS-2024]`, `[AAP-2013-AOM]`, etc.). Tags
aggregate in §2 Evidence base.

---

## Indian context

The SKIDS pediatrician practises in India. Protocols are written for that
context. This means:

**Antimicrobial stewardship.** Indian community-acquired resistance
patterns differ from US/EU. Where AAP and IAP guidelines diverge on
antibiotic choice, follow IAP unless explicitly justified.

**Cost-conscious investigations.** Indian families often pay out of
pocket. If a test costs ₹3,000 and rarely changes management, do not
order it routinely. Where the literature supports a less-expensive
substitute, name the substitute.

**Cultural framing.** Mental health stigma, generational dietary
norms, school-vs-home dynamics, gender roles in adolescent care —
these are real clinical variables. Address them in §10 Parent-facing
communication when relevant. Do not pretend the patient lives in a
context-free environment.

**Vaccination schedule.** IAP IIS, not CDC. Where the schedules differ
(e.g., influenza, HPV timing), follow IAP.

**Drug availability.** Some drugs commonly used in US/EU pediatrics are
not licensed or readily available in India. Where this is the case,
use the available substitute and flag the difference.

---

## Examples

### Example 1 — clinical instruction

**Wrong (marketing register):**
> Our comprehensive approach to pediatric eczema delivers world-class
> outcomes through evidence-based topical therapy customized for each
> child's unique needs.

**Wrong (over-hedged):**
> Topical corticosteroids are generally considered to be one of the
> options that may be beneficial in many cases of pediatric atopic
> dermatitis, depending on severity and other clinical factors.

**Right:**
> Apply mid-potency topical corticosteroid (mometasone 0.1% cream)
> once daily to active eczema for 7–14 days. Step down to emollient-only
> maintenance once flares clear. Reassess at 4 weeks [AAD-2014-AD].

### Example 2 — referral trigger

**Wrong (vague):**
> Refer to a specialist if the child is not improving with standard care.

**Right:**
> Refer to pediatric dermatology within 4 weeks if SCORAD remains ≥40
> after a documented trial of mid-potency topical steroid + daily
> emollient + trigger avoidance. Send the dermatologist the SCORAD
> trajectory, photos, and current regimen [AAD-2014-AD].

### Example 3 — parent communication

**Wrong (jargon dump):**
> Your child has atopic dermatitis with secondary bacterial colonisation
> requiring topical corticosteroid therapy and emollient maintenance.

**Wrong (over-soft):**
> So your little one's skin is being a bit cranky right now! Don't worry,
> this is super common and we'll get it sorted in no time!

**Right:**
> Aanya has eczema. Her skin barrier doesn't hold moisture well, which
> makes it itchy and red. We are going to do two things: a small amount
> of medicated cream once a day for two weeks to calm the active
> patches, and a daily moisturiser to rebuild her skin barrier so flares
> get less frequent. We'll see her back in four weeks. Most children at
> this stage are noticeably better by then.

---

## When in doubt

Read the most recently completed protocol (currently A1 SKIDS Screening,
soon to include B1-05 Skin) as a voice anchor. If your draft sounds
different, recalibrate before continuing.

If a section feels under-developed, mark it
`[NEEDS EXPANSION IN EDITORIAL PASS]` and move on. Honest stubs are
preferable to dishonest padding.

If a clinical claim feels uncertain, cite the source you would use to
defend it in front of a medical council. If you cannot name that source,
the claim is not ready for the protocol.
