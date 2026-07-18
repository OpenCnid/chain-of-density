# Chain-of-Density Research Notes — Methodology

This collection recognizes the research that inspires our work. We do not store or
redistribute papers. Instead, each paper gets an original synthesis written in our own
words using **Chain of Density (CoD)** summarization, with a citation back to the source
at every level of the chain. The originals remain canonical; this collection is our
working ground truth for day-to-day reference.

## The method, and its own citation

Chain of Density is itself published research, so we cite it the same way we cite
everything else here:

> Griffin Adams, Alex Fabbri, Faisal Ladhak, Eric Lehman, Noémie Elhadad.
> *From Sparse to Dense: GPT-4 Summarization with Chain of Density Prompting.*
> New Frontiers in Summarization Workshop, 2023. arXiv:2309.04269.
> https://arxiv.org/abs/2309.04269 · https://aclanthology.org/2023.newsum-1.7/

The core move: write an entity-sparse summary first, then iteratively rewrite it,
fusing in 1–3 missing salient entities per round **without increasing length**. Their
human evaluations found readers prefer summaries denser than a vanilla prompt produces
and almost as dense as human-written ones — and that density past that point trades
informativeness against readability. That is why we keep **all tiers**, not just the
densest one: the chain is the artifact.

## Adaptation for research papers

CoD was designed for news articles at ~70 words. Papers need three adjustments:

1. **Tier length is fixed per document** (declare a budget in the note's frontmatter
   and hold it constant across tiers — the constant-length constraint is what forces
   fusion; ~150–200 words is the usual range).
2. **"Entity" is broadened** to the units that matter in research: methods, models,
   datasets, benchmarks, metrics with exact values, ablations, limitations, and the
   authors' own framing of their contribution.
3. **Every entity enters the chain with a locator** — a pointer to where it lives in
   the source (§ section, Table N, Figure N). A claim without a locator doesn't go in.

For the full authoring pipeline — evidence extraction before densification, map/reduce
for long sources, audit-rubric candidate selection — see
[chain-of-density-synthesis-prompt.md](chain-of-density-synthesis-prompt.md).

## Authoring rules

- **Own words, always.** Original synthesis only. At most one short attributed quote
  per document (under 15 words, in quotation marks). Never copy figures, tables,
  or passages.
- **Exact numbers, located.** Quantitative claims use the source's exact values with a
  locator. Never round, never estimate, never fill in a number from memory.
- **Pin the version.** Record the arXiv version (vN) or publication date you actually
  studied. Papers get revised; a note is only ground truth relative to a pinned version.
- **Commentary is quarantined.** Our appreciation and opinions live in *Our take*,
  clearly ours, never blended into the tiers.
- **Verification date.** Record when the note was last checked against the source.
  If the source has moved on (new version, errata, retraction), the note says so.

## Layout

Each paper gets its own repository, named after the paper it studies so the
research community can find it. Inside:

```
density-chain.md    the five-tier note
index.json          source pin + verification metadata
README.md           what the paper is and what our note is, in one screen
AGENTS.md           how AI agents consume and maintain the note
```

The methodology itself — this file and the synthesis prompt — lives canonically
in [chain-of-density](https://github.com/OpenCnid/chain-of-density) and is
linked from other paper repos, not copied into them.

This methodology is also packaged as a runnable Claude Code skill —
`.claude/skills/density-chain/` in this repo — so a paper repo can be produced
end to end by saying *"add a note for \<paper\>"*.

## Document template

Each `density-chain.md` follows this frame. Bracketed names are generation instructions, not
literal text; `...` slots repeat the pattern established around them.

```markdown
---
title: "{Exact_Paper_Title_As_Published}"
authors: "{Author_List_As_Published}"
venue: "{Venue_Or_Preprint_Server_With_Year}"
source: "{Canonical_Link_With_Pinned_Version}"
license: "{License_Stated_By_Source_Or_Unknown}"
date_summarized: {ISO_Date}
verified_against_source: {ISO_Date}
tier_budget_words: {Fixed_Word_Budget_Held_Constant_Across_Tiers}
tags: [{Topic_Tags}]
entity_ledger:
  - "{Entity} — T{Tier_Introduced} — {Locator}"
  - ...
---

# T1 — Sparse

{Fixed_Length_Overview_Of_Problem_Approach_And_Headline_Result_In_Our_Own_Words_With_Locators}

# T2

{Same_Length_Rewrite_Fusing_In_Two_To_Three_New_Salient_Entities_Each_With_A_Locator}

# T3

...

# T4

...

# T5 — Dense

{Same_Length_Maximally_Fused_Rewrite_That_Stays_Readable_With_Every_Claim_Traceable}

# Key results

| Claim or metric | Exact value | Locator |
|---|---|---|
| {Result_As_Stated_By_Source} | {Exact_Value} | {Section_Table_Or_Figure} |
| ... | ... | ... |

# Our take

{Our_Commentary_And_Appreciation_Clearly_Ours_Never_Presented_As_The_Papers_Claims}

# Provenance

- Canonical source: {Link}
- Version studied: {Version_Identifier_And_Date}
- Revisions or errata noticed since: {Notes_Or_None}
```

## Ground-truth policy

The collection is our working ground truth: when our repos need a research fact, we
cite our note, and the note carries the locator back to the primary source. If a note
and its source ever disagree, **the source wins** and the note gets fixed. That
ordering is what makes it safe to treat the collection as ground truth at all.
