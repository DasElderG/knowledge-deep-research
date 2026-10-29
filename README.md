# knowledge-deep-research

An agent skill for broad and deep research, and an assignment to revise it.

The skill already works. It plans by question, reuses saved evidence and keeps a card for each source. It checks important claims against the saved originals and records what it couldn't establish. But it tells the agent which steps to take. Nothing in its design makes sure the finished report passes a stated bar. The assignment asks you to change that.

| Path | What it is |
|---|---|
| [SKILL.md](SKILL.md), [references/](references/) | The skill as it is today. The tag `original` marks this version. |
| [assignment/TASK.md](assignment/TASK.md) | The revision task |
| [assignment/TESTING.md](assignment/TESTING.md) | How to test the original and your revision on the same three tasks |
| [LICENSE](LICENSE) | MIT |

## Install

Clone the repository into your harness's skills folder. For Claude Code:

```bash
git clone https://github.com/DasElderG/knowledge-deep-research.git ~/.claude/skills/knowledge-deep-research
```

Then ask your agent for deep research on a question.

## Tools the Skill Names

The skill was written for one working environment, and it names some tools from it. You may not have them.

| The skill names | What it does there | What to use instead |
|---|---|---|
| `firecrawl`, `firecrawl-research-index`, `firecrawl-developer-index` | Web search and page capture | Any search-and-fetch tool that saves the page text, such as Firecrawl or Tavily |
| `knowledge-search` | Search over research saved earlier | Plain file search in your research folder |
| `systemops-establish-ground-truth`, `outcome-first-course-design` | Other skills it hands work to | Nothing. Leave that work out. |
| global `AGENTS.md` | Rules for delegating work to other agents | Your harness's own subagent feature |
