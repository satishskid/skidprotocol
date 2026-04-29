# Future Tools

External tools bookmarked for use at specific later stages of the
SKIDS protocol library project. Not active now. Install when their
trigger condition is met.

---

## Frontend Slides — for SKIDS Manager marketing assets

**Tool:** zarazhangrui/frontend-slides
**Repo:** https://github.com/zarazhangrui/frontend-slides
**What it does:** Creates beautiful, distinctive HTML slide decks from
markdown content. Curated styles (12+ presets) avoid generic AI-slop
aesthetics. Single-file output, no build tools required. Includes
PowerPoint conversion support.

### When to install

Once any 5+ Tier 1 protocols are at APPROVED status, the manager-asset
derivative work begins. This is the Layer 2B work referenced in
project planning — turning each protocol's §11 (Manager handoff) into:

- Social media post sets per channel (Instagram, WhatsApp Business,
  Facebook, LinkedIn)
- In-clinic posters for each specialty clinic
- Marketing decks for school-relationship outreach
- Investor and recruitment decks
- Training decks for new SKIDS managers

Frontend Slides is the right tool for the deck-style outputs in
this list.

### Install

```bash
git clone https://github.com/zarazhangrui/frontend-slides.git ~/.claude/skills/frontend-slides
```

Then in Claude Code, `/frontend-slides` becomes available. Point it at
the protocol's §10 and §11 content, plus the relevant SKIDS brand
tokens (terracotta accent, editorial layout — see
`docs/01-voice-and-style-guide.md` for the parent.skids.clinic register).

### Outputs to expect

Per protocol:
- A 10–15 slide manager training deck
- A 5-slide investor / recruitment one-pager
- A 3-slide in-clinic explainer poster set
- A social-media kit (3–5 image cards per channel)

### Integration with the library

The Frontend Slides outputs are stored in
`derived/manager-playbook/B1-XX-name/` once that derivative directory
is created. The protocol library itself stays unchanged; the slides
are derived assets.

---

## Graphify — for cross-protocol knowledge graph

**Tool:** safishamsi/graphify
**Repo:** https://github.com/safishamsi/graphify
**What it does:** Multi-modal knowledge graph builder. Reads code, docs,
papers, images, even video transcripts. Uses Tree-sitter for code
analysis and Claude subagents for semantic extraction. Outputs an
interactive HTML graph plus a queryable JSON.

### When to install

Once the protocol library reaches 10+ APPROVED protocols, run Graphify
over the entire `protocols/` and `docs/` and `shared/` directories. The
output will surface:

- **Cross-protocol relationships** — which protocols share dispensary
  stock, which share referral partners, which share screening flags
- **God nodes** — concepts that show up in multiple protocols and
  may deserve their own shared/ document
- **Surprising connections** — protocol overlaps the human authors
  may have missed (e.g., obesity-sleep apnoea-adolescent metabolic
  syndrome cluster)
- **Suggested questions** — queries the graph is uniquely positioned
  to answer

### Why this matters

The protocol library is the institutional clinical brain of SKIDS.
A knowledge graph over that brain becomes the foundation for:

- The SKIDS Companion AI assistant's cross-protocol reasoning
- The SKIDS Fellowship's curriculum planning (which protocols form
  natural groupings for subspecialty learning paths)
- The investor demonstration of clinical depth (a queryable graph
  of 26 protocols × dozens of conditions × hundreds of decision rules
  is a meaningfully different artifact from a folder of markdown files)
- Audit trails for protocol governance (which protocol claims trace
  back to which guideline citations)

### Install (when ready)

```bash
uv tool install graphifyy
graphify install
# Then in the protocol library directory:
/graphify .
```

The graph output goes to `graphify-out/` which should be added to
`.gitignore` since it can be regenerated.

### Integration with Companion

The graph.json output can feed the Companion software's clinical-AI
backend, allowing the Doctor Module to surface cross-protocol context
("this child's allergy presentation overlaps with the asthma protocol's
GINA stepwise approach — see also...").

This is a v2 integration, after the library is mature.

---

## How to know when these are ready to install

Check `CLAUDE.md` §4 STATUS TRACKER. The triggers are:

- **Frontend Slides:** install when ≥5 protocols are APPROVED and
  manager-asset derivative work begins
- **Graphify:** install when ≥10 protocols are APPROVED and the
  cross-protocol graph would be meaningful

Both are bookmarks, not blockers. The protocol library can complete
without them. They are amplifiers for downstream work.

---

## Tools considered and not adopted

For the record, these were reviewed and explicitly skipped for this
project:

- **Everything Claude Code (affaan-m/everything-claude-code)** — meta-
  skill for general software engineering. Too broad, not protocol-
  specific. GSD covers our actual workflow needs.
- **Awesome Design.md (VoltAgent/awesome-design-md)** — design system
  references for UI generation. Not relevant to clinical text authoring.
- **UI/UX Pro Max (nextlevelbuilder/ui-ux-pro-max-skill)** — same
  category as above. Not applicable to protocol library work.

These may become relevant for parent.skids.clinic web-surface design
or the SKIDS Manager Console UI work, both of which are separate
projects.
