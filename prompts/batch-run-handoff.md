# Batch-run handoff prompt

Paste everything inside the fence as the first message of a session, then
replace `${Repo_URLs}` with the repo list. Bracketed names are generation
instructions, not literal text.

```xml
<request type="Batch_Density_Chain_Run">

  <context>
    Lab: OpenCnid Labs (github.com/OpenCnid) — research recognition through careful attribution.
    Canonical methodology: github.com/OpenCnid/chain-of-density (METHOD.md + synthesis prompt; local clone at D:\chain-of-density).
    Hub: github.com/OpenCnid/llm-research-inspirations (entries require receipts; no receipt, no entry).
    Harness: the `density-chain` skill is installed at user level and inside the chain-of-density repo. It documents the full pipeline, including batch mode. Trust the skill over improvisation.
  </context>

  <task>
    Act as the OpenCnid research-notes maintainer.
    1. Invoke the `density-chain` skill and follow its batch mode.
    2. Process every repo in [Repo_URLs] — one repo to completion at a time (verify → write → audit → commit), never several half-finished.
    3. For each repo: locate the paper link in its README.md; download the paper into the session scratchpad and read it there; write {Locator_Verified_Five_Tier_Note_As_density-chain.md}; add or update index.json; bring the README to house style while preserving the owner's existing prose (restructure, don't delete).
    4. Commit per repo with a descriptive message and push — pushing these repos is authorized for this run.
    5. Add an llm-research-inspirations entry only where a {Concrete_Receipt_Commit_Design_Doc_Or_Shipped_Feature} exists.
  </task>

  <constraints>
    *** CRITICAL ***
    - Downloaded papers are session working material: they live in the scratchpad and stay there. A repo receives the note plus the one-command fetch section — never the PDF.
    - Exact numbers with locators, read from the source during this session — or nothing. Pin the exact version read and record the verification date.
    - Pause and ask (rather than guess) when: a README has no findable paper link, or a repo already contains a committed paper PDF.
    - Load the prompt-engineering and hypershot-protocol skills before authoring README furniture, templates, or any artifact that primes future generation.
    - Humor lives in READMEs and "our take" only. Tiers, key results, and provenance stay bone-dry.
  </constraints>

  <output_instructions>
    Format: one line-item per repo — {Repo_Link} · {Paper_And_Pinned_Version} · {What_Changed} · {Anything_Paused_And_Why} — then a one-paragraph batch summary.
    Audience: Darian, catching up after being away; lead with the outcome.
  </output_instructions>

</request>

Repos for this run:
${Repo_URLs}
```
