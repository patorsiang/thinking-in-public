# Introduction to subagents - short

Subagents solve this by spinning up a separate context window. The subagent receives two things:

- A custom system prompt from your configuration file that defines the subagent's role and behavior
- A task description written by the parent agent based on what you asked for

- Built-in Subagents
  - General purpose subagent -- for multi-step tasks
  - Explore -- for fast searching and navigation of codebases
  - Plan -- used during plan mode for research and analysis of your codebase before presenting a plan
- Custom Subagents
  - Able to create your own subagents with custom system prompts and tool access. This lets you define specialized agents tailored to your workflow -- a code reviewer, a test writer, a documentation generator, or anything else you need.

  0. by using `/agent`
  1. the scope: Project-level or User-level
  2. Customizing Tools
  3. Choosing a Model and Color
  4. The Config File (`.claude/agents/your-agent-name.md`)

  - name -- A unique identifier for the subagent. This is how you reference it, either by asking Claude directly or by typing @agent code-quality-reviewer in your message.
  - description -- Controls when Claude decides to use the subagent. This must be a single line (use escaped newline characters \n if you need breaks). You can include example conversations here to help Claude understand when delegation is appropriate.
  - tools -- Lists which tools the subagent can access. This matches whatever you selected during generation, but you can edit the list here at any time.
  - model -- Specifies which Claude model to use: sonnet, opus, haiku, or inherit.
  - color -- The UI color for identifying the subagent.

- How Subagent Config Data Gets Used
  - Writing Descriptions That Shape Input Prompts
  - Defining an Output Format
  - Reporting Obstacles

- When subagents shine
  - Research tasks
  - Code Reviews
  - Custom System Prompts
- When Subagents Hurt
  - Expert Claims
  - Sequential Pipelines
  - Test Runners
- The Decision Rule
  - Use subagents for:
    - Research and exploration
    - Code reviews
    - Tasks that need a custom system prompt
  - Avoid subagents for:
    - "Expert" personas that don't add real capability
    - Multi-step pipelines where each step depends on the last
    - Running tests where you need full output for debugging
