# Citation Conventions

Every clinical claim in a SKIDS protocol must cite at least one source.
This document defines the citation format, the approved evidence
hierarchy, and how citations aggregate in §2 Evidence base.

---

## Why citations matter here

The SKIDS Clinical Protocol Library is the institutional clinical brain
of SKIDS. Every parent-facing claim must trace back to a specific section
of a specific protocol, and every protocol claim must trace back to a
specific source. This chain is what makes the platform defensible —
medico-legally, ethically, and commercially.

The citation chain is also what allows the library to update
non-destructively. When AAP releases a revision, an editor opens
the cited section, follows the citation back to source, and updates
the protocol. Without citations this is impossible.

---

## Citation format

Citations use bracket tags inline and aggregate in §2 Evidence base.

### Inline format

```
[TAG]
```

A bracket tag appears at the end of the sentence containing the claim,
before the period. Multiple tags are comma-separated:

> Watchful waiting is acceptable for non-severe AOM in children
> ≥2 years [AAP-2013-AOM, IAP-TB-6E].

### Tag construction

```
[ORG-YEAR-TOPIC]      for guidelines and policy statements
[TEXT-EDITION]        for textbook references
[Cochrane-XXXXX]      for Cochrane reviews
[PMID:XXXXXXXX]       for individual papers via PubMed ID
```

### Approved organisation prefixes

| Prefix | Source |
|---|---|
| AAP | American Academy of Pediatrics |
| IAP | Indian Academy of Pediatrics |
| AAFP | American Academy of Family Physicians |
| AAO-HNS | American Academy of Otolaryngology – Head and Neck Surgery |
| AAD | American Academy of Dermatology |
| AAPD | American Academy of Pediatric Dentistry |
| NASPGHAN | North American Society for Pediatric Gastroenterology |
| GINA | Global Initiative for Asthma |
| CDC | Centers for Disease Control and Prevention (US) |
| ICMR | Indian Council of Medical Research |
| NTEP | National Tuberculosis Elimination Programme (India) |
| NHM | National Health Mission (India) |
| WHO | World Health Organization |
| ESPGHAN | European Society for Paediatric Gastroenterology |
| ERS | European Respiratory Society |

### Approved textbook tags

| Tag | Reference |
|---|---|
| `NELSON-21` | Nelson Textbook of Pediatrics, 21st edition (2019) |
| `NELSON-22` | Nelson Textbook of Pediatrics, 22nd edition (when available) |
| `IAP-TB-6E` | IAP Textbook of Pediatrics, 6th edition |
| `GHAI-9E` | Ghai Essential Pediatrics, 9th edition |
| `RUDOLPH-23` | Rudolph's Pediatrics, 23rd edition |

When citing a specific chapter or page, append `:CH##` or `:p###`:
```
[NELSON-21:CH421]    for chapter 421
[IAP-TB-6E:p845]     for page 845
```

### Examples of well-formed tags

```
[AAP-2013-AOM]       AAP Otitis Media Clinical Practice Guideline, 2013
[IAP-IIS-2024]       IAP Immunisation Schedule 2024-25
[GINA-2024]          GINA Asthma Management Strategy, 2024
[AAD-2014-AD]        AAD Atopic Dermatitis Guidelines, 2014
[NASPGHAN-2018-FC]   NASPGHAN Functional Constipation Guideline, 2018
[Cochrane-CD003266]  Cochrane Review on cromones in asthma
[PMID:31104364]      Specific PubMed paper
[NELSON-21:CH656]    Nelson 21st ed., chapter 656
[IAP-TB-6E:p412]     IAP Textbook 6th ed., page 412
```

---

## Evidence hierarchy

When sources conflict, follow this hierarchy:

```
TIER 1 — IAP guidelines and Indian-context policy
TIER 2 — AAP / WHO guidelines for general pediatric standards
TIER 3 — Subspecialty-society guidelines (NASPGHAN, GINA, AAD, etc.)
TIER 4 — Reference textbooks (Nelson, IAP Textbook, Ghai)
TIER 5 — Cochrane systematic reviews
TIER 6 — Individual high-quality RCTs and meta-analyses
```

For Indian-specific clinical context (vaccination, antimicrobial
resistance, prevalence patterns), Tier 1 always takes precedence.
For globally consistent science (drug pharmacokinetics, basic
pathophysiology), Tier 2 is acceptable.

When IAP and AAP genuinely diverge on a clinical recommendation, the
protocol must:
1. State which is followed and why
2. Cite both sources
3. Document the rationale in §2 Evidence base

---

## Aggregation in §2 Evidence base

Every protocol's §2 must include the full bibliography for every tag
used in the protocol body, in alphabetical order by tag:

```
**Cited evidence base:**

- [AAD-2014-AD] Eichenfield LF et al. Guidelines of care for the
  management of atopic dermatitis. Section 2: Management and treatment
  of atopic dermatitis with topical therapies. J Am Acad Dermatol.
  2014;71(1):116–132.

- [AAP-2013-AOM] Lieberthal AS et al. The diagnosis and management of
  acute otitis media. Pediatrics. 2013;131(3):e964–999.

- [IAP-IIS-2024] Indian Academy of Pediatrics. IAP Immunisation Schedule
  2024-25. IAP Publications, 2024.

- [NELSON-21] Kliegman RM et al, eds. Nelson Textbook of Pediatrics,
  21st ed. Elsevier, 2019.
```

---

## Citation density

Acceptable density is approximately one citation per 200–300 words of
clinical content. Variation by section is normal:

- §2 Evidence base: dense (every line is a citation)
- §3 Presenting concerns: light (descriptive content)
- §4 Diagnostic workflow: moderate (each named scale and threshold needs a tag)
- §5 Severity grading: dense (the threshold source must be named)
- §6 Therapeutic options: dense (every drug, dose, and duration needs a tag)
- §7 Hard referral triggers: moderate (each trigger needs supporting evidence)
- §8 Follow-up schedule: light to moderate
- §9–§12: minimal (these are operational, not clinical)

---

## What does not need a citation

- SKIDS-specific operational decisions ("we use Companion to log this")
- SKIDS-specific subscription or pricing references
- Cross-references to other SKIDS protocols (use the protocol_id instead)
- Routine clinical practice that is universally agreed (e.g., "take a
  history" does not need a citation; "use the BEARS questionnaire to
  screen for sleep problems in children 2–18 years" does)
- Ordinary descriptive prose that does not make a clinical claim

---

## What absolutely needs a citation

- Every drug, dose, route, frequency, and duration
- Every diagnostic threshold (Hb cutoff, BP percentile, severity score)
- Every named questionnaire/scale (with its citation for the cutoff)
- Every recommended duration of therapy
- Every referral trigger with a clinical justification
- Every age-specific or weight-specific decision rule

---

## Bibliography file

The shared bibliography lives at `shared/citations.bib` (Markdown
format, not BibTeX) and is updated whenever a new tag is introduced.
This is the canonical lookup. If a citation appears in a protocol
without an entry in `citations.bib`, editorial review fails.

The bibliography is alphabetical by tag and includes:
- Full citation
- DOI or PubMed link where available
- Last verified date

---

## Updating citations when guidelines update

When a governing guideline issues a revision:

1. Open `shared/citations.bib` and update the tag's full citation
   (if version-specific) or add a new tag for the new version
2. Search the protocol library for occurrences of the old tag
3. For each occurrence, decide: does the old recommendation still hold,
   or does the new guideline change the protocol?
4. Update affected protocols, increment their version numbers, and
   update their `last_updated` field in the YAML frontmatter
5. Log the change in the protocol's `STATUS.md`
6. Notify the protocol owner (named subspecialist) for sign-off

This is the maintenance loop that keeps the library current.
