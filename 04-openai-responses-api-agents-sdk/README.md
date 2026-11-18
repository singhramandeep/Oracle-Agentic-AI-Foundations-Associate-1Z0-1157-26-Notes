[🏠 Home](../README.md) › Module 4

# Module 4: OpenAI Responses API & Agents SDK Basics

The OpenAI agent stack: Responses API, Agents SDK, tools, multi-agent handoffs, guardrails, and a customer support agent demo.

## Lessons

| # | Lesson | Figures |
|---|---|---|
| 4.1 | [OpenAI Agent Stack](01-openai-agent-stack.md) | 1 |
| 4.2 | [OpenAI Responses API](02-openai-responses-api.md) | 3 |
| 4.3 | [OpenAI Agents SDK](03-openai-agents-sdk.md) | 1 |
| 4.4 | [Demo: Responses API and Agents SDK](04-demo-responses-api-and-agents-sdk.md) | 2 |
| 4.5 | [Tools & Function Calling](05-tools-and-function-calling.md) | 5 |
| 4.6 | [Multi-Agent Handoff](06-multi-agent-handoff.md) | 3 |
| 4.7 | [Guardrails and Safety](07-guardrails-and-safety.md) | 1 |
| 4.8 | [Putting It All Together](08-putting-it-all-together.md) | 2 |
| 4.9 | [Demo: Customer Support Agent](09-demo-customer-support-agent.md) | 6 |
| 4.10 | [Summary](10-summary.md) |  |

## Key Concepts Introduced

- **Responses API** — OpenAI's stateful API for agents with function calling and built-in tools; OCI offers an OpenAI-compatible version. ([4.2](02-openai-responses-api.md))
- **Agents SDK** — OpenAI's Python framework on top of the Responses API for agents, handoffs, guardrails and tracing. ([4.3](03-openai-agents-sdk.md))
- **Runner** — The Agents SDK component that runs the agent loop (`Runner.run` / `run_sync`). ([4.3](03-openai-agents-sdk.md))
- **Handoff** — Transferring control from one agent to a more specialised agent in a multi-agent system. ([4.6](06-multi-agent-handoff.md))
- **Tracing** — Recording each model call, tool call and handoff for debugging and observability. ([4.3](03-openai-agents-sdk.md))

---

⬅️ [Module 3: Introduction to MCP](../03-model-context-protocol/README.md) | [Module 5: Agentic AI for OCI Enterprise AI](../05-oci-enterprise-ai-agents/README.md) ➡️
