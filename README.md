# Alfredo Rosadilla

Senior software engineer and technical lead. I build AI agents and the interfaces around them, with an eye on evaluation, safety and cost.

Santiago, Chile (UTC-3) · [rosadilla.dev](https://www.rosadilla.dev) · [LinkedIn](https://www.linkedin.com/in/alfredo-rosadilla/)

## Featured project

- **[agent-eval-harness](https://github.com/Binarysite/agent-eval-harness)**: release gate for LLM agents. Deterministic rule checks, an optional LLM judge, and a run that fails if any critical case fails: in the bundled example 23 of 24 cases pass (95.8%) and the run still exits 1. Zero runtime deps.

It runs with one command and no API key. It is JavaScript (ESM) with JSDoc and hand-written `.d.ts` types checked by `tsc` in CI.

## What I work on

- **Applied AI.** An LLM chat agent for clinics: tool calling, a typed intent classifier with LLM fallback, human handoff, escalation of urgent cases, and guardrails (token budgets, kill switch, output guard, personal-data removal). It runs in a live pilot on demo sites for prospective clinics; no paying clinic yet. The agency's internal CRM and operations dashboard runs in production.
- **Evaluation.** A 294-scenario evaluation suite (65 critical) scored by an LLM judge, run through the real pipeline. The suite is private; the release gate it uses is public in [agent-eval-harness](https://github.com/Binarysite/agent-eval-harness), with its [known limits](https://github.com/Binarysite/agent-eval-harness/blob/main/docs/DESIGN.md#known-limits).
- **Front end at scale.** Nearly three years at Blaize, an AI chip company, building the React and TypeScript front end of Blaize AI Studio, and the plan to split a ~1,400-file monolith into a monorepo.
- **Technical leadership.** More than five years at Globant as a team lead for clients such as LATAM Airlines and Quantcast.
- **Stack.** TypeScript, React, Node.js, PostgreSQL, Docker, AWS.

Most of my work lives in private repositories (client and company code). Happy to walk through it in an interview.
