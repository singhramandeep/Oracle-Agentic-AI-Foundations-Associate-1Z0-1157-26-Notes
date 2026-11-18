[🏠 Home](../README.md) › Module 2

# Module 2: LangChain for AI Agents

LangChain building blocks (models, prompts, chains, memory), building agents with `create_agent`, and what happens under the hood.

## Lessons

| # | Lesson | Figures |
|---|---|---|
| 2.1 | [Module Introduction](01-module-introduction.md) |  |
| 2.2 | [Introduction to LangChain](02-introduction-to-langchain.md) |  |
| 2.3 | [Demo: LangChain Building Blocks](03-demo-langchain-building-blocks.md) |  |
| 2.4 | [Building Your First Agent with LangChain](04-building-your-first-agent-with-langchain.md) |  |
| 2.5 | [Demo: Your First LangChain Agent](05-demo-your-first-langchain-agent.md) |  |
| 2.6 | [LangChain Agents Under the Hood (Part 1)](06-langchain-agents-under-the-hood-part-1.md) |  |
| 2.7 | [LangChain Agents Under the Hood (Part 2)](07-langchain-agents-under-the-hood-part-2.md) |  |
| 2.8 | [Summary](08-summary.md) |  |

## Key Concepts Introduced

- **LangChain** — An open-source framework of composable building blocks (models, prompts, chains, memory, tools, agents) for LLM apps. ([2.2](02-introduction-to-langchain.md))
- **LangGraph** — LangChain's graph-based runtime for stateful, controllable agent workflows; `create_agent` runs on top of it. ([2.4](04-building-your-first-agent-with-langchain.md))
- **Chains / LCEL** — Components connected with the pipe operator (`prompt | model | parser`) into a left-to-right pipeline. ([2.3](03-demo-langchain-building-blocks.md))
- **Prompt Template** — A reusable prompt with placeholders filled in at run time; chat templates use system/human/AI message roles. ([2.3](03-demo-langchain-building-blocks.md))
- **Memory** — Stored conversation messages fed back into the prompt so a stateless LLM keeps context. ([2.3](03-demo-langchain-building-blocks.md))
- **create_agent** — LangChain's one-call constructor that wires a model, tools and a system prompt into a ReAct agent. ([2.5](05-demo-your-first-langchain-agent.md))

---

⬅️ [Module 1: Introduction to AI Agents](../01-introduction-to-ai-agents/README.md) | [Module 3: Introduction to MCP](../03-model-context-protocol/README.md) ➡️
