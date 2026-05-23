# Claude Code in Action — Short Note

- What is a coding assistant?
  - ![How it work](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1750967940%2F002_-_What_is_a_Coding_Assistant%3F_02.1750967940100.png)
    1. Gather context - Understanding what the error refers to, which part of the codebase is affected, and what files are relevant
    2. Formulate a plan - Deciding how to solve the issue, such as changing code and running tests to verify the fix
    3. Take action - Actually implementing the solution by updating files and running commands
  - User -> assistant -> LLM

    ```mermaid
    sequenceDiagram
    actor User as You
    participant Assistant
    participant LLM

    User->>Assistant: What code is written in main.go file?
    Assistant->>LLM: What code is written in main.go file? If you want to read a file, response with "ReadFile: name of file"
    LLM->>Assistant: ReadFile: main.go
    Assistant->>LLM: <Content of main.go file>
    LLM->>User: <response>
    ```

  - Coding assistants use language models to complete different tasks
  - Not all language models use tools with the same skill level
- Working with it as a partner
  - Tools/Commands

    | Name          | Purpose                                 |
    |---------------|-----------------------------------------|
    | Agent         | Launch a subagent to handle a task      |
    | Bash          | Run a shell command                     |
    | Edit          | Edit a file                             |
    | Glob          | Find files based upon a pattern         |
    | Grep          | Search the contents of a file           |
    | LS            | List files and directories              |
    | MultiEdit     | Make several edits at the same time     |
    | NotebookEdit  | Write to a cell in a Jupyter notebook   |
    | NotebookRead  | Read a cell                             |
    | Read          | Read a file                             |
    | TodoRead      | Read one of the created to-do's         |
    | TodoWrite     | Update the list of to-do's              |
    | WebFetch      | Fetch from a URL                        |
    | WebSearch     | Search the web                          |
    | Write         | Write to a file                         |

  - start with `/init` to set up persistent memory files
    - `CLAUDE.md`: project-specific persistent memory (can be shared with team)
    - `CLAUDE.local.md`: local customizations (not shared)
    - `~/.claude/CLAUDE.md`: global settings used across all projects on your machine
  - controlling context:
    - `/compact`: when the task is not finished but you have less remaining context space
    - `/clear`: when the task is complete and you're moving to a new, unrelated task
  - custom commands:
    - `.claude/commands/<cmd>.md`: define goal and steps for custom commands
      - Example use cases: audit, write_tests
  - MCP server: `claude mcp add <server_name>`
  - Hooks
    - Tools that run before or after specific events in Claude Code
    - Configuration: set up in `~/.claude/settings.json` or `~/.claude/settings.local.json`
    - Available hook events:
      - PreToolUse — runs before a tool call
      - PostToolUse — runs after a tool call completes
      - UserPromptSubmit — runs when the user submits a prompt, before Claude processes it
      - SessionStart — runs when starting or resuming a session
      - SessionEnd — runs when a session ends
      - PreCompact — runs before a compact operation occurs (manual or automatic)
      - Stop — runs when Claude Code has finished responding
      - SubagentStop — runs when a subagent has finished
      - Notification — runs when Claude sends a notification (e.g., when Claude needs permission or after idle timeout)
    - Practical Applications
      - Code formatting — automatically format files after Claude edits them
      - Testing — run tests automatically when files are changed
      - Access control — block Claude from reading or editing specific files
      - Code quality — run linters or type checkers and provide feedback to Claude
      - Logging — track what files Claude accesses or modifies
      - Validation — check naming conventions or coding standards
    - Implementation: hooks are implemented using JavaScript
    - To begin setting up hooks: `npm run setup`
