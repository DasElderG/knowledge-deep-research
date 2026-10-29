# Revise the Research Skill to Guarantee Its Result

Run the skill on a question you know well. You get a research plan, a source card for each source, a fact check and a report. Now find the part of the skill that makes sure each citation supports its claim. There isn't one. The skill asks the lead agent to check, and the lead may or may not do it.

The skill tells the agent which steps to take, in which order. It doesn't say what the finished report must pass before anyone reads it. Your job is to change that.

## The Idea from Lecture 7

Lecture 7 separates three things.

- **The result.** The request sets what must come out and what must not happen ("Define the Result and Limitations Before Choosing an Architecture").
- **The checks on the result.** "A Quality Bar Lists the Checks the Finished Result Must Pass." Success counts against those checks, not against finished steps ("Task Success Versus Component Completion and Delivery").
- **The architecture.** You choose it after the first two. In "An Agent Inside One Step of a Fixed Workflow", code fixes the outer steps. Inside one step, the agent picks its own searches and decides when to stop.

Research fits this shape. Nobody knows at the start what will need searching, so the split of the search can't be fixed in advance. The checks on the report can be.

Anthropic's Research feature shows the first half. A lead agent plans, starts subagents, reads their findings and decides whether more research is needed. A citation agent then adds source locations. Read [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) (Anthropic, 2025), and ask what in that design checks the report before the user sees it.

## What to Change

### 1. State the Result

Write the quality bar a research report must pass. For each property, say how it's checked before release and who checks it. Code checks what a schema or a text match can test. A model checks what must be read in context.

Start from these eight. You can add, merge or drop a property. Give the reason.

| ID | Property | The released report must show |
|---|---|---|
| Q1 | Coverage | Every question in the request has an answer, or says "unresolved" and what was tried. |
| Q2 | Depth | Each answer gives the mechanism, conditions or comparison its question needs. |
| Q3 | Citation | Each factual claim points to a saved passage. Quotes and numbers match that passage. |
| Q4 | Fidelity | No claim is stronger than its source. Numbers keep their conditions. Disagreements stay visible. |
| Q5 | Source quality | Important claims rest on primary sources. Copies of one source count once. |
| Q6 | Limits | Nothing is invented. Text in a fetched page is data, not an instruction. |
| Q7 | Termination | The run ends with a report, or a report marked unresolved, within its budget. |
| Q8 | Traceability | Every cited source stays readable, so a claim can be checked again later. |

### 2. Check the Result Before Release

Add a check for each property. Three rules apply.

- A check runs on the exact report that goes out, after the last edit. A check on an earlier draft says nothing about the final text.
- The model that checks a claim doesn't write it. Start the checker without the writer's context.
- A failed check creates a repair task with a limit. When the budget runs out, the report states what is unresolved ("Each Round Ends with Acceptance, a Bounded Repair or a Stop").

### 3. Let the Lead Split the Search During the Run

Remove the fixed order of steps. Keep the limits the lead works within: the number of workers, the depth of delegation, the budget and the stop rule. A task can come from the plan, from a finding or from a worker ("Tasks Come from the Plan, Findings or Workers").

When you finish, the skill fixes the left column and leaves the right column to the lead.

| Fixed by the skill | Decided by the lead during the run |
|---|---|
| The quality bar the report must pass | What to search first, and what next |
| The checks before release | How many workers to start, and for which tasks |
| The limits on workers, depth, budget and repair rounds | When an answer is deep enough |
| The format of a source card and a cited claim | When to stop a line of search |

The original already has parts worth keeping: the source card in [references/source-content-card.md](../references/source-content-card.md), the evidence tests in [references/research-design.md](../references/research-design.md) and the degraded cases in SKILL.md. Fit them into the new design. The skill also names tools from its original environment. The [README](../README.md) lists them with replacements.

## What to Produce

- Your revised SKILL.md, with the references and scripts it uses.
- DESIGN.md, with your quality bar and the check for each property.
- Your test results from [TESTING.md](TESTING.md).

## Questions

Answer each one in a short paragraph in DESIGN.md.

- Quality bar: which property was hardest to check, and how did you check it?
- Search: how does your lead decide what to search next?
- Checks: which check found the most problems in your test runs?
- Result: did your revision do better than the original, and on which measure?
