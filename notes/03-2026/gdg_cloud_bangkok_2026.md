# GCG Cloud BKK 220326

## ChaiyoGCP Kick off

Cr: <https://www.youtube.com/live/0OFoRF2b1NE?si=12aBR6pXKXyevMa8>

### Getting Started with Google Antigravity

by Jirayut Nimsaeng

- vide code
  - planning
  - rules
    - e.g.
      - code generation guide
      - code style guide
  - skills (SKILL.md)
    - code review
    - unit code
    - QA
- developer is not disappeared but just turn ourself to AI developer, we need to grow faster like junior - meddle - senior within 1 year (difference from before)

### Evaluate ADK agent performance using the Vertex AI Generative AI Evaluation Service

by Rewat Airamaneerat

- AI agent is smart as context. AI agent -> MCP -> LLM
- A to A:
- context is the key point
- cost that make AI cannot replace dev
- AI read prompt from agent and list the set to evaluate (vertex AI)
- grading methodologies:
  - exact match (like rule base)
  - in-order match (check flow)
  - any order match
  - single tool use
  - prreision / recall
- response evaluation
  - semantic (meaning)
  - LLM as a judge
  - rag matric

## Build with AI

Cr. <https://www.youtube.com/live/p9WMHTTPdWk?si=q-aQGTrY9LfCBSpU>

### Vibe coding

by Saad Hamid

- think -> build -> publish

- AI studio (rapid prototype)
- Antigravity (agentic IDE)
- Gemini CLI (smart terminal)

- AI can build simple apps

- powerful prompt more than lazy prompt
  - give a role
  - define the goal
  - does it need AI?
  - create the vibe
  - optional: add a visual

### Best Practice to Design Agentic AI System in google ADK

by Joan Santoso

- Assistants vs Agents: moving from "Chatting" (Task oriented) to "Doing" (Goal-oriented)
- Buidingg an AI system isn't just about picking a smart model; it's about how you organize the pieces around it.
- Design Pattern
  - is the solution
  - is the blueprints
  - How the AI components are organized
  - How the AI connects to external tools (databases, search engines).
  - How we orchestrate the workflow (Does one AI do it alll? or multiple AIs work as a team?)
- 3 phases
  - Assessment
    - Task Compleity
    - performance
    - budget
    - human in the loop or not
  - Decision
    - Single-Agent Systems: One AI handling the task
    - Multi-Agent system: A ream of AIs coordinating together
  - Evolution
    - Not a One-time fix: this architecture is not set in stone
      - when to revise?
        - workload changes or grows
        - business requirements evolve
        - new AI capability are released
- ADK - allow us build multi agent like sub-agent
  - Multi-Agents
    - sequential pattern: can be set like pipeline like
      - sub agent #1 - doing task 1 and send to subagent #2
    - parallel pattern
    - loop Pattern -> not to loop to the subagent but loop to master one.
    - Review & Critique Pattern: if the main agent as generator and connect to subagent set as Critic review and response to user when the quality score meets requirements
    - coordinator pattern: dynamically routes request to the appropriate subagent
    - human in the loop: let the human be the back of your system when system generate a response send to the human reviewer to evaluation and approves before sent to user
  - State Management and callback in ADK
    - Session
    - output_key
    - callback can add safety
- the flow of design
  - Start simple: and evolve to multi agent if it's necessary
  - specialization - one clear purpose
  - tooling - agent as a tool
  - control - sequential Agent
  - safety first: for the sensitive case, always implement Human in the loop pattern

### Dynamic UIs with GenUI and Gemini

by Amorn Apichattanakul

- A2UI Protocol Library: to create Pre-defined components
  - Support: React, Aunglar Flutter, Lit
  - SwiftUI, Jetpack compose (Qq2 2026)
- Agnetic UI
  - makes that possible turning static screens into a Adaptive UX that is personalized, dynamic and a truly rich interactive with AI
