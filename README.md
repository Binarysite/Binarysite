# Alfredo Rosadilla

Senior software engineer and technical lead. I build AI agents and the interfaces around them, with an eye on evaluation, safety and cost.

My view: an agent is ready to ship when its worst case is bounded, not when its average looks good.

Santiago, Chile (UTC-3) · [rosadilla.dev](https://www.rosadilla.dev) · [LinkedIn](https://www.linkedin.com/in/alfredo-rosadilla/)

## Open source

Three small tools for shipping agents. Each one clones and runs with no install and no API key, has zero runtime dependencies, typed declarations checked in CI on Node 22 and 24, and its known limits written down.

- **[agent-eval-harness](https://github.com/Binarysite/agent-eval-harness)**: can this agent be released? Deterministic rule checks, an optional LLM judge, and a run that fails if any critical case fails. In the bundled example (a rule-based stand-in agent with its privacy check removed on purpose, scored by the mock judge), 23 of 24 cases pass (95.8%) and the run still exits 1.
- **[shell-guard-bench](https://github.com/Binarysite/shell-guard-bench)**: does the guard on a coding agent's shell hold? 89 dangerous, evasive and harmless commands, none executed, thrown at any Claude Code PreToolUse hook: what it blocks, what slips through, what it blocks by mistake.
- **[llm-cascade-router](https://github.com/Binarysite/llm-cascade-router)**: does this message need the model at all? Exact match, local scoring and a classifier answer first, with a trace per layer: on its own in-sample bank of 48 invented messages, 31 skip the main LLM; on 24 held-out messages, 7 do, with 1 wrong fixed answer.

## What I work on

- **Applied AI.** An LLM chat agent for clinics: tool calling, a typed intent classifier with LLM fallback, human handoff, escalation of urgent cases, and guardrails (token budgets, kill switch, output guard, personal-data removal). It runs in a live pilot on demo sites for prospective clinics; no paying clinic yet. The agency's internal CRM and operations dashboard runs in production.
- **Evaluation.** A 294-scenario evaluation suite (65 critical) with an LLM judge, run through the real pipeline. The suite is private; the same release-gate idea, rewritten from scratch around an invented shop, is public in [agent-eval-harness](https://github.com/Binarysite/agent-eval-harness), with its [known limits](https://github.com/Binarysite/agent-eval-harness/blob/main/docs/DESIGN.md#known-limits).
- **Front end at scale.** At Blaize, an AI chip company (Nov 2023 to Sep 2026, nearly three years), I built the React and TypeScript front end of Blaize AI Studio in a team of about 8, and wrote the plan to split a ~1,400-file monolith into a monorepo.
- **Technical leadership.** More than five years at Globant (2016 to 2022), where I grew into a team lead for clients such as LATAM Airlines and Quantcast.
- **Stack.** TypeScript, React, Node.js, PostgreSQL, Docker, AWS.

Most of my work lives in private repositories (client and company code). Happy to walk through it in an interview.
