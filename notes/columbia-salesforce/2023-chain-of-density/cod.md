---
title: "From Sparse to Dense: GPT-4 Summarization with Chain of Density Prompting"
authors: "Griffin Adams, Alexander Fabbri, Faisal Ladhak, Eric Lehman, Noémie Elhadad"
venue: "New Frontiers in Summarization Workshop (NewSum), 2023"
source: "https://arxiv.org/abs/2309.04269 (pinned: arXiv:2309.04269v1, 2023-09-08)"
license: "arXiv.org perpetual non-exclusive license 1.0"
date_summarized: 2026-07-17
verified_against_source: 2026-07-17
tier_budget_words: 150
tags: [summarization, prompting, chain-of-density, evaluation, gpt-4]
entity_ledger:
  - "Chain of Density (CoD) prompting — T1 — Abstract, §2"
  - "GPT-4 as the summarizer — T1 — Abstract"
  - "fixed-length densification; informativeness–readability tradeoff — T1 — §4, §6"
  - "five steps, 1–3 entities per step, ~70-word budget — T2 — §2, Fig. 2"
  - "missing-entity criteria (relevant, specific ≤5 words, novel, faithful, anywhere) — T2 — §2"
  - "CNN/DailyMail test set, 100 random articles — T2 — §2"
  - "entity density trajectory 0.089→0.167; vanilla 0.122; human 0.151 — T3 — Tab. 1"
  - "abstractiveness ↑, fusion ↑, lead bias ↓ across steps — T3 — §4, Fig. 3"
  - "human study: 4 author-annotators, median step 3, mode step 2 (30.8%), EV 3.06, 61% first places ≥3, Fleiss' κ 0.112 — T4 — §4"
  - "GPT-4 five-dimension self-assessment; overall peak step 4 (4.76) — T4 — §4"
  - "released data: 500 annotated + 5,000 unannotated summaries, HuggingFace — T5 — Abstract, §1"
  - "scope limits: news-only, GPT-4-only, low agreement — T5 — §4–6"
---

# T1 — Sparse

Chain of Density (CoD) is a prompting recipe that makes GPT-4 summaries denser
on purpose. Instead of asking for one summary, the prompt asks the model to
write a deliberately entity-sparse first draft, then rewrite it several times,
each rewrite absorbing a few more salient facts from the article while the
length stays fixed [Abstract; §2]. Because the budget never grows, every
addition forces compression elsewhere — the summaries become more abstractive
and more fused rather than simply longer [§4]. The authors ran the procedure on
news articles and asked people which rewrite they actually preferred. The
answer sits in the middle of the chain: readers wanted summaries denser than
what a vanilla GPT-4 prompt produces, and almost as dense as human-written
references, but disliked the densest steps, where added facts crowd out
readability [Abstract; §4]. The paper's lasting contribution is naming that
tradeoff — informativeness against readability — and giving it a dial [§6].

# T2

Chain of Density makes GPT-4 summaries denser by construction. A single prompt
asks for an entity-sparse first draft of a news article, then four more
rewrites — five steps total — each folding in one to three "missing entities"
while holding the summary near a fixed ~70-word budget matched to the
vanilla-prompt baseline [§2, Fig. 2]. A missing entity must be relevant to the
main story, specific yet concise (five words or fewer), novel to the previous
summary, faithful to the article, and locatable anywhere in it [§2]. Run over
100 randomly sampled CNN/DailyMail test articles, the procedure yields 500
summaries whose density climbs step by step [§2]. Fixed length is the engine:
each addition forces compression, so summaries grow more abstractive and fused
rather than longer [§4]. Human preferences land mid-chain — denser than vanilla
GPT-4, near human density, short of the unreadable end [Abstract; §4].

# T3

Chain of Density prompts GPT-4 for an entity-sparse draft of a news article,
then four rewrites — five steps — each fusing in one to three missing entities
(relevant, specific in five words or fewer, novel, faithful, anywhere in the
article) at a fixed ~70-word budget [§2, Fig. 2]. Across 100 random
CNN/DailyMail test articles, measured entity density climbs from 0.089 entities
per token at step one to 0.167 at step five, crossing vanilla GPT-4 (0.122)
around step two and human references (0.151) around step four [Tab. 1]. The
fixed budget is the engine: additions force compression, so summaries become
more abstractive, exhibit more fusion, and shed the lead bias typical of news
summarizers — trends the paper shows graphically rather than numerically
[§4, Fig. 3]. Preferences land mid-chain: denser than vanilla, near human
density, short of the crowded end [Abstract; §4].

# T4

Chain of Density prompts GPT-4 through five fixed-length (~70-word) rewrites of
a news summary, each fusing in one to three missing entities — relevant,
specific (≤5 words), novel, faithful, anywhere in the article [§2, Fig. 2].
Over 100 CNN/DailyMail articles, density climbs from 0.089 to 0.167 entities
per token, passing vanilla GPT-4 (0.122) and human references (0.151) on the
way [Tab. 1]; summaries grow more abstractive and fused, with less lead bias
[§4, Fig. 3]. Four annotators — the paper's first four authors — picked
favorites: the median preferred step was three (mode: step two, at 30.8%;
expected value 3.06), 61% of first-place votes went to step three or later, and
agreement was low (Fleiss' κ = 0.112) [§4]. GPT-4 self-assessment on five
dimensions — informative, quality, coherence, attributable, overall — peaked at
step four overall (4.76), with quality and coherence declining after steps two
and one respectively [§4].

# T5 — Dense

Chain of Density prompts GPT-4 through five fixed-length (~70-word) rewrites,
each fusing one to three missing entities — relevant, specific (≤5 words),
novel, faithful, anywhere in the article — into a news summary [§2, Fig. 2]. On
100 CNN/DailyMail test articles, entity density rises from 0.089 to 0.167
entities per token, crossing vanilla GPT-4 (0.122) and human references (0.151)
[Tab. 1], while abstractiveness and fusion climb and lead bias falls
[§4, Fig. 3]. Four author-annotators preferred mid-chain summaries — median
step three, mode step two (30.8%), 61% of first places at step three or later,
Fleiss' κ = 0.112 — and GPT-4's five-dimension self-scores peaked overall at
step four (4.76), with quality and coherence declining after steps two and one
[§4]. The authors released 500 annotated plus 5,000 unannotated summaries on
HuggingFace [Abstract; §1]. Scope limits: one domain (news), one model (GPT-4),
low annotator agreement — "aim near human density" is a finding about this
setting, not a universal constant [§4–6].

# Key results

| Claim or metric | Exact value | Locator |
|---|---|---|
| Densification procedure | 5 steps; 1–3 entities per step; ~70-word fixed budget | §2, Fig. 2 |
| Corpus | 100 randomly sampled CNN/DailyMail test articles | §2 |
| Entity density, CoD steps 1→5 | 0.089 → 0.129 → 0.148 → 0.158 → 0.167 entities/token | Tab. 1 |
| Entity density, vanilla GPT-4 | 0.122 entities/token | Tab. 1 |
| Entity density, human references | 0.151 entities/token | Tab. 1 |
| Human-preferred step | median 3; mode 2 (30.8%); expected value 3.06 | §4 |
| First-place votes at step ≥ 3 | 61% | §4 |
| Inter-annotator agreement | Fleiss' κ = 0.112 (4 annotators: first four authors) | §4 |
| GPT-4 "overall" self-score peak | step 4, at 4.76 / 5 | §4 |
| Released data | 500 annotated + 5,000 unannotated summaries (HuggingFace) | Abstract; §1 |

# Our take

This is the paper our whole note format comes from, and it shaped this repo's
design end to end. Three of its findings became three of our rules. The preference for
mid-chain density (median step three, not five) is why we keep *every* tier
instead of shipping only the densest — the best summary is provably not the
most compressed one. The low inter-annotator agreement (κ = 0.112) reads to us
as a feature, not a flaw: density preference is personal, so the honest move is
to hand the reader the whole chain and let them pick their tier. And the
fixed-length constraint — the unglamorous mechanical trick at the paper's
core — turned out to be the whole engine: without it, "add more detail" just
makes summaries longer, never denser. We adapted rather than adopted: our tiers
run ~150 words instead of ~70, our "entities" include ablations and
limitations, and we select final candidates by audit rubric rather than by
step count, because later work (see README references) found the dial behaves
differently outside news. Gratitude, specifically: this paper gave our
note-taking a spine.

# Provenance

- Canonical source: https://arxiv.org/abs/2309.04269
- Published version: https://aclanthology.org/2023.newsum-1.7/
- Version read: arXiv:2309.04269v1 (submitted 2023-09-08; v1 is the latest as
  of verification)
- Released data: https://huggingface.co/datasets/griffin/chain_of_density
- Verified against source: 2026-07-17, via the ar5iv rendering of v1; section,
  table, and figure numbering follows that rendering
- Revisions or errata noticed since: none
