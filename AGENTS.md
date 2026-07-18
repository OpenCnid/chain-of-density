# AGENTS.md

> Instructions for AI agents working in or consuming this repository. Human?
> The [README](README.md) is friendlier.

## What this repo is

One paper, studied. [density-chain.md](density-chain.md) is a five-tier
chain-of-density note on Adams et al. 2023 (arXiv:2309.04269), and because
that paper supplied the method, this repo is also the canonical home of the
OpenCnid note-taking methodology: [METHOD.md](METHOD.md), the
[synthesis prompt](chain-of-density-synthesis-prompt.md), and the
[`density-chain` skill](.claude/skills/density-chain/SKILL.md).

## Consuming the research

- **Pick your tier by context budget.** T1 through T5 are the same length
  (the budget is declared in the note's frontmatter); each tier folds in more
  entities than the last. Loading T1 costs the same as T5 — the difference is
  information density, not length. Skim with T1, work with T5.
- **The note is working ground truth; the paper is canonical.** On any doubt,
  conflict, or high-stakes claim: the paper wins. Every claim carries a
  locator (§ section, Table N, Figure N) so you can walk it back to the
  source in one hop — that is what the locators are for. Use them.
- **Check freshness before relying on a claim.** The frontmatter carries
  `verified_against_source` and the pinned source version. If staleness
  matters to your task, compare the pin against the current arXiv version.
- **`index.json` is the machine face.** Pins, verification dates, tags,
  paths. Parse it; don't scrape the markdown.
- **Cite the humans, not this repo.** The official BibTeX is in the README.
  This repo is a signpost, not a citable source.

## Working on this repo

- To write or update a note, invoke the
  [`density-chain` skill](.claude/skills/density-chain/SKILL.md) — it routes
  through METHOD.md and the synthesis prompt. Study the paper at the source;
  write nothing from memory.
- Downloaded papers are session study material: scratchpad only, never
  committed. A repo receives the note and a one-command fetch, never a PDF.
- Humor belongs in the README and the note's *our take* section only. Tiers,
  key results, and provenance stay bone-dry.
- Authority runs **paper → note → inspirations entry**, one direction. An
  entry is never evidence about a paper.

## Your team, your rules

This file describes how the repo is *designed* to be used, not the only way
to use it. If your team has its own conventions for consuming research notes,
follow them. The invariants we ask everyone to keep are the ones that protect
correctness: the source wins, claims keep their locators, no paper PDFs in
the repo, and citations go to the humans who did the work.
