# Claude Platform — 101

Anthropic's infrastructure for building with Claude programmatically.

## Core Access Methods

- **REST API**
  - Primary endpoint: `messages.create`
  - Key parameters:
    - `model`: Which Claude model to use
    - `max_tokens`: Maximum length of response
    - `system`: System prompt to set persona and behavior
    - `messages`: Array of conversation messages

- **SDKs** (Node.js, Python, etc.)
  - Installation: `npm install @anthropic-ai/sdk`
  - Example usage:

    ```javascript
    import Anthropic from "@anthropic-ai/sdk";

    const client = new Anthropic();

    const buggyCode = `
    function add(a, b) {
      return a - b;
    }
    `;

    const response = await client.messages.create({
      model: "claude-opus-4-20250514",  // or claude-sonnet-4-20250514, claude-haiku-4-5-20251001
      max_tokens: 1024,
      system: "You are a terse senior code reviewer. Give feedback in one paragraph.",
      messages: [
        { role: "user", content: `Review this code:\n${buggyCode}` },
      ],
    });

    for (const block of response.content) {
      if (block.type === "text") {
        console.log(block.text);
      }
    }
    ```

- **Command Line Interfaces**
- **Web Console**

## Choosing the Right Model

- **Claude Opus** (Most capable)
  - Cost: Highest
  - Speed: Slowest
  - Best for: Deep reasoning, complex analysis, multi-step coding, nuanced writing, tasks benefiting from extended thinking
  - Use case: When accuracy and intelligence matter more than cost/speed

- **Claude Sonnet** (Balanced)
  - Cost: Medium
  - Speed: Fast
  - Best for: Most production work; balances intelligence, speed, and cost
  - Use case: Default choice for most applications

- **Claude Haiku** (Fast and efficient)
  - Cost: Lowest
  - Speed: Fastest
  - Best for: High-volume, low-complexity work like classification, extraction, routing, Q&A
  - Use case: When speed and cost efficiency are priorities

## Agents

An agent is software that can observe its environment, make decisions, and take actions to achieve goals. Agents use the Claude API in a loop: observe → decide → act → repeat.

- **Agent Loop**
  1. Send a message or task to Claude
  2. Claude responds (may request tool use)
  3. Execute the requested tool or action
  4. Return the result back to Claude
  5. Repeat until `stop_reason` is `end_turn`

- **Tools**: Functions you define and expose to agents
  - Agents can choose from multiple tools based on task needs
  - Examples: database queries, API calls, file operations, external service integrations

- **Built-in Tools** (available via Claude API)
  - Web search: Access current information from the internet
  - Code execution: Run code snippets and get results
  - Web fetch: Retrieve content from URLs

- **Extended Thinking**
  - Enables Claude to reason step-by-step before producing a final response (chain-of-thought reasoning)
  - Helps with: Math and multi-step logic, code debugging, regulatory analysis, trade-off analysis, option comparison
  - Available on Opus; configure thinking budget levels:
    - `low`: Quick reasoning
    - `medium`: Moderate depth
    - `high`: Default; deeper reasoning
    - `xhigh`: Extra high reasoning effort
    - `max`: Maximum reasoning

## Extending Your Agent

- **Skills**
  - Core component: `SKILL.md` file containing instructions and procedures
  - Purpose: Teach Claude a repeatable procedure or template for specific tasks
  - How to use:
    1. Create or upload a Skill
    2. Attach the Skill to a request
    3. Run the agent
  - Example: Custom workflows, specialized procedures, domain-specific templates

- **Model Context Protocol (MCP)**
  - Purpose: Connect Claude to third-party services (Slack, Asana, GitHub, etc.)
  - Difference from tools and skills:
    - **Tools**: Internal integrations (your database, your APIs, your systems)
    - **Skills**: Templates and procedures Claude learns to apply
    - **MCP**: External integrations (third-party services and platforms)

## Building a Managed Agent Experience

A fully managed, stateful agent platform consists of:

- **Agents**: Definitions with specific tools, personas, and capabilities
- **Sessions**: Individual runs triggered from your application
- **Environments**: Sandboxes with packages and network controls
- **Tools**: Custom tools that integrate with your backend
- **MCP**: Connections to third-party services
- **Memory**: Persistent storage the agent reads on startup and writes to on completion
- **Outcomes**: Rubrics and graders that define and measure success
- **Multi-agent Coordination**: Coordinators delegating tasks to specialist agents

### Minimal Managed Agent Setup

The simplest implementation requires five steps:

1. **Create the agent**: Define its capabilities, tools, and persona
2. **Create the environment**: Set up the sandbox with dependencies and controls
3. **Create the session**: Initialize a run instance
4. **Open stream and send kickoff**: Start the agent with an initial message
5. **Consume the stream**: Handle three main event types:
   - `agent.message`: Claude's text response
   - `agent.tool_use`: Claude requesting a specific tool
   - `session.status_idle`: Agent has completed the task

## Context Management

Managing context efficiently is critical for agent performance and cost:

- **Just-in-time Context**: Load only relevant information when needed
- **Server-side Compaction**: Automatically condense context when running low on tokens

  ```javascript
  context_management: {
    edits: [
      { type: "compact" }
    ]
  }
  ```

- **Prompt Caching**: Reuse cached prompts to reduce token costs
- **Memory Tool**: Persistent agent memory across sessions
- **Layered Patterns**: Combine multiple strategies (e.g., `lookup_building_code` pattern)

## Key Concepts Summary

| Concept | Purpose | When to Use |
|---------|---------|------------|
| Tools | Execute internal operations | Integrating with your systems |
| Skills | Teach procedures | Repeatable workflows and templates |
| MCP | Connect to external services | Third-party integrations |
| Extended Thinking | Deep reasoning | Complex analysis and problem-solving |
| Context Management | Optimize token usage | Long-running agents with memory |
| Sessions | Manage agent runs | Individual task execution |
| Memory | Persistent agent state | Cross-session information retention |
