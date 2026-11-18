[🏠 Home](../README.md) › [Module 1: Introduction to AI Agents](README.md) › 1.2

# 1.2 Agentic AI Core Components

Every AI agent, regardless of its complexity, is built upon **three foundational components**. Together, they transform a passive large language model into an active, real-world problem solver.

> **Agentic System = LLM (Brain) + Tools (Hands) + Orchestration Loop (Nervous System / OS)**

## 1. The LLM: The Brain & Reasoning Engine

The Large Language Model (LLM) sits at the center of the agent, acting as its cognitive core. It can consist of a single model or multiple models working together without requiring retraining for different tool configurations.

- **Core Responsibilities:**

  - Understands user intent from natural language.

  - Plans multi-step execution paths to achieve goals.

  - Decides which tools to call and what arguments to supply.

  - Interprets tool results and generates the final response.

- **The Selection Trade-Off:** Choosing an LLM requires balancing **Capability, Cost, and Latency**:

  - **Instruction Following:** The model must reliably adhere to structured system prompts that define its role, tools, and expected output formats.

  - **Context Window Size:** Larger context windows are preferred because agents rapidly accumulate data (thoughts, actions, and observations) with each iteration.

  - **Reasoning Ability:** High reasoning quality is essential for multi-step planning and utilizing strategies like *Chain-of-Thought* or *ReAct*.

  - **Cost & Optimization:** Because every loop iteration triggers an API call, many systems use a **two-tier approach**—routing simple tasks to cheaper, faster models while reserving advanced models for complex reasoning.

## 2. Tools: The Hands & Real-World Capabilities

Tools give the LLM agency. Without them, an LLM can only generate text; with them, it can execute actions, query databases, interact with APIs, and run code.

- **The Function Calling Lifecycle:**

  1. **Definition:** The agent shares available tools with the LLM as conceptual **JSON schemas** alongside the user prompt.

  2. **Decision:** The LLM evaluates the toolbox and decides whether to respond directly or generate a **structured tool call request** (e.g., calling a weather API with "city": "Paris").

  3. **Execution:** The agent validates the request, executes the external code/API, and returns the output to the LLM as an **observation**.

  4. **Iteration:** The LLM reviews the observation and decides whether to call another tool or formulate a final answer.

- **Critical Security Boundary:** **The LLM never executes code itself.** It only generates the structured request; the agent's underlying runtime environment handles the actual execution.

- **Model Context Protocol (MCP):** An emerging universal standard by Anthropic designed to standardize tool interfaces across different LLM providers.

## 3. The Loop: The Orchestration Layer & Operating System

Often referred to as the agent's **nervous system** or **operating system**, the orchestration layer is the application controller. While traditional software routes HTTP requests, an agentic loop routes reasoning steps and tool calls.

## Six Core Responsibilities of the Loop:

1. **Loop Management:** Controls the core execution cycle (Reason → Act → Observe), deciding when to continue, retry, pause, or terminate based on safety limits and goal completion.

2. **Reasoning Strategy:** Applies structured frameworks (like *ReAct* or *Chain-of-Thought*) to systematically break complex goals into manageable sub-tasks.

3. **Memory Management:** Maintains short-term working memory across ongoing interactions and retrieves long-term organizational knowledge when needed.

4. **Tool Routing:** Selects the appropriate tool for a step, formats valid requests, handles execution failures, and feeds results back into the reasoning cycle.

5. **State Machine Tracking:** Monitors the agent's progress through a task, identifying completion, repetition, or failure states to guide subsequent actions.

6. **Safety & Guardrails:** Enforces system-level rules and constraints that override model decisions to prevent unsafe, invalid, or unauthorized actions.

## Summary: The Three Pillars of Agentic AI

| **Component** | **Analogy**          | **Primary Function**                                             | **Key Consideration**                                               |
|---------------|----------------------|------------------------------------------------------------------|---------------------------------------------------------------------|
| **LLM**       | The Brain            | Intent understanding, planning, reasoning, and decision-making.  | Balancing capability against latency and API costs.                 |
| **Tools**     | The Hands            | Executing real-world actions (APIs, code, database queries).     | Maintains a strict security boundary (LLM requests; code executes). |
| **Loop**      | The Operating System | State tracking, memory, routing tools, and enforcing guardrails. | Where the primary engineering and orchestration complexity lives.   |

**Key Takeaway:** The secret sauce of Agentic AI lies in the **Orchestration Loop**. By dynamically connecting the reasoning power of the **LLM** with the execution capabilities of **Tools**, the loop creates an autonomous system capable of self-correction and complex problem-solving.

---

### 🔗 Related

- **ReAct** → [1.3 Reasoning Patterns](03-reasoning-patterns.md)
- **Guardrails** → [1.5 Safety & Guardrails](05-safety-and-guardrails.md)
- **Chains / LCEL** → [2.3 Demo: LangChain Building Blocks](../02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md)
- **Model Context Protocol (MCP)** → [3.2 What Is MCP?](../03-model-context-protocol/02-what-is-mcp.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [1.1 What Is an AI Agent?](01-what-is-an-ai-agent.md) | [⬆️ Module 1](README.md) | [1.3 Reasoning Patterns](03-reasoning-patterns.md) ➡️
