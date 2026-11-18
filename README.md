# Agentic AI Foundations — Study Notes

Personal study notes for **Oracle Agentic AI Foundations Associate (1Z0-1157-26)**, based on the [Oracle Agentic AI Foundations (2026)](https://mylearn.oracle.com/ou/course/oracle-agentic-ai-foundations-2026/163240/271885) course on Oracle MyLearn.

## How these notes are organised

- Each **module** has its own folder with a `README.md` overview and one file per lesson.
- Every lesson has breadcrumbs at the top, **Previous / Next** links at the bottom, and a **Related** list that links concepts to the lesson where they are explained.
- The [Glossary](glossary.md) collects the key terms with links back to their lessons.
- Figures and slide captures live in [`assets/images`](assets/images).

## Modules

### [Module 1: Introduction to AI Agents](01-introduction-to-ai-agents/README.md)

What an AI agent is, its core components, reasoning patterns, a first hand-built agent, and safety guardrails.

- [1.1 What Is an AI Agent?](01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- [1.2 Agentic AI Core Components](01-introduction-to-ai-agents/02-agentic-ai-core-components.md)
- [1.3 Reasoning Patterns](01-introduction-to-ai-agents/03-reasoning-patterns.md)
- [1.4 Building Your First AI Agent](01-introduction-to-ai-agents/04-building-your-first-ai-agent.md)
- [1.5 Safety & Guardrails](01-introduction-to-ai-agents/05-safety-and-guardrails.md)
- [1.6 Summary](01-introduction-to-ai-agents/06-summary.md)

### [Module 2: LangChain for AI Agents](02-langchain-for-ai-agents/README.md)

LangChain building blocks (models, prompts, chains, memory), building agents with `create_agent`, and what happens under the hood.

- [2.1 Module Introduction](02-langchain-for-ai-agents/01-module-introduction.md)
- [2.2 Introduction to LangChain](02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- [2.3 Demo: LangChain Building Blocks](02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md)
- [2.4 Building Your First Agent with LangChain](02-langchain-for-ai-agents/04-building-your-first-agent-with-langchain.md)
- [2.5 Demo: Your First LangChain Agent](02-langchain-for-ai-agents/05-demo-your-first-langchain-agent.md)
- [2.6 LangChain Agents Under the Hood (Part 1)](02-langchain-for-ai-agents/06-langchain-agents-under-the-hood-part-1.md)
- [2.7 LangChain Agents Under the Hood (Part 2)](02-langchain-for-ai-agents/07-langchain-agents-under-the-hood-part-2.md)
- [2.8 Summary](02-langchain-for-ai-agents/08-summary.md)

### [Module 3: Introduction to MCP](03-model-context-protocol/README.md)

The Model Context Protocol: architecture, core concepts, wiring MCP servers into agents, and a real-world walkthrough.

- [3.1 Module Introduction](03-model-context-protocol/01-module-introduction.md)
- [3.2 What Is MCP?](03-model-context-protocol/02-what-is-mcp.md)
- [3.3 Core MCP Concepts](03-model-context-protocol/03-core-mcp-concepts.md)
- [3.4 Add an MCP Server to Your First Agent](03-model-context-protocol/04-add-an-mcp-server-to-your-first-agent.md)
- [3.5 Demo: MCP Server with LangChain Clients and Codex](03-model-context-protocol/05-demo-mcp-server-with-langchain-clients-and-codex.md)
- [3.6 Real-World MCP Walkthrough](03-model-context-protocol/06-real-world-mcp-walkthrough.md)
- [3.7 Summary](03-model-context-protocol/07-summary.md)

### [Module 4: OpenAI Responses API & Agents SDK Basics](04-openai-responses-api-agents-sdk/README.md)

The OpenAI agent stack: Responses API, Agents SDK, tools, multi-agent handoffs, guardrails, and a customer support agent demo.

- [4.1 OpenAI Agent Stack](04-openai-responses-api-agents-sdk/01-openai-agent-stack.md)
- [4.2 OpenAI Responses API](04-openai-responses-api-agents-sdk/02-openai-responses-api.md)
- [4.3 OpenAI Agents SDK](04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md)
- [4.4 Demo: Responses API and Agents SDK](04-openai-responses-api-agents-sdk/04-demo-responses-api-and-agents-sdk.md)
- [4.5 Tools & Function Calling](04-openai-responses-api-agents-sdk/05-tools-and-function-calling.md)
- [4.6 Multi-Agent Handoff](04-openai-responses-api-agents-sdk/06-multi-agent-handoff.md)
- [4.7 Guardrails and Safety](04-openai-responses-api-agents-sdk/07-guardrails-and-safety.md)
- [4.8 Putting It All Together](04-openai-responses-api-agents-sdk/08-putting-it-all-together.md)
- [4.9 Demo: Customer Support Agent](04-openai-responses-api-agents-sdk/09-demo-customer-support-agent.md)
- [4.10 Summary](04-openai-responses-api-agents-sdk/10-summary.md)

### [Module 5: Agentic AI for OCI Enterprise AI](05-oci-enterprise-ai-agents/README.md)

Running agents in production on OCI: lifecycle and runtime needs, the OCI Enterprise AI platform, building blocks, and deployment models.

- [5.1 Module Introduction](05-oci-enterprise-ai-agents/01-module-introduction.md)
- [5.2 Need for Agent Lifecycle and Runtime](05-oci-enterprise-ai-agents/02-need-for-agent-lifecycle-and-runtime.md)
- [5.3 Introduction to OCI Enterprise AI Platform](05-oci-enterprise-ai-agents/03-introduction-to-oci-enterprise-ai-platform.md)
- [5.4 Agentic AI for Enterprises](05-oci-enterprise-ai-agents/04-agentic-ai-for-enterprises.md)
- [5.5 OCI Enterprise AI Agents Building Blocks](05-oci-enterprise-ai-agents/05-oci-enterprise-ai-agents-building-blocks.md)
- [5.6 Demo: OCI Enterprise AI Agents Setup](05-oci-enterprise-ai-agents/06-demo-oci-enterprise-ai-agents-setup.md)
- [5.7 OCI Enterprise AI Agents: Deploy & Scale](05-oci-enterprise-ai-agents/07-oci-enterprise-ai-agents-deploy-and-scale.md)
- [5.8 Summary](05-oci-enterprise-ai-agents/08-summary.md)

### [Module 6: Agentic AI for Oracle AI Database](06-oracle-ai-database-agentic-ai/README.md)

Agentic AI inside Oracle AI Database: AI Vector Search, Private Agent Factory, and the Autonomous AI Database MCP Server.

- [6.1 Agentic AI for Oracle AI Database](06-oracle-ai-database-agentic-ai/01-agentic-ai-for-oracle-ai-database.md)
- [6.2 Introduction to Oracle AI Vector Search](06-oracle-ai-database-agentic-ai/02-introduction-to-oracle-ai-vector-search.md)
- [6.3 Oracle AI Vector Search Workflow](06-oracle-ai-database-agentic-ai/03-oracle-ai-vector-search-workflow.md)
- [6.4 Demo: Oracle AI Vector Search](06-oracle-ai-database-agentic-ai/04-demo-oracle-ai-vector-search.md)
- [6.5 Oracle AI Database Private Agent Factory](06-oracle-ai-database-agentic-ai/05-oracle-ai-database-private-agent-factory.md)
- [6.6 Demo: Private Agent Factory](06-oracle-ai-database-agentic-ai/06-demo-private-agent-factory.md)
- [6.7 Oracle Autonomous AI Database MCP Server](06-oracle-ai-database-agentic-ai/07-oracle-autonomous-ai-database-mcp-server.md)

## Quick Links

- 📖 [Glossary](glossary.md)
- 🚀 Start here: [1.1 What Is an AI Agent?](01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)

---

*Unofficial personal notes for exam preparation; not affiliated with or endorsed by Oracle.*
