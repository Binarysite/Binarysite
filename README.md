# Alfredo Rosadilla

Senior software engineer and technical lead. I build AI agents and the interfaces around them, and I make them safe to ship: what never reaches the model, whether quality held, and what the agent is allowed to do in a shell.

My view: an agent is ready to ship when its worst case is bounded, not when its average looks good.

Santiago, Chile (UTC-3) · [rosadilla.dev](https://www.rosadilla.dev) · [LinkedIn](https://www.linkedin.com/in/alfredo-rosadilla/)

## Open source: three tools for shipping agents

The router decides what never reaches the model, the harness proves that did not lower quality, and the bench limits what the agent can do in a shell.

Each one runs with no API key, has zero runtime dependencies, typed declarations checked in CI on Node 22 and 24, and its known limits written down. None is on the npm registry; each block below clones and runs it.

### [llm-cascade-router](https://github.com/Binarysite/llm-cascade-router)
[![CI](https://github.com/Binarysite/llm-cascade-router/actions/workflows/ci.yml/badge.svg)](https://github.com/Binarysite/llm-cascade-router/actions/workflows/ci.yml)

Answer each chat message with the cheapest layer that can: exact match, local scoring, a cheap classifier, then the LLM. A trace per layer says which one answered and why.

```bash
git clone --depth 1 https://github.com/Binarysite/llm-cascade-router && cd llm-cascade-router && npm run ask
```

In the example (an invented sticker shop), 3 of 4 messages are answered without the LLM. On its own in-sample bank of 48 invented messages, 31 skip the main LLM; on 24 held-out messages, 7 do, with 1 wrong fixed answer.

### [agent-eval-harness](https://github.com/Binarysite/agent-eval-harness)
[![CI](https://github.com/Binarysite/agent-eval-harness/actions/workflows/ci.yml/badge.svg)](https://github.com/Binarysite/agent-eval-harness/actions/workflows/ci.yml)

Your LLM agent passes 95% of cases and still leaks one customer's order. This CI gate fails the build on that one: rule checks first, an optional LLM judge after, and one failed critical case exits 1 whatever the pass rate.

```bash
git clone --depth 1 https://github.com/Binarysite/agent-eval-harness && cd agent-eval-harness && npm run eval:regression
```

In the bundled example (a rule-based stand-in agent with its privacy check removed on purpose, scored by the mock judge), 23 of 24 cases pass (95.8%) and the run still exits 1. See the failing case, [prv-01](https://github.com/Binarysite/agent-eval-harness/blob/main/README.md#L23-L33), in the README output. The README also shows how to fetch the starter files.

### [shell-guard-bench](https://github.com/Binarysite/shell-guard-bench)
[![CI](https://github.com/Binarysite/shell-guard-bench/actions/workflows/ci.yml/badge.svg)](https://github.com/Binarysite/shell-guard-bench/actions/workflows/ci.yml)

Does your Claude Code safety hook catch `cd dir && rm -rf ~`? 89 dangerous, evasive and harmless commands, never run by the bench, thrown at any PreToolUse hook: what it blocks, what slips through, what it blocks by mistake.

```bash
git clone --depth 1 https://github.com/Binarysite/shell-guard-bench && cd shell-guard-bench && npm run example
```

Measured on cc-safety-net 2.6.7: it contains all 20 critical delete and git cases and blocks none of the 17 harmless commands. Kills, rsync, databases, deploys and sudo are outside what it promises.

Security: each repo has a SECURITY.md with private vulnerability reporting and CI actions pinned by commit SHA; CodeQL scans llm-cascade-router and agent-eval-harness (shell-guard-bench has none).

## What I work on

- **Applied AI.** An LLM chat agent for clinics: tool calling, a typed intent classifier with LLM fallback, human handoff, escalation of urgent cases, and guardrails (token budgets, kill switch, output guard, personal-data removal). It runs in a live pilot on demo sites for prospective clinics; no paying clinic yet. The agency's internal CRM and operations dashboard runs in production.
- **Evaluation.** A 294-scenario evaluation suite (65 critical) with an LLM judge, run through the real pipeline. The suite is private; the same release-gate idea, rewritten from scratch around an invented shop, is public in [agent-eval-harness](https://github.com/Binarysite/agent-eval-harness), with its [known limits](https://github.com/Binarysite/agent-eval-harness/blob/main/docs/DESIGN.md#known-limits).
- **Front end at scale.** At Blaize, an AI chip company (Nov 2023 to Sep 2026, nearly three years), I built the React and TypeScript front end of Blaize AI Studio in a team of about 8, and wrote the plan to split a ~1,400-file monolith into a monorepo.
- **Technical leadership.** More than five years at Globant (2016 to 2022), where I grew into a team lead at LATAM Airlines and a technical lead at Quantcast.
- **Stack.** TypeScript, React, Node.js, PostgreSQL, Docker, AWS.

Most of my work lives in private repositories (client and company code). Happy to walk through it in an interview.
