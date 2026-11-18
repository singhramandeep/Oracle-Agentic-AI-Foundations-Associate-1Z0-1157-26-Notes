[🏠 Home](../README.md) › [Module 2: LangChain for AI Agents](README.md) › 2.4

# 2.4 Building Your First Agent with LangChain

## 1. Basic LLM vs. AI Agent

A core distinction in artificial intelligence is how data and execution flow are handled by the model. An AI agent transforms the large language model (LLM) from a passive responder into an active reasoning engine.

| **Feature**        | **Basic LLM Call**                                                        | **AI Agent**                                                               |
|--------------------|---------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Execution Flow** | One-shot (Input goes in → text comes out → done). | Dynamic loop (Iterates until a satisfactory answer is reached).            |
| **Control Flow**   | Defined entirely by the developer at every step.                          | **Decided by the LLM** (figures out which tools to use and in what order). |
| **Capabilities**   | Limited to generating text based on static training data.                 | Can call tools, inspect results, and decide if more data is needed.        |
| **State & Memory** | Stateless without manual intervention.                                    | Dynamically tracks context, reasoning, and tool observations.              |

**Core Definition:** An AI agent is a system where the LLM decides the control flow of the application.

## 2. Tools: Giving the LLM Hands

Tools turn a basic LLM into an actor that can interact with the real world (e.g., searching the web for current information, querying databases, running code, or calling APIs).

## Anatomy of a Tool & Python Essentials

In LangChain, tools are defined as standard Python functions enhanced with specific components that act as instructions for the AI:

- **The** `@tool` **Decorator:** Acts as a label or badge that registers and wraps the function so the agent framework can discover it as a callable tool. The underlying function itself does not change.

- **Type Hints:** Explicitly defines the expected data types for parameters (e.g., requiring two floating-point numbers). This allows the agent to read parameter requirements and construct valid tool calls, preventing broken execution.

- **Docstrings:** The triple-quoted string right after the function definition. **These are not just documentation for humans; they are direct instructions for the AI.** The LLM reads docstrings to determine when and how to use the tool. Clear descriptions lead to accurate tool selection; vague docstrings lead to wrong choices.

- **Return Type:** Defines what data format the tool sends back (e.g., outputting a floating-point number). This helps the LLM plan how to chain one tool's output directly into another tool's input.

## How Tool Calling Works (The JSON Schema Boundary)

The framework takes your Python code (decorator, type hints, docstring, and return type) and converts it into a **JSON Schema**.

This structured JSON Schema is sent to the LLM alongside the user's message.

1. **The LLM never sees your raw Python code.** It evaluates the JSON Schema to decide whether to call a tool.

2. **Separation of Concerns:** The LLM does not execute the tool directly. It generates a *tool call request*, and the LangChain runtime executes the actual code. This separation ensures system safety and controllability.

## 3. The ReAct Reasoning Pattern

1. **ReAct** stands for **Reasoning plus Acting**. It is the fundamental pattern driving LangChain agents through a continuous, self-correcting execution loop:

2. **Reason:** The agent thinks about the user prompt and decides what action or information it needs next.

3. **Act:** The agent executes a tool call request (e.g., calling a weather tool or a math function) or responds directly to the user.

4. **Observe:** The agent examines the tool's results and feeds that observation back into its context.

5. **Repeat:** It evaluates if it has enough information to provide a complete answer. If not, it loops back to Reason, Act, and Observe again (e.g., searching, calculating, and cross-referencing across multiple loops).

## 4. Step-by-Step Implementation: Building a ReAct Agent

A complete, working agent can be implemented in approximately 15 lines of code following a 4-step workflow:

## Step 1: Environment Setup & Model Initialization

- **Isolate Dependencies:** Set up a Python virtual environment.

- **Install Core Packages:**

  - langchain (core framework)

  - langchain-openai (provider integration for OpenAI models)

  - langgraph (provides the underlying agent runtime)

  - python-dotenv (securely loads environment variables)

- **Manage API Keys:** Save provider API keys (e.g., OpenAI API key) inside an environment file (`.env`) rather than hardcoding them in the codebase. *(Note: Providers can be swapped by installing the relevant integration package, such as* langchain-anthropic *for Claude).*

- **Initialize Model:** Call the initialization method (e.g., `init_chat_model`) and pass in the target model name.

## Step 2: Define Tools

Create the necessary standalone tools using simple Python functions. For example, creating a multiply tool and a divide tool. Each function must be wrapped in the `@tool` decorator and include explicit type hints and clear docstrings.

## Step 3: Create the Agent

Execute the single creation line that passes the initialized model and the defined tools (as a list or dictionary) into the framework. Under the hood, LangChain and LangGraph take the model and tools to construct the full backend ReAct reasoning loop.

## Step 4: Invoke the Agent

Run the agent using the .`invoke()` method by passing in a natural language query.

- *Example Query:* "What is 15 multiplied by 8 and divided by 3?"

- *Execution:* The agent autonomously reasons, calls the multiply tool (15 \* 8 = 120), observes the result, chains that output into the divide tool (120 / 3), observes the new result, and terminates the loop to return the final answer of **40**.

---

### 🔗 Related

- **AI Agent** → [1.1 What Is an AI Agent?](../01-introduction-to-ai-agents/01-what-is-an-ai-agent.md)
- **ReAct** → [1.3 Reasoning Patterns](../01-introduction-to-ai-agents/03-reasoning-patterns.md)
- **LangChain** → [2.2 Introduction to LangChain](02-introduction-to-langchain.md)
- **Chains / LCEL** → [2.3 Demo: LangChain Building Blocks](03-demo-langchain-building-blocks.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [2.3 Demo: LangChain Building Blocks](03-demo-langchain-building-blocks.md) | [⬆️ Module 2](README.md) | [2.5 Demo: Your First LangChain Agent](05-demo-your-first-langchain-agent.md) ➡️
