# Sample Solution: Design Note

This is one possible answer to [TASK.md](../TASK.md). The revised skill is in [SKILL.md](SKILL.md). It hasn't been tested yet, so the results section below is empty on purpose.

## What Changed

The original tells the agent what to do: frame, reuse, broaden, preserve, integrate, deliver. The revision says what the report must pass, and checks it before release. Between the contract and the checks, the lead decides how to search.

```text
 CONTRACT (fixed)          LOOP (lead decides, inside limits)          CHECKS (fixed)        RELEASE
 research questions   ──►  ledger of tasks                        ──►  C1 coverage      ──►  report.md
 quality bar Q1–Q8         tasks from the plan, findings, workers      C2 citation           checks.md
 limits                    workers return claims or "unknown"          C3 content
 budget + reserve          accept · bounded repair · stop              C4 limits
                                 ▲                                     C5 trace
                                 │                                        │
                                 └─ a failed check becomes a repair task ─┘
```

## Quality Bar and Checks

The exact pass rules are in SKILL.md, under "Checks before release". This table gives the reason for each choice of checker.

| Property | Check | Who checks | Why this checker |
|---|---|---|---|
| Q1 Coverage | C1 | Code | Matching RQ IDs to answer headings is a text match. |
| Q2 Depth | C3 | Verifier model | Whether an answer explains enough has to be read in context. |
| Q3 Citation | C2 | Code, then the verifier | Markers, quotes and numbers can be matched against saved text. A miss can be a formatting problem, so a model looks before anything fails. |
| Q4 Fidelity | C3 | Verifier model | "Stronger than its source" needs the claim and the passage read together. |
| Q5 Source quality | C3 | Verifier model | Whether a source is primary, and whether two sources are really one, needs judgment. |
| Q6 Limits | C4 | Harness and verifier | Tool permissions stop outside effects. The verifier catches invented sources and followed page instructions. |
| Q7 Termination | Loop limits | Harness | The budget, the reserve and the stop rule end the run. A check can't do that. |
| Q8 Traceability | C5 | Code | A file either exists with the recorded hash or it doesn't. |

Two rules hold for every check. It runs on the exact text that ships, after the last edit. And the model that checks a claim isn't the one that wrote it ("Context Isolation for a Code Review Agent", Lecture 7).

## Fixed Versus Decided During the Run

| Fixed by the skill | Decided by the lead |
|---|---|
| The contract: questions, quality bar, limits, budget | What to search first, and what next |
| Checks C1–C5 and their pass rules | How many workers to start, and for which tasks |
| Workers don't start workers. Two empty rounds stop a line. At most two repair rounds. | When an answer is deep enough |
| The formats of the ledger, the card and a cited sentence | Which lead to follow after a finding |

## What Was Removed, and Why

- **The six-step order.** It fixed the process, and nothing in it guaranteed the result.
- **Lanes chosen while planning.** At the start, nobody knows what will need searching. Tasks now come from findings, too ("Tasks Come from the Plan, Findings or Workers").
- **"The parent personally compares."** The writer checking its own work shares its own blind spots. Code checks what code can test, and a fresh-context verifier reads the rest.
- **Names of tools from the original environment.** The revision names what it needs, not which product provides it.

The source card, the evidence tests in `research-design.md`, reuse before fetching and the degraded cases stay. They were already about the result.

## Choices This Sample Made

- All eight properties apply to every run. A request can add checks but not remove them.
- The contract is written from the request. Nobody approves it before the search starts.
- The output is a report. Teaching material built from it is a separate job.
- The lead runs in one session and starts its own workers. Workers don't delegate.

## Questions from the Task

**Quality bar: which property was hardest to check, and how did you check it?** Q4, fidelity. No text match can tell whether a sentence says more than its source. C3 hands that to a verifier that starts with no memory of the writing. That verifier can still share the writer's model and its blind spots. Using a different model for C3 is a cheap next step.

**Search: how does your lead decide what to search next?** It starts with a few tasks per research question. After each round it adds a task for each gap, contradiction or better source the findings reveal. It stops a line after two rounds with no new accepted claim.

**Checks: which check found the most problems in your test runs?** Not tested yet. The guess is C2, because quotes and numbers drift easily between a source and a summary. The test will show whether that's right.

**Result: did your revision do better than the original, and on which measure?** Not tested yet. See the decision rule below.

## Test Status

Not run. [TESTING.md](../TESTING.md) asks for the decision rule before any run. This sample's rule keeps the revision if three things hold. Its mean RACE score is within the judge's noise of the original's. It passes more citation checks. It costs at most 1.5 times as much per report.

## Trying the Sample

The sample links to the repository's `references/` folder from its own location. To install it as the skill, copy it over the top-level SKILL.md and change each `../../references/` link to `references/`.
