[🏠 Home](../README.md) › [Module 2: LangChain for AI Agents](README.md) › 2.6

# 2.6 LangChain Agents Under the Hood (Part 1)

## Core Concept: agent.invoke Under the Hood

- **The Loop**: While `agent.invoke` appears as a single line of code, it initiates a full multi-step communication loop between your code, LangChain, and the LLM.

- **Demonstration Problem**: *"What is 15 multiplied by 8 then divided by 3?"*

## Step-by-Step Execution Flow

## Step 1: User Runs the Python Code

- **Action**: The user runs a Python script calling the `run_agent` function with the math question.

- **Entry Point**: Inside `run_agent`, calling `agent.invoke` serves as the formal entry point into the LangChain agent loop.

- **Chain of Control**:

  - User → Your Code → LangChain → Model API.

  - The user **never** directly communicates with the LLM.

- **Why Separation Matters**: Keeps your application in absolute control over which tools are available, how results are formatted, and what the LLM can and cannot do.

## Step 2: LangChain Calls the Model API

- **Initial Payload Sent**: LangChain transmits two distinct elements to the model API:

  1. **Message Array**: The conversation history so far (currently just the initial user question).

  2. **Tools Array**: A JSON schema describing every tool the model is permitted to call, including function names, descriptions, and parameter schemas (argument names, types, and required fields).

- **Schema Generation**: LangChain automatically builds this JSON schema by inspecting your tool-decorated Python functions (reading function signatures, type hints, and docstrings).

- **Purpose**: Acts as an instruction "toolbox" the model evaluates to decide which tool to call and what arguments to pass.

## Step 3: Model Returns a Structured Tool Call Request

- **Reasoning**: The model reads the question, checks its toolbox, and determines it must solve 15 × 8 first.

- **Execution Limitation**: The model cannot execute Python code itself.

- **Output**: Instead of a final text answer, it returns a **structured tool call request** object (following the OpenAI-compatible function calling API specification):

  - content: Empty (no final text answer yet, as computation is incomplete).

  - tool name: multiply

  - arguments: A JSON string representing {"a": 15, "b": 8} that your application must parse.

  - id: `call_001` (a crucial identifier linking this specific request to the eventual result).

## Step 4: LangChain Parses the Response & Maps to Code

- **Framework Interception**: LangChain reads the response, notes the empty content field and the presence of a tool call request, and extracts three items: the tool name (multiply), the arguments (A=15, B=8), and the call ID (`call_001`).

- **The Bridge (Tool Registry)**: Because the model only outputs text strings (e.g., "multiply"), LangChain uses an internal registry—a Python dictionary automatically built during agent creation—to map string names to actual Python function references (`tool_registry`\["multiply"\]).

- **Framework Value**: LangChain automates the parsing and dictionary lookup, eliminating the need to write boilerplate parsing logic manually.

## Step 5: Real Code Execution

- **Crossing the Boundary**: The architecture transitions from text/JSON model reasoning to real code execution on your machine.

- **Execution**: LangChain calls the Python multiply function with parameters 15 and 8.

- **Result**: The normal Python function executes without AI involvement and returns the value 120.

- **Enterprise Context**: While this math example is trivial, the exact same architectural pattern governs complex enterprise tasks (querying production databases, calling APIs, sending emails, creating tickets, or provisioning cloud resources).

## Step 6: Updating Stateless History & Continuing the Loop

- **Payload Update**: To send the result back to the LLM, LangChain transmits the *entire* updated conversation history containing three entries:

  1. The original user message.

  2. The assistant's tool call request (`call_001`).

  3. The new tool response message with a role of tool (not user or assistant), containing the result 120 and tagged with `call_001` to link it to the original request.

- **Why Full Context is Resent**: LLMs are **stateless** and do not remember previous API calls; every single request must include the complete conversation history so the model knows the tool ran and produced 120.

- **Next Iteration**: Receiving the full context, the model continues reasoning and initiates tool request number 2 (division) in the next phase of the loop.

---

### 🔗 Related

- **LangChain** → [2.2 Introduction to LangChain](02-introduction-to-langchain.md)
- 📖 [Glossary](../glossary.md)

---

⬅️ [2.5 Demo: Your First LangChain Agent](05-demo-your-first-langchain-agent.md) | [⬆️ Module 2](README.md) | [2.7 LangChain Agents Under the Hood (Part 2)](07-langchain-agents-under-the-hood-part-2.md) ➡️
