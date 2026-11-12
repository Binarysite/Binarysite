# Alfredo Rosadilla

I build LLM agents and the gates that decide whether they ship: evals that fail the build on
the one case that matters, guards that bound what an agent may run in a shell, and routing
that keeps repeat questions away from the model.

Senior software engineer and tech lead. Santiago, Chile (UTC-3).
[rosadilla.dev](https://www.rosadilla.dev) · [LinkedIn](https://www.linkedin.com/in/alfredo-rosadilla/)

## Open source

| Repo | The question it answers | Measured |
|---|---|---|
| [agent-eval-harness](https://github.com/Binarysite/agent-eval-harness) | Did this change make the agent unsafe, even though the pass rate looks fine? | 23 of 24 cases pass and the build still exits 1 on a privacy leak. Its LLM judge was [measured on 48 labelled replies](https://github.com/Binarysite/agent-eval-harness/tree/main/reports/calibration): with `deepseek-reasoner` the gate caught 25 of 25 bad ones (after a fix that measurement found) and wrongly failed 1 of 23 good ones |
| [shell-guard-bench](https://github.com/Binarysite/shell-guard-bench) | Does your Claude Code hook stop `cd x && rm -rf ~`, or only `rm -rf ~`? | 201 commands thrown at a hook as data, never executed by the bench. cc-safety-net 2.7.12 kept all 55 blocks its docs promise; the families outside its scope that still pass are [reported upstream](https://github.com/kenryu42/cc-safety-net/issues/350) |
| [mcp-footprint](https://github.com/Binarysite/mcp-footprint) | How many context tokens does an MCP server cost before you type anything? | Seven official servers measured with pinned versions: Notion's tool definitions come to 17,140 o200k tokens, sequential-thinking's to 488. A CI budget fails the build when a server's definitions grow. [Numbers shared on Notion's tool-filter request](https://github.com/makenotion/notion-mcp-server/issues/111#issuecomment-6812837460) |
| [llm-cascade-router](https://github.com/Binarysite/llm-cascade-router) | Which messages never needed the LLM? | On CLINC150's 5,500 public test messages, the local layers answer 110 of 450 in-scope questions with 2 wrong out of 112 answers given, and send the rest to the model |

Each one runs with one command and no API key, and CI fails if a number in its README
drifts from the committed run. The harness, the bench and the router have zero runtime dependencies.

## Recent work

- **Aureliai Solutions.** An LLM chat agent for clinics: tool calling, a typed intent
  classifier with an LLM fallback, human handoff, escalation of urgent cases, token budgets
  and a kill switch. It is in a live pilot on demo sites for prospective clinics; no paying
  clinic yet. Its evaluation suite has 294 scenarios (65 critical) and runs through the real
  pipeline; agent-eval-harness is that release gate rebuilt in the open.
- **Blaize** (AI chips), Nov 2023 to Sep 2026. The React and TypeScript front end of Blaize
  AI Studio, in a team of about 8, and the plan to split a ~1,400-file monolith into a monorepo.
- **Globant.** Grew into team lead at LATAM Airlines and technical lead at Quantcast.

## How I work

- The worst case gates a release, not the average.
- Every number in a README comes from a command you can rerun.
- I build with Claude Code; the co-author lines in the history are on purpose.

Most of my work lives in private client and company repositories. Happy to walk through it.
