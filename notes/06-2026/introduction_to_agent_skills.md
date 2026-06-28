# Introduction to agent skills - short

## skill

- reusable markdown files, you don't have to tell claude every time

- Personal skills go in `~/.claude/skills`
- Project skills go in `.claude/skills`

- `CLAUDE.md` files load into every conversation
  - Project-wide standards that always apply
  - Constraints like "never modify the database schema"
  - Framework preferences and coding style
- `Skills` load on demand when they match your request.
  - Task-specific expertise
  - Knowledge that's only relevant sometimes
  - Detailed procedures that would clutter every conversation
  - Add knowledge to your current conversation
  - `Slash commands` require you to explicitly type them. Skills don't.
- Use Subagents when:
  - You want to delegate a task to a separate execution context
  - You need different tool access than the main conversation
  - You want isolation between delegated work and your main context
- Use Hooks for:
  - Operations that should run on every file save
  - Validation before specific tool calls
  - Automated side effects of Claude's actions
- best for specialized knowledge that applies to specific tasks:
  - Code review standards your team follows
  - Commit message formats you prefer
  - Brand guidelines for your organization
  - Documentation templates for specific types of docs
  - Debugging checklists for particular frameworks
- In `SKILL.md`:
  - name (required) — Identifies your skill.
  - description (required) — Tells Claude when to use the skill.
  - allowed-tools (optional) — Restricts which tools Claude can use when the skill is active
  - model (optional) — Specifies which Claude model to use for the skill.
  - example:

      ```md
      ---
      name: codebase-onboarding
      description: Helps new developers understand the system works.
      allowed-tools: Read, Grep, Glob, Bash
      model: sonnet
      ---
      ```

- CLAUDE.md — always-on project standards
- Skills — task-specific expertise that loads on demand
- Hooks — automated operations triggered by events
- Subagents — isolated execution contexts for delegated work
- MCP servers — external tools and integrations
