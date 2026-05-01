# Citation Verification Guide — For Editorial Review Team

**Scope:** All citations in `shared/citations.bib` and all `[NEEDS EXPANSION IN EDITORIAL PASS]` markers across 27 protocols
**Purpose:** Verify every citation against the actual published source before any protocol moves from DRAFT_COMPLETE to APPROVED

---

## How citations work in this library

Every clinical claim in a protocol ends with a bracket tag like `[AAP-BF-4E]` or `[IAP-IDA-2021]`. These tags resolve in `shared/citations.bib`, which is the master bibliography.

**The rule:** If a tag appears in any protocol, it must have an entry in `citations.bib`. If `citations.bib` says "Last verified: pending", the citation has NOT been checked against the actual publication. No protocol can reach APPROVED status until all its citations are verified.

---

## What needs to be verified

### Step 1: Verify each citation entry in citations.bib

For each entry in `shared/citations.bib` that says "Last verified: pending":

1. **Find the source.** Look up the publication on PubMed, the publisher's website, or the issuing organisation's site.
2. **Confirm the title** matches what's in the bib entry (some entries were drafted from memory and may have slight title variations).
3. **Confirm the year** matches the actual publication year (3 known errors flagged below).
4. **Confirm the authors** are correct (first author and "et al." is sufficient for the bib).
5. **Confirm the DOI or URL** if one is listed.
6. **Check for superseding versions.** If a newer version of the guideline exists (e.g., a 2024 update to a 2020 guideline), note it. The protocol author will decide whether to update the reference or note the newer version.
7. **Update "Last verified: pending"** to "Last verified: YYYY-MM-DD" with the date you verified it.

### Known citation errors to fix

| Citation key | Issue | What to check |
|---|---|---|
| `[AAP-LearningDisability-2014]` | Key says 2014; citation body says 2011 | Correct year is **2011** (Handler & Fierson, Pediatrics 2011). Fix the key to `[AAP-LearningDisability-2011]` and update all protocol references. |
| `[WHO-2024-Growth]` | Key says 2024; WHO Growth Standards published 2006 | Should be `[WHO-2006-Growth]` or clarified as "WHO Child Growth Standards (2006; current web version)". |
| `[ICCS-2014]` | 2014 cited; 2016 update exists | Austin PF et al., J Pediatr Urol 2016 is the current ICCS consensus. Update to `[ICCS-2016]` or add a note that the 2016 update is the governing version. |

---

### Step 2: Resolve [NEEDS EXPANSION IN EDITORIAL PASS] markers

There are **78 markers** across the 27 protocols. Each one looks like:

```
[NEEDS EXPANSION IN EDITORIAL PASS — confirm exact title and year]
```

For each marker:

1. **Read the context** around the marker to understand what needs expanding.
2. **Most markers are citation-verification requests** — "confirm exact title and year" for an IAP position statement. These are resolved by Step 1 above.
3. **Some markers are clinical-decision requests** — e.g., "confirm SKIDS network position on BCG stocking" or "confirm whether SKIDS clinics will stock FeNO devices." These require a decision from Dr. Satish Prasad Rath, not a literature lookup.
4. **Remove the marker** once the issue is resolved, or replace it with the verified content.

### How to find all markers

Run this command from the project root:

```bash
grep -rn "NEEDS EXPANSION" protocols/*/PROTOCOL.md
```

This outputs every marker with its file and line number.

---

### Step 3: Verify IAP position statements specifically

Many citations reference IAP position statements with estimated years (e.g., `[IAP-Obesity-2022]`, `[IAP-Hearing-2020]`, `[IAP-Speech-2019]`). These are the hardest to verify because:

- IAP publishes position statements through multiple chapters (Adolescent Health Academy, Allergy Chapter, Neurology Chapter, etc.)
- Some are published in Indian Pediatrics, some in IAP guidelines books, some on the IAP website only
- Exact titles vary between the chapter publication and the IAP compilation

**Recommended approach for IAP citations:**

1. Check the IAP website (iapindia.org) for the chapter's current position statements
2. Check Indian Pediatrics journal (indianpediatrics.net) for the published version
3. If the exact document cannot be found, contact the relevant IAP chapter convener
4. If the position statement does not exist as cited, the protocol author will either find the correct document or remove the citation and replace with the textbook reference (`[IAP-TB-6E]`)

### IAP citations requiring verification

| Citation key | Chapter | Estimated year | Protocol(s) using it |
|---|---|---|---|
| IAP-Adolescent-2023 | Adolescent Health Academy | 2023 | B1-13 |
| IAP-Allergy-2022 | Allergy and Applied Immunology | 2022 | B1-06 |
| IAP-Asthma-2021 | Pulmonology | 2021 | B1-14 |
| IAP-Atopic-2023 | Allergy | 2023 | B1-05 |
| IAP-Behaviour-2022 | DBP / Adolescent Health | 2022 | B1-08 |
| IAP-Cardiac-2020 | Cardiology | 2020 | B1-16 |
| IAP-Constipation-2020 | Gastroenterology | 2020 | B1-21 |
| IAP-Development-2020 | DBP | 2020 | B1-23 |
| IAP-Endocrine-2021 | Endocrinology | 2021 | B2-01 |
| IAP-Enuresis-2020 | Nephrology | 2020 | B1-20 |
| IAP-Epilepsy-2021 | Neurology | 2021 | B2-02 |
| IAP-GI-2021 | Gastroenterology | 2021 | B1-15 |
| IAP-Hearing-2020 | Otology | 2020 | B1-02 |
| IAP-Infections-2022 | Infectious Disease | 2022 | B1-19 |
| IAP-Learning-2020 | DBP | 2020 | B1-12 |
| IAP-Nephrology-2020 | Nephrology | 2020 | B1-17 |
| IAP-Obesity-2022 | Endocrinology / Nutrition | 2022 | B1-10 |
| IAP-OralHealth-2019 | Preventive Pediatrics | 2019 | B1-04 |
| IAP-RF-2008 | Cardiology | 2008 | B1-03 |
| IAP-Rheumatology-2020 | Rheumatology | 2020 | B2-03 |
| IAP-Sleep-2020 | Sleep Medicine | 2020 | B1-07 |
| IAP-Speech-2019 | DBP | 2019 | B1-11 |
| IAP-Thalassemia-2019 | Haematology | 2019 | B1-18 |
| IAP-Vision-2022 | Ophthalmology | 2022 | B1-01 |
| IAP-AEFI-2020 | Immunisation | 2020 | B1-22 |

---

## Output expected

For each citation entry in `citations.bib`:
- **Verified** (title, year, authors confirmed against source) — update "Last verified" date
- **Corrected** (title/year/key modified) — note what changed
- **Not found** (position statement does not exist as cited) — flag for protocol author

For each [NEEDS EXPANSION] marker:
- **Resolved** (content expanded or verified) — remove marker
- **Decision needed** (clinical/operational decision required from Dr. Rath) — escalate

Deliver as a marked-up copy of `citations.bib` with verification dates, plus a summary table of resolved/unresolved markers.
