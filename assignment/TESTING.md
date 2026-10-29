# Test the Original and Your Revision on the Same Tasks

A revision is better only if the same test says so. Run both skills on three fixed research tasks and score every report with the same evaluator. Studio 06 already set up both: the tasks come from DeepResearchBench, and the evaluator is its original RACE scorer.

## What You Compare

| Arm | What runs |
|---|---|
| Original | The skill at the tag `original` in this repository |
| Revised | Your revision |
| No skill (optional) | One agent with the same prompt and no skill |

Put the original next to your revision:

```bash
git worktree add ../knowledge-deep-research-original original
```

## Keep Everything Else the Same

- Use the same model, reasoning effort and tools in every run.
- Set the same limits in every run: searches, page fetches, wall time and number of workers.
- Use the exact prompts of tasks 99, 93 and 100 from Studio 06's [TASKS.md](https://github.com/NickGuAI/agentic-engineering-course/blob/main/studio/studio-06/instruction/TASKS.md).
- Start every run in a new, empty workspace. The original skill reuses saved research, so a second run in the same folder would reuse the first run's work.
- Run each skill without a person in the loop. Neither skill may stop to ask you a question.

## Keep the Benchmark's Answers Away

The benchmark's reference reports and scoring criteria are public on GitHub, so a research agent can find them.

- Keep your benchmark checkout outside the research workspace.
- Block every URL that contains `deep_research_bench`.
- After each run, list the URLs the agent fetched.
- If a run opened the benchmark's files, record it as a failed run.

## Run Each Task Three Times

Run each arm three times on each task. Keep one Markdown report from each run: the report a reader would get. The RACE helper has two report folders, `single` and `multi`. Here, `single` holds the original and `multi` holds your revision.

```text
test/
├── run-1/reports/single/99.md   original
│                       /93.md
│                       /100.md
│         reports/multi/99.md    revised
│                      /93.md
│                      /100.md
├── run-2/reports/...
└── run-3/reports/...
```

## Score with RACE

Clone the [course repository](https://github.com/NickGuAI/agentic-engineering-course) for the helper. Install the pinned evaluator once, as in step 2 of Studio 06's [EVALUATION.md](https://github.com/NickGuAI/agentic-engineering-course/blob/main/studio/studio-06/instruction/EVALUATION.md). Then score each run into its own new output folder.

```bash
COURSE=path/to/agentic-engineering-course
BENCHMARK=path/to/deep-research-bench
PYTHON=path/to/evaluator-venv/bin/python

read -rsp 'OpenAI API key: ' OPENAI_API_KEY
export OPENAI_API_KEY
for n in 1 2 3; do
  "$PYTHON" "$COURSE/studio/studio-06/instruction/code/evaluate.py" \
    --submission "test/run-$n" \
    --benchmark "$BENCHMARK" \
    --output "test/run-$n/eval"
done
unset OPENAI_API_KEY
```

Each run makes paid model calls on your key. RACE gives each report four dimension scores (comprehensiveness, insight, instruction following and readability) and an overall score. An overall score of 0.5 means your report and the benchmark's reference report earned the same weighted total. Higher is better.

## Measure the Judge's Noise

Score one run a second time into a new folder:

```bash
"$PYTHON" "$COURSE/studio/studio-06/instruction/code/evaluate.py" \
  --submission "test/run-1" --benchmark "$BENCHMARK" --output "test/run-1/eval-repeat"
```

The same reports get different scores. That difference is the judge's noise. If the two arms differ by less than this, call it a tie.

## Check What RACE Doesn't

RACE compares each report with a reference report. It doesn't open your sources. Check the citations yourself, the same way in both arms.

1. In each report, take the first ten sentences that state a number, a date or a quotation.
2. Open the source each one cites.
3. Mark each sentence: supported, partly supported, not supported or no citation.
4. Check that every cited source can still be opened (Q8).

## Record the Cost

For each run, record the tokens, searches, page fetches and wall time. A failed run stays in the count. Report the cost per accepted report ("Full Cost per Accepted Request, Including Failed Attempts", Lecture 7).

## Decide Before You Look

Write your decision rule in DESIGN.md before you run the tests. Which result would make you keep the revision? For example, keep it if three things hold. Its mean RACE score is within the judge's noise of the original. It passes more citation checks. It costs at most 1.5 times as much per report.

## Results Table

| Task | Arm | RACE overall, runs 1–3 | Mean | Citations supported | Failed runs | Cost per report |
|---|---|---|---|---|---|---|
| 99 | Original | | | | | |
| 99 | Revised | | | | | |
| 93 | Original | | | | | |
| 93 | Revised | | | | | |
| 100 | Original | | | | | |
| 100 | Revised | | | | | |
