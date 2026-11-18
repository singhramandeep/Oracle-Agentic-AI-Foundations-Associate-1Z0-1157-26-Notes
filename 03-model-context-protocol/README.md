[🏠 Home](../README.md) › Module 3

# Module 3: Introduction to MCP

The Model Context Protocol: architecture, core concepts, wiring MCP servers into agents, and a real-world walkthrough.

## Lessons

| # | Lesson | Figures |
|---|---|---|
| 3.1 | [Module Introduction](01-module-introduction.md) |  |
| 3.2 | [What Is MCP?](02-what-is-mcp.md) |  |
| 3.3 | [Core MCP Concepts](03-core-mcp-concepts.md) |  |
| 3.4 | [Add an MCP Server to Your First Agent](04-add-an-mcp-server-to-your-first-agent.md) | 1 |
| 3.5 | [Demo: MCP Server with LangChain Clients and Codex](05-demo-mcp-server-with-langchain-clients-and-codex.md) |  |
| 3.6 | [Real-World MCP Walkthrough](06-real-world-mcp-walkthrough.md) |  |
| 3.7 | [Summary](07-summary.md) |  |

## Key Concepts Introduced

- **Model Context Protocol (MCP)** — An open standard for connecting AI applications to tools and data through a common client–server protocol. ([3.2](02-what-is-mcp.md))
- **MCP Host / Client / Server** — The host app embeds MCP clients, each holding a 1:1 connection to a server that exposes capabilities. ([3.3](03-core-mcp-concepts.md))
- **MCP Primitives** — What a server exposes: tools (actions), resources (data) and prompts (templates). ([3.3](03-core-mcp-concepts.md))
- **Transports (stdio / Streamable HTTP)** — How MCP messages travel: stdio for local servers, Streamable HTTP for remote ones. ([3.3](03-core-mcp-concepts.md))

---

⬅️ [Module 2: LangChain for AI Agents](../02-langchain-for-ai-agents/README.md) | [Module 4: OpenAI Responses API & Agents SDK Basics](../04-openai-responses-api-agents-sdk/README.md) ➡️
