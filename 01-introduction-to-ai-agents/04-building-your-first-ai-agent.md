[🏠 Home](../README.md) › [Module 1: Introduction to AI Agents](README.md) › 1.4

# 1.4 Building Your First AI Agent

- Building an AI agent moves a large language model (LLM) from a passive text generator into an active, self-directed problem solver.

## 1. The Agent Framework Landscape

- Before writing code, it is important to select the right framework for the job. Frameworks reduce boilerplate code and handle the complex orchestration required as agent systems scale.

| **Framework**                                        | **Core Approach**                                                                              | **Best Suited For**                                                                | **Key Pros & Cons**                                                                                                                        |
|------------------------------------------------------|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **LangChain**                                        | Chains LLM calls together using standardized tool pipelines.                                   | Most standard production workflows and integrations.                               | • **Pros:** Huge ecosystem, extensive integrations, great documentation.<br>• **Cons:** Can feel overengineered for very simple tasks.     |
| **LangGraph**                                        | Adds stateful, graph-based workflows to LangChain.                                             | Complex production apps requiring state management, routing, and middleware.       | • **Pros:** Exceptional for complex control flows and loops.<br>• **Cons:** Higher learning curve due to advanced abstractions.            |
| **OpenAI Agents SDK**                                | Uses a lightweight, Python-first approach via the Responses API and native tool orchestration. | Python-first applications tightly integrated with OpenAI models and runtime loops. | • **Pros:** Less boilerplate code, built-in tracing/observability, guardrails.<br>• **Cons:** More opinionated design; evolving ecosystem. |
| **CrewAI** *(Not covered in depth)*                  | Multi-agent workflows structured around a collaborative "team" hierarchy.                      | Workflows that mirror human team dynamics and role delegation.                     | • **Pros:** Great for multi-agent delegation.<br>• **Cons:** Can introduce unnecessary overhead for single agents.                         |
| **Hugging Face** smolagents *(Not covered in depth)* | Minimalist framework where agents generate literal Python code to execute actions.             | Learning, experimentation, and code-centric reasoning tasks.                       | • **Pros:** Extremely lightweight, highly transparent reasoning.<br>• **Cons:** Smaller ecosystem compared to established frameworks.      |

- **Practical Guidance:** For learning purposes, start with simple examples to understand core mechanics. For production pipelines, frameworks like **LangChain**, **LangGraph**, and the **OpenAI Agents SDK** provide the robustness and ecosystem support required as complexity grows.

## 2. The Four-Step Build Process

- Creating a functional agent generally follows a straightforward four-step implementation blueprint:

- \[Step 1: Pick the Brain\] ➔ \[Step 2: Define the Tools\] ➔ \[Step 3: Create the Agent\] ➔ \[Step 4: Invoke the Agent\]

## Step 1: Pick the AI Brain

- Select your foundational Large Language Model (e.g., GPT-4o-mini, GPT-4o, or other provider models). This model acts as the reasoning engine that reads instructions, evaluates tool definitions, and drives the decision loop.

## Step 2: Define Tools (Real-World Actions)

- Tools give the LLM its "hands." In a simple example, these could be basic math functions (add, multiply, divide, square root). In a production system, these are API calls, database queries, or enterprise tool integrations.

- To convert Python code into something an LLM can understand, frameworks use **Python Essentials**:

- **The** `@tool` **Decorator:** Registers a standard Python function with the framework, giving it "special powers" so the AI can discover and execute it.

- **Type Hints:** Explicitly defining input and return types (e.g., a: float, b: float, -\> float) tells the framework how to structure data payloads correctly.

- **Docstrings:** Clear descriptions enclosed in triple quotes (""") inside the function. **This is not just documentation for humans; it is an instruction manual for the AI.** The LLM reads docstrings to determine *when* and *why* to invoke a specific tool.

- **JSON Schema Conversion:** Under the hood, the framework automatically converts your annotated Python functions into a structured **JSON Schema**. The LLM never reads your raw Python code—it reads this generated schema to decide how to act.

## Step 3: Create the Agent

- In modern frameworks, binding the model to the tools requires minimal code—often just a single line (e.g., calling `create_agent`(model, tools)). While the code footprint is small, this step constructs the entire backend **ReAct loop** (Reason → Act → Observe), enabling the model to dynamically call tools and self-correct based on outputs.

## Step 4: Invoke the Agent

- Run the agent by passing in a natural language query using an invocation method (e.g., .invoke({"input": "query"})). The agent takes over from there, managing its own execution loop.

## 3. The Agent in Action: From Simple to Chained Execution

- When an agent is invoked, its reasoning engine automatically determines the necessary execution paths without human intervention.

- Example 2 Flow: "15 \* 8 / 3"

- \[User Query\] ➔ \[Loop 1: Multiply(15,8) ➔ Output: 120\] ➔ \[Loop 2: Divide(120,3) ➔ Output: 40\] ➔ \[Final Answer: 40\]

- **Example 1: Single-Step Execution (Simple Addition)**

  - *Query:* "What is 42 plus 58?"

  - *Execution:* The agent reads the prompt, reasons that it needs the Add tool, executes it once, observes the result (100), and terminates the loop to return the answer.

- **Example 2: Chained Execution (Multiplication then Division)**

  - *Query:* "What is 15 times 8 divided by 3?"

  - *Execution:* The agent realizes it cannot answer in a single step.

    1. **Loop 1:** It calls Multiply(15, 8) and observes the output (120).

    2. **Loop 2:** It chains that output into the next step, calling Divide(120, 3) to observe the result (40).

    3. **Termination:** Having answered the full query, it halts the loop and outputs 40.

- **Example 3: Autonomous Strategy & Planning (Rectangle Area & Square Root)**

  - *Query:* "A rectangle has a width of 12 and height of 7. What is the square root of its area?"

  - *Execution:* Notice that *no tool exists for "area"*. The agent must reason independently:

    1. **Plan:** It deduces from general knowledge that Area = Width × Height.

    2. **Loop 1:** It maps this realization to the Multiply(12, 7) tool and observes the area (84).

    3. **Loop 2:** It feeds 84 into the SquareRoot(84) tool.

    4. **Termination:** It observes the result (≈ 9.165) and delivers the final answer.

- **Key Takeaway:** The power of an AI agent lies in its autonomy. You do not need to hardcode rigid, step-by-step workflows or define the sequence of tool execution. By combining well-documented **Tools** with a robust **ReAct Loop**, the agent autonomously reads the query, formulates a multi-step plan, chains tool outputs together, and solves complex problems on its own.

---

### 🔗 Related

- **AI Agent** → [1.1 What Is an AI Agent?](01-what-is-an-ai-agent.md)
- **Orchestration Layer** → [1.2 Agentic AI Core Components](02-agentic-ai-core-components.md)
- **ReAct** → [1.3 Reasoning Patterns](03-reasoning-patterns.md)
- **LangChain** → [2.2 Introduction to LangChain](../02-langchain-for-ai-agents/02-introduction-to-langchain.md)
- **LangGraph** → [2.4 Building Your First Agent with LangChain](../02-langchain-for-ai-agents/04-building-your-first-agent-with-langchain.md)
- **Chains / LCEL** → [2.3 Demo: LangChain Building Blocks](../02-langchain-for-ai-agents/03-demo-langchain-building-blocks.md)
- **Agents SDK** → [4.3 OpenAI Agents SDK](../04-openai-responses-api-agents-sdk/03-openai-agents-sdk.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [1.3 Reasoning Patterns](03-reasoning-patterns.md) | [⬆️ Module 1](README.md) | [1.5 Safety & Guardrails](05-safety-and-guardrails.md) ➡️
