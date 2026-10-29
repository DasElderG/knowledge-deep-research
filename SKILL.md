---
name: knowledge-deep-research
description: "Use when asked for broad or deep research, a literature or course survey, due diligence, a study package, or evidence for a decision. Reuses saved research, fills explicit gaps, examines mechanisms and comparisons, and delivers traceable findings with reusable source-content cards. Not for a single lookup (firecrawl-search), locating existing knowledge alone (knowledge-search), course-outline design (outcome-first-course-design), or establishing current internal state (systemops-establish-ground-truth)."
user-invocable: true
argument-hint: '<question> [intended use, scope, existing research, constraints]'
allowed-tools: Bash, Read, Write, Edit, Grep, Glob, Agent
---

# Broad and Deep Research

## Goal

Answer the requested question at the needed depth, with reusable content and evidence whose scope, limits, and provenance remain visible.

## Acceptance criteria

- **Question coverage:** read the coverage table in `research-plan.md` against the request. Every required question has a finding and source locator, or an explicit gap with its consequence. The deliverable matches the selected mode below.
- **Useful depth:** apply the relevant extraction and evidence tests in [research-design.md](references/research-design.md). A list of titles or repeated conclusions cannot substitute for the mechanism, method, conditions, or comparison the question needs.
- **Traceability:** follow each material factual claim in `report.md` through `source_index.md` to its content card and saved evidence. Quotes, numbers, definitions, and implementation claims have exact locators; reading scope follows the [card contract](references/source-content-card.md).
- **Parent verification:** read `fact_check.md`. The parent has personally compared load-bearing claims and disputed passages with saved original evidence, recorded supported/partial/contradicted/unverified verdicts, and repaired overclaims. Unsupported claims are attributed or left open.
- **Consistency:** inspect affected summaries, tables, visuals, cards, and conclusions after a correction. They agree with the latest evidenced correction or explicitly preserve a disagreement.
- **Closure:** read `search_manifest.md` for actual source coverage, acquisition errors, worker IDs, output paths, and terminal lane states. Follow the owning runtime's lifecycle rules; no worker is silently left running at delivery.

## Modes and boundaries

Infer the mode from the request and existing decisions; ask only for a missing fact that would materially change the work.

| Mode | Deliver |
|---|---|
| Survey or source comparison | The actual definitions, frameworks, teaching sequences, methods, overlaps, disagreements, and gaps. When requested, show original structures visually before proposing a synthesis. |
| Learning or preparation | A coherent explanation of concepts and mechanisms, concrete examples, conditions, competing explanations, and evidence needed to understand the topic. |
| Decision support | A comparison against explicit criteria and plausible alternatives, a calibrated judgment when requested, and the evidence that would change it. |

Keep requested comparison separate from proposed recommendations. Use `outcome-first-course-design` for educational sequencing and approved learning outcomes; research supplies evidence rather than silently redesigning a course. Independent chapter authoring follows a content framework and is a separate stage from evidence acquisition.

Use existing project/task research locations. This skill does not create a second research home, alter task lifecycle, publish, send messages, train models, or execute the product being studied. Follow standing authorization and budgets; this skill adds no approval or goal gate.

For external acquisition, use Firecrawl or Tavily as needed. For Firecrawl authentication preflight, commands, and error handling, use the installed `firecrawl` router. Its installed sibling is `../firecrawl/SKILL.md`; its source owner is `workspace/firecrawl/SKILL.md` relative to the skill repository root. Use `firecrawl-research-index` for paper discovery and citation expansion and `firecrawl-developer-index` for implementation documentation when relevant. Internal live state routes to `systemops-establish-ground-truth`. Delegation and model choice follow global AGENTS.md; substantial units use its required transport.

## Working method

**Frame and retrieve.** Read the request, prior decisions, supplied materials, and existing research index. Use `knowledge-search` or scoped file search to find reusable content; a search miss may be an indexing gap. Establish the question, intended use, hard conditions, definitions, and what evidence would answer each part. Start `research-plan.md` with that coverage map and the missing evidence, not a predetermined thesis or source quota.

**Reuse before acquisition.** Navigate from content cards and digests to detailed notes, prior audits, then the necessary passages in saved originals. Notes locate evidence; notes alone do not verify it. Carry forward an existing documented verification when the claim, source version, conditions and relevant freshness remain applicable; record it as reused, not newly performed. Reopen the decisive passage for a new, changed, disputed or insufficiently supported claim. Refresh or fetch when content is missing, its reading scope is insufficient, the relevant fact may have changed, a version matters, or a contradiction cannot be resolved locally. Log the reason and version rather than re-reading or re-fetching the whole collection by default.

**Broaden and deepen to answer gaps.** Choose research lanes by missing questions, source access, or evidence type; choose overlap only for an actual contested claim. Follow strong anchors to references, citers, rival methods, implementation records, and disconfirming cases as needed. Prefer a targeted original passage over repeated general searches. Depth means explaining how a result arises and where it applies; breadth means covering relevant alternatives and perspectives. Neither is measured by worker, article, or search counts. Load [research-design.md](references/research-design.md) when designing lanes or extracting a course, product, experiment, or theory.

**Preserve substantive evidence.** Maintain source-content cards using the [single card contract](references/source-content-card.md). Save new captures once and link existing originals in place. Distinguish observed facts, attributed claims, inference, and proposed synthesis. Evaluate evidence for each claim using the rubric in `research-design.md`; publisher category alone never decides truth. Workers return specific findings, locators, caveats, unresolved questions, and their actual reading scope.

**Integrate and challenge.** The parent reconciles definitions and versions, combines evidence by question, and checks the load-bearing source passages personally. Agreement among workers citing the same underlying source adds no independent corroboration. Investigate a material contradiction at its exact point; preserve unresolved disputes. For a proposed judgment, test its weakest premise, strongest alternative, and disconfirming evidence. Update affected artifacts before writing the final answer.

**Deliver at the requested level.** Lead with the requested findings or judgment and a visual structure when it helps comparison. Preserve enough content for later reuse, with inline underlying-source citations, limits, and remaining gaps. A research handoff to course design includes evidence and candidate explanations; a full chapter outline or final classroom sequence remains with the course-design skill. External-facing prose follows the standing authorship rule and its owning writing skill.

## Output contract

Reuse the owning package's equivalent files and names rather than creating duplicate ledgers. For a new multi-source package, the default is `<task_dir>/research/<slug>-YYYYMMDD/`; use a session scratchpad only when no task owns the work. The following records may be sections of one small report:

| Record | Required content |
|---|---|
| `research-plan.md` | Question, use, mode, conditions, question-to-evidence coverage, reuse inventory, gaps, proposed research scope and explicit budget if supplied. |
| `source_index.md` and content cards | Stable source identities linked to substantive cards, local saved evidence, and acquisition provider. Use the card contract; retain a machine-readable ledger if the package already has one. |
| `fact_check.md` | Claim, proposed wording, source and exact passage/table/code locator, verdict with reason, parent inspection, and correction or open consequence. |
| `search_manifest.md` | Actual corpus/search coverage and limits, dated acquisitions/preflight receipts or reuse-only state, lane ownership and outputs, terminal status, and errors. |
| `report.md` | Requested explanation/comparison/judgment, supporting evidence, conditions, disagreements, limits, and gaps; a recommendation only in scope. |

A complete hypothetical package appears in [research-design.md](references/research-design.md#worked-example). No schema requires re-quoting full articles; short necessary excerpts and original locators suffice.

## Degraded cases

| Condition | Response |
|---|---|
| No question, intended use, or usable context | State the missing decision-changing input and ask one focused question; do not launch broad research against an invented objective. |
| No matching local material | Record actual scope and index coverage; use scoped file discovery before concluding there is a research gap. |
| Original unavailable or only abstract/catalog accessible | Record the accessible scope and failed acquisition. Keep unsupported details open; do not upgrade a title, summary, or file's existence into full reading. |
| Material is stale or versions conflict | Bind claims to the evidenced date/version, refresh the affected fact when allowed, and retain the earlier record and any unresolved difference. |
| Tool or worker fails | Record its safe raw error type/status/message and attempted scope, following the owning tool's fallback policy. Continue independent useful work and deliver the consequence of the gap. An execution failure is not a negative finding. |
| Budget ends before coverage is complete | Deliver checked findings and the exact remaining gaps; do not label the survey comprehensive or the unresolved claim verified. |

## Observed failure modes

- Repeated original acquisition during revisions wasted time because prior reading had not been consolidated into reusable content. Use the reuse path and card contract.
- Research built from general advice and product claims lacked direct implementation and comparison evidence. Apply the claim-specific extraction tests.
- A comparison changed both model and team size, while its summary implied an isolated architecture gain. Preserve all changed factors and the budget unit.
- A draft said another course omitted trade-offs even though its lecture included local trade-offs. Compare the inspected content and preserve the scope of a gap claim.
- Authentication/fallback and broad process-stop mistakes disrupted earlier lanes. Use the owning tool policy and stop workers by their real IDs, with lifecycle authority retained by the parent.
