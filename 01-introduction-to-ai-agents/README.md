[🏠 Home](../README.md) › Module 1

# Module 1: Introduction to AI Agents

What an AI agent is, its core components, reasoning patterns, a first hand-built agent, and safety guardrails.

## Lessons

| # | Lesson | Figures |
|---|---|---|
| 1.1 | [What Is an AI Agent?](01-what-is-an-ai-agent.md) |  |
| 1.2 | [Agentic AI Core Components](02-agentic-ai-core-components.md) |  |
| 1.3 | [Reasoning Patterns](03-reasoning-patterns.md) |  |
| 1.4 | [Building Your First AI Agent](04-building-your-first-ai-agent.md) |  |
| 1.5 | [Safety & Guardrails](05-safety-and-guardrails.md) |  |
| 1.6 | [Summary](06-summary.md) |  |

## Key Concepts Introduced

- **AI Agent** — A system that wraps an LLM in a decision loop with tools so it can perceive, reason, act and observe until a goal is met. ([1.1](01-what-is-an-ai-agent.md))
- **Agent Loop** — The iterative Perceive → Reason → Act → Observe cycle that drives an agent until it has a final answer or hits a safety limit. ([1.1](01-what-is-an-ai-agent.md))
- **Orchestration Layer** — The application controller (the agent's 'nervous system') that manages the loop, memory, tool routing, state and guardrails. ([1.2](02-agentic-ai-core-components.md))
- **Function Calling** — The LLM emits a structured tool-call request from a JSON schema; the runtime, not the model, executes it and returns an observation. ([1.2](02-agentic-ai-core-components.md))
- **ReAct** — Reason + Act: the model interleaves reasoning steps with tool calls and observations. ([1.3](03-reasoning-patterns.md))
- **Chain-of-Thought** — Prompting the model to reason step by step before answering. ([1.3](03-reasoning-patterns.md))
- **Tree-of-Thought** — Exploring several reasoning paths in parallel and evaluating them before committing to one. ([1.3](03-reasoning-patterns.md))
- **Guardrails** — System-level checks and limits (input, output, tool and iteration controls) that keep an agent safe and on task. ([1.5](05-safety-and-guardrails.md))
- **Human-in-the-Loop** — Requiring human approval before an agent takes high-impact actions. ([1.5](05-safety-and-guardrails.md))

---

[Module 2: LangChain for AI Agents](../02-langchain-for-ai-agents/README.md) ➡️
