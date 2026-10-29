# Research design and evidence review

Load when planning a broad investigation, choosing lanes, comparing teaching materials, analyzing a system, evaluating a study, or resolving a disputed conclusion. This reference supplies depth tests and a worked package; [source-content-card.md](source-content-card.md) owns source records.

## Shape the research around questions

Begin with the intended use: explain a topic, compare actual sources, prepare teaching, test a claim, or support a decision. Translate it into answerable questions and hard conditions. A condition such as a recent term, deployed product, equal inference budget, named textbook edition, or fixed code version changes which evidence qualifies.

For each question, record what would directly answer it, what is already available, the exact remaining gap, and what happens if the gap stays open. Select relevant dimensions rather than filling every row below mechanically.

| Dimension | Question to answer | Suitable evidence |
|---|---|---|
| Concepts | How is the term defined, by whom, and within what scope? | Original definitions and surrounding argument; precise edition/page or dated official usage. |
| Teaching | In what order is the subject taught, with what explanation, examples and practice? | Actual syllabus, published lecture body, exercises, and reading instructions. |
| Mechanisms | What produces the behavior? What variables or assumptions matter? | Derivation, algorithm, concrete trace, implemented process, or empirically tested model. |
| Implementation | How does the actual system make decisions and move data/state? | Versioned documentation, fixed-commit code, operational traces or credible first-hand engineering records. |
| Effects | What changed, relative to what, with what uncertainty and resources? | Methods, complete tables, baselines, outcomes, repetitions and measurement boundaries. |
| Alternatives | What other approaches solve the same problem? When does the apparent advantage disappear? | Competing methods, replication, ablation, negative results, migration and post-mortem evidence. |
| Transfer | Does a mechanism from another discipline apply under comparable assumptions? | The original model and an explicit mapping of variables, differences, and a testable transfer claim. |

Breadth adds missing alternatives, evidence types, or perspectives. Depth follows a claim from a high-level statement to its mechanism, method, assumptions, consequences, and boundary. A long list of search hits provides neither by itself.

## Evaluate the evidence for the specific claim

Do not turn a publisher hierarchy into an automatic verdict. Apply these questions together:

| Test | Ask |
|---|---|
| Authority | Does this source control or directly establish this fact? A school controls its syllabus, a vendor documents its interface, and a textbook can establish its own definition. None automatically proves comparative quality. |
| Directness | Is this the original passage, data, implementation, or first-hand observation? Does the cited passage actually contain the asserted detail? |
| Method | Are the sample, comparison, measurements, controls, confounders and uncertainty appropriate for the claim? A testimonial and a controlled experiment answer different questions. |
| Independence | Are apparent corroborators separate observations, or quotations, mirrors, shared datasets, and retellings of one original? |
| Incentives | What does the author gain from the framing? First-party results remain attributable evidence; an independent opinion is not automatically stronger than well-described first-party data. |
| Scope and freshness | Does the task, population, date, edition, deployment, or version match the question? Does the reading scope cover the needed passage? |
| Contrary evidence | What credible alternative explanation or finding challenges the interpretation? Can the disagreement be resolved by methods, versions, or definitions? |

Use claim-level verdicts:

- `supported`: the inspected evidence supports the wording within its stated conditions. Specify whether this is direct documentation, a reported result, or independent corroboration.
- `partial`: some wording is supported, but an important condition, comparison, or inference is not.
- `contradicted`: inspected evidence conflicts with the wording; identify the exact point and competing evidence.
- `unverified`: necessary evidence is missing, unread, inaccessible, or inconclusive.

Reserve causal or universal conclusions for evidence that can support them. Confidence should describe the exact proposition and its conditions. A marketing statement can be reported as a statement without endorsing its effect. A source's failure to mention something does not establish that it does not exist.

## Extract at the depth the question needs

### Definitions, textbooks and theory

Read the definition and its surrounding explanation. Preserve the original language where exact terminology matters, with a short necessary quote and edition/page. Distinguish related terms, scope, assumptions, and examples. Keep source definitions separate from an instructor's working synthesis. A table of contents is a lead to a chapter, not proof of its argument.

For mathematics, record the variables, assumptions, objective, main result, and interpretation. For a management or organizational analogy, explain which causal mechanism transfers and which assumptions differ; analogy alone is not empirical validation.

### Courses and official tutorials

Build comparison cards from the actual materials, covering:

- institution/provider, term/date and material status;
- original sequence and actual headings, preserving the source's granularity;
- definitions, distinctions and prerequisite assumptions;
- how a concept is introduced and developed, including examples, diagrams, questions, demonstrations and exercises;
- local trade-offs and production topics actually covered, with locators;
- reading scope and missing or future materials.

Label a published lecture, a complete syllabus, a catalog description, a future schedule, and an adjacent course distinctly. Verify claims such as "does not cover communication" against the inspected scope; use "not found in the inspected sections" when that is all the evidence establishes. A university name or course title does not prove depth.

When comparing teaching approaches, show their original flows side by side, then separate observed differences from any proposed adaptation. If only comparison is requested, stop there. Give course design a content-and-evidence handoff rather than silently treating source order as the approved classroom sequence.

### Products, frameworks and implementations

Start from the user task and claimed outcome. Trace one actual request through entry, routing/decision, task allocation, tools, data, context/state, communication, integration, stopping and output. Explain which parts are fixed code, model decisions, human decisions, or undocumented. Include the relevant failure/recovery behavior when it changes the architectural judgment.

Bind the analysis to product mode and version, document date, release, or commit. A research prototype, public repository, production deployment, adoption claim, license, and measured benefit are separate facts. Distinguish documented behavior from code-reachable behavior and from what was actually observed running. Do not invent proprietary internals to complete a diagram; mark unknown edges.

Explain the alternatives and consequences of important choices. A role-name diagram needs a control/data/state trace to support an architectural claim. Read docs before interpreting an unfamiliar subsystem, and inspect the relevant implementation when the question requires it. Executing or deploying the product requires its own authority.

### Papers and empirical comparisons

Read the methods and relevant tables, including decisive captions and supplementary qualifications. Record:

- task/data/population and what counts as success;
- model and system versions, baseline strength, and all changed factors;
- architecture, prompting, tools, search, training, and evaluation procedures relevant to the claim;
- budget unit and inclusion boundaries: calls, tokens, credits, money, elapsed time, total compute, verification, retries and environment cost as applicable;
- metric definition, unit, denominator, uncertainty, repetitions/seeds and exceptions;
- result, mechanism evidence, confounders, generalization limits and contrary results.

Changing model and team size together does not isolate organization. Equal model credits do not imply equal total compute. A whole-suite dollar total is not per-task cost. Separate capability training, test-time inference, model routing, and coordination when those mechanisms differ. Retain failed runs and explicitly labeled saved traces.

For influential literature, follow references, citers, replications, and rival methods from strong anchors. Verify citation counts with dated provenance if reporting them; popularity is not correctness. An abstract can locate a candidate but cannot establish unread implementation or methods details.

## Delegation and integration

Choose independent units that can answer specific gaps. Common choices include a concept family, a set of actual curricula, empirical comparisons, product implementations, or a contested claim. Do not require fixed lane counts or duplicate every search. Overlap is useful when it can independently inspect a disputed passage or test another interpretation.

A lane brief includes the research question and hard conditions, existing reusable cards and audits, exact gap, suitable evidence, exclusions, write ownership, deliverables, required locators and reading scope, authorized tools, any explicit budget, verification checks, and handoff. Use the global delegation rules for transport, model choice, actual IDs and lifecycle. Record launch, progress, terminal status and output in the manifest, and report failures as failures.

The parent defines the framework and owns judgment. It reads lane outputs, inspects the load-bearing original passages, resolves conflicting terms/versions, and rewrites an integrated explanation. It checks the actual table, code path or quotation that supports a conclusion rather than relying on another worker's summary. A worker may collect evidence or run a check without owning acceptance.

When the evidence is ready for long-form teaching, chapter drafting may proceed under explicit chapter interfaces: question answered, prerequisite concepts, expected mechanism depth, content/evidence handoff, exclusions, and what the next chapter consumes. The chapter count and depth follow the material. This is an authoring stage, not a reason to re-fetch each chapter's sources.

## Worked example

This entire package is hypothetical. The source, IDs, paths, findings and worker below are illustrative; the [complete content card](source-content-card.md#complete-hypothetical-example) supplies the fictional source details.

The requested task is: "Explain queue separation and compare the available evidence before choosing a service architecture." The current request is a learning/comparison task, so the package does not recommend a deployment.

### research-plan.md

```markdown
# Queue separation: explanation and evidence comparison

Use/mode: learning and source comparison for an architecture discussion.
Conditions: distinguish queue organization from increased worker capacity;
include tail latency and the full cost boundary. No implementation requested.
Reuse: notes/queue-separation.md and raw/queue-separation-v2.md already exist.
Scope: explain the mechanism and qualify the existing experiment. No new
network acquisition is needed for Q1 or C2. Equal-capacity effects remain open.
Budget: none specified; stop when the requested questions are answered or bounded.

| Question | Direct evidence | Existing material | Gap / consequence |
|---|---|---|---|
| Q1 How can separation change waiting? | Design trace and assumptions | S-queue-v2 Design | Explain classifier/capacity assumptions |
| Q2 Does the experiment isolate separation? | Worker counts and method | S-queue-v2 Method/Table 2 | It does not: capacity changed |
| Q3 What evidence would justify choosing? | Equal-capacity quality, latency and cost | None identified | Open; no design recommendation |
```

### source_index.md

```markdown
| ID | Underlying source | Version / scope | Card | Saved evidence | Provider |
|---|---|---|---|---|---|
| S-queue-v2 | [Queue Separation in a Document Review Service](https://example.org/engineering/queue-separation-v2) | v2; selected-sections | cards/S-queue-v2.md | raw/queue-separation-v2.md | Existing saved web capture |

The source's release-note mirror is one derivative record, not a new experiment.
```

### fact_check.md

```markdown
| Claim | Proposed wording | Original locator / parent inspection | Verdict and corrected use |
|---|---|---|---|
| C1 | Long jobs can delay short jobs in one FIFO queue | S-queue-v2 Design; parent read saved trace 2026-04-12 | supported as the described mechanism, subject to workload assumptions |
| C2 | Separation reduces p95 40% at equal capacity | S-queue-v2 Method and Table 2; parent read saved original 2026-04-12 | partial: 20 s to 12 s reported, but workers increased 8 to 16; equal-capacity inference removed |
| C3 | Separation lowers cost per accepted job | S-queue-v2 Results lacks this measurement | unverified; leave open |

Corrections: C2 changed in report.md, the content card, and the comparison table.
Original v1 capture retained and linked as superseded.
```

### search_manifest.md

```markdown
Coverage: existing queue-separation notes, v2 original and earlier audit.
Acquisition: reuse-only; no web preflight or new fetch performed.

| Unit | Real ID | Scope | Output | Terminal state |
|---|---|---|---|---|
| Queue experiment audit | hypothetical-worker-id | Inspect saved Method/Table 2 | lanes/queue-audit.md | completed; parent-reviewed; closed by owner |

Errors: none. Limits: appendix sweep unread; no equal-capacity study identified
within this package. The terminal state above illustrates a lifecycle receipt;
an actual run must record the real ID and observed state.
```

### report.md

```markdown
# Queue separation: mechanism and evidence

Shared FIFO → long jobs occupy workers → short jobs wait behind them.
Separate pools → fewer long/short queue interactions → capacity may be stranded.

The source describes that mechanism under an estimated-job-length policy.
Its replay reports p95 changing from 20 s to 12 s while worker count doubles.
This comparison establishes neither equal-capacity benefit nor lower total cost.
See [the fictional source](https://example.org/engineering/queue-separation-v2),
Design, Method and Table 2.

The material supports explaining the mechanism and showing a confounded
comparison. Choosing an architecture would require equal-capacity results,
classifier-error behavior, quality and full cost per accepted job. Those
questions remain open; this comparison makes no deployment recommendation.
```

## Final review

Use the acceptance checks in the entry skill. Inspect the report as a reader: can they explain the mechanism, see what was actually compared, distinguish evidence from inference, locate the decisive content, and identify what remains unknown? Check every required question rather than inferring completeness from source counts. Where new evidence could change a conclusion, state which result or condition would do so.
