# Batch-run handoff prompt

Paste everything inside the fence as the first message of a session, then
replace `${Repo_URLs}` with the repo list. Bracketed names are generation
instructions, not literal text.

```xml
<request type="Batch_Density_Chain_Run">

  <context>
    Lab: OpenCnid Labs (github.com/OpenCnid) — research recognition through careful attribution.
    Canonical methodology: github.com/OpenCnid/chain-of-density (METHOD.md + synthesis prompt + AGENTS.md; local clone at D:\chain-of-density).
    Hub: github.com/OpenCnid/llm-research-inspirations (entries require receipts; no receipt, no entry).
    Exemplar paper repo: github.com/OpenCnid/pcf-adaptive-agents — the naming convention (searchable handle) and findability convention (description + topics) in the flesh.
  </context>

  <instruction>
    Act as the OpenCnid research-notes maintainer.
    1. Load the toolkit first, via the Skill tool, in this order — before any other work:
       - `prompt-engineering` — the structural authoring protocol
       - `hypershot-protocol` — contamination-free templates and frames
       - `density-chain` — the operational pipeline; its batch mode governs this run
    2. Process every repo in [Repo_URLs] — one repo to completion at a time (verify → write → audit → commit), never several half-finished.
    3. For each repo: locate the source link in its README.md (arXiv, ACL Anthology, DOI, or lab article — the skill routes both shapes); fetch the source into the session scratchpad and study it there; write {Locator_Verified_Five_Tier_Note_As_density-chain.md}; add or update index.json and AGENTS.md; bring the README to house style while preserving the owner's existing prose (restructure, don't delete); set the repo description and GitHub topics per the skill's findability step.
    4. Commit per repo with a descriptive message and push — pushing these repos is authorized for this run.
    5. Add an llm-research-inspirations entry only where a {Concrete_Receipt_Commit_Design_Doc_Or_Shipped_Feature} exists.
  </instruction>

  <constraints>
    *** CRITICAL ***
    - Downloaded sources are session study material: they live in the scratchpad and stay there. A repo receives the note plus a straight-from-the-source fetch link — never the PDF.
    - Exact numbers with locators, studied at the source during this session — or nothing. Pin the exact version studied (arXiv vN, or publication date + URL for articles) and record the verification date.
    - When a source involves Matthew Murphy (github.com/gusthemole — Lexideck curriculum, PCF, SPARK), attribute him with a link and lead with the lab-connection disclosure; the friendship never moves the one-way rule.
    - Pause and ask (rather than guess) when: a README has no findable source link, or a repo already contains a committed paper PDF.
    - Humor lives in READMEs and "our take" only. Tiers, key results, and provenance stay bone-dry.
  </constraints>

  <output_instructions>
    Format: one line-item per repo — {Repo_Link} · {Source_And_Pinned_Version} · {What_Changed} · {Anything_Paused_And_Why} — then a one-paragraph batch summary.
    Audience: Darian, catching up after being away; lead with the outcome.
  </output_instructions>

</request>

Repos for this run:
${Repo_URLs}
```
