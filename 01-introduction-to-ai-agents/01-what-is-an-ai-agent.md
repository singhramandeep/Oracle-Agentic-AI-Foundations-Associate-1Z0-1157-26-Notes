[🏠 Home](../README.md) › [Module 1: Introduction to AI Agents](README.md) › 1.1

# 1.1 What Is an AI Agent?

An **AI Agent** is a system that perceives its environment and acts within it. Unlike standard chatbots that passively answer questions, or fixed workflows that follow predefined sequences, an AI agent **thinks and decides its next steps dynamically**.

## 1. The Core Architecture

An LLM-based agent is not a new model; it is an **architectural pattern**. It wraps a Large Language Model inside a decision loop and equips it with external tools.

> **AI Agent = LLM (Brain) + Tools (Hands) + Loop (Nervous System)**

- **LLM (The Brain):** Provides the reasoning, language understanding, and decision-making capabilities.

- **Tools (The Hands):** Enables real-world interaction (e.g., calling APIs, querying databases, searching the web, executing code).

- **Loop (The Nervous System):** Keeps the iterative problem-solving process moving forward.

## 2. Four Key Properties of an AI Agent

- **Goal-Directed:** Actively works toward achieving a specific objective.

- **Autonomous:** Dynamically chooses the next steps without needing step-by-step human prompts.

- **Tool-Using:** Moves beyond text generation to interact with external systems and data sources.

- **Iterative:** Operates in a continuous evaluation and execution loop until the goal is met.

## 3. Standalone LLM vs. LLM-Based AI Agent

| **Feature**      | **Standalone LLM**                                                    | **LLM-Based AI Agent**                                                                |
|------------------|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| **Behavior**     | Passive responder; stateless.                                         | Active decision-maker; maintains state.                                               |
| **Memory**       | No memory between calls (unless manually passed).                     | Retains state across multiple iterations.                                             |
| **Action**       | Can only generate text.                                               | Can call tools and take real-world actions.                                           |
| **Verification** | Cannot easily self-correct or verify facts.                           | Observes tool results to self-correct.                                                |
| **Analogy**      | A brilliant person locked in an empty room with no internet or phone. | That same person at a desk with a computer, phone, reference books, and a to-do list. |

## 4. The Agent Execution Loop

Agents solve complex problems by mimicking human trial-and-error reasoning through a four-step cycle:

1. **Perceive:** Receives user input or observes new environment data.

2. **Reason:** The LLM evaluates the situation and selects the best next step (sometimes using "hidden reasoning").

3. **Act:** Executes an action, such as calling an external tool or responding to the user.

4. **Observe:** Reviews the result of the tool's output and feeds it back into the loop.

## Loop Termination & Risks

- **When does it stop?** The loop terminates when the agent reasons it has enough information to provide a final answer, or when it hits a safety limit (maximum number of iterations).

- **Associated Risks:** Because the loop runs multiple LLM API calls, it introduces **latency** (time delays) and **financial costs**. It also risks errors like hallucinated tool calls or infinite loops, making **orchestration and guardrails** essential.

## 5. Example in Action: Flight Booking

**User Query:** *"I want to book a flight from Austin to Zurich."*

- **Perceive:** Agent takes the user's destination and origin input.

- **Reason:** Determines it lacks live flight data and decides to use the flights tool.

- **Act:** Calls the flights tool with parameters: *Austin*, *Zurich*, and the requested date.

- **Observe:** Receives three flight options with prices from the tool.

- **Reason (Iteration 2):** Determines it now has sufficient information to answer the user; no further tools are needed.

- **Final Output:** Presents the available flights and prices clearly to the user.

**Key Takeaway:** You do not need to train a new model to build an AI agent. By wrapping a standard LLM inside an **iterative decision-making loop** with access to **external tools**, you transform a passive text generator into an active problem solver.

---

### 🔗 Related

- **Memory** → [2.3 Demo: LangChain Building Blocks](../02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ — | [⬆️ Module 1](README.md) | [1.2 Agentic AI Core Components](02-agentic-ai-core-components.md) ➡️
