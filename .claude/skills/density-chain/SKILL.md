---
name: density-chain
description: Write an OpenCnid five-tier chain-of-density note for a research paper, or scaffold a complete new paper repo around one. Use whenever the user asks to add, summarize, note, recognize, or "make a repo for" a research paper (arXiv, ACL Anthology, a lab blog post — any published research), mentions a density chain, CoD note, tier note, paper note, or the OpenCnid paper-repo collection — even if they never name this skill. Also use when updating, re-verifying, or extending an existing OpenCnid paper repo.
---

# density-chain

Produce OpenCnid's house artifact: a five-tier chain-of-density note on a research
paper, verified against the source, living in a repo named after the paper.

## Why the rules are shaped this way

Three findings from the method's own paper (Adams et al. 2023, arXiv:2309.04269)
drive everything below, so keep them in mind rather than following steps blindly:

- **Fixed length is the engine.** Without a held word budget, "add detail" makes
  a summary longer, never denser. Every tier must be rewritten *at the same
  length*, not appended to.
- **The best tier is not the densest.** Human preference peaked mid-chain
  (median step 3), and annotators barely agreed with each other (Fleiss'
  κ = 0.112). That is why we ship all five tiers and let the reader pick —
  never just T5.
- **The collection is only ground truth because the source always wins.** Pin
  the exact version read, record the verification date, and if note and paper
  ever disagree, fix the note. Authority runs paper → note → inspirations
  entry, one direction only.

## Read the framework first

Read these two documents before writing anything; they are the canonical spec
and this file is only the field guide:

1. `METHOD.md` — the rules that don't bend, plus the document template
   (frontmatter, tiers, entity ledger, key results, our take, provenance).
2. `chain-of-density-synthesis-prompt.md` — the full authoring framework:
   evidence-unit extraction, map/reduce for long papers, the audit rubric that
   selects candidates (never "densest wins").

Where to find them, in order of preference: the repo root if you are inside the
chain-of-density repo; the local clone at `D:\chain-of-density\`; or raw from
GitHub at
`https://raw.githubusercontent.com/OpenCnid/chain-of-density/main/METHOD.md`
(same pattern for the synthesis prompt).

## The pipeline

1. **Fetch and verify — never write from memory.** Pull the paper via its
   ar5iv/arXiv HTML rendering and the arXiv abs page (for license, version
   number, and date). Every number, every author affiliation, every claim gets
   read from the source in this session, with a locator (§ section, Table N,
   Figure N). A quantity you "remember" is a quantity you don't write.
2. **Write the note as `density-chain.md`.** Follow METHOD.md's template
   exactly: pinned frontmatter, a declared tier word budget held constant,
   T1–T5, entity ledger with tier-introduced + locator per entity, a key
   results table of exact values, *our take* quarantined at the bottom, and a
   provenance section noting which rendering the locators follow.
3. **Index it.** Add or update `index.json` (schema: see the chain-of-density
   repo's copy). Trellis consumes these; a note without an index entry is
   invisible to the staleness machinery.
4. **New paper? New repo, named after the paper.** Kebab-case the name the
   research community actually uses (`chain-of-density`,
   `lost-in-the-middle`) — discoverability is the point; someone searching for
   the paper should find our reading of it. Scaffold: `density-chain.md`,
   `index.json`, `README.md`, `LICENSE.md` (CC BY 4.0 for prose), and a
   *link* to chain-of-density for METHOD.md and the synthesis prompt — never a
   copy (one canonical home, no drift).
5. **README in house style.** Use the chain-of-density repo's README as the
   living template. The required furniture: a theme-neutral animated SVG banner
   (mid-tone palette #58a6ff→#9b8cf7→#ef6fd0, mono type), shields badges
   including joke badges that state real guarantees, the one-way-rule alert, a
   "standing on the shoulders of giants" section naming the authors with
   affiliations *as printed on the paper*, a "want the PDF? one command,
   straight from the source" section (curl from arXiv — we never host papers),
   a "cite the humans, not us" section carrying the official BibTeX (fetch it
   from the ACL Anthology `.bib` endpoint or arXiv — never hand-roll a
   citation), honest notes including the human+AI co-authorship disclosure,
   references, and a footer joke. Voice: high-level, fun, educational; wry
   parentheticals, no marketing.
6. **Humor placement.** READMEs and *our take* only. The tiers, the key
   results, and the provenance stay bone-dry — they are the ground truth, and
   jokes in ground truth age like milk.
7. **Inspirations entry — only with a receipt.** If the paper demonstrably
   shaped OpenCnid work (a commit, design doc, or shipped feature you can
   link), add an entry to
   [llm-research-inspirations](https://github.com/OpenCnid/llm-research-inspirations)
   in its entry-format frame. No receipt, no entry — admiration is free;
   entries are earned.

## Non-negotiables

- Own words, always. At most one short attributed quote (<15 words) per note;
  never a figure, table, or passage; never commit a paper PDF.
- Exact numbers with locators, or nothing.
- Pin the source version and record the verification date.
- Authority runs paper → note → entry. Never backwards.
