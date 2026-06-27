# AI Capabilities and Limitations

## Core Framework: Mapping Human Skills to AI Properties

| Human Competency | AI Property | What It Means | Capability | Limitation |
|---|---|---|---|---|
| **Delegation** | Steerability | How much control you have over AI behavior | Can adjust tone, style, approach with clear instructions | Can't always perfectly follow nuanced constraints |
| **Description** | Working Memory | What the AI is focusing on right now | Maintains context within a conversation | Context window has limits; attention degrades over very long conversations |
| **Discernment** | Next Token Prediction | Where AI answers actually come from | Predicts statistically likely continuations; patterns learned from training | Produces plausible-sounding answers even when uncertain or wrong |
| **Diligence** | Knowledge | What the AI actually knows | Trained on vast amounts of text; can retrieve and apply learned patterns | Has knowledge cutoff; can't access real-time info; may confuse similar concepts |

---

## Four Core Properties of Generative AI

### 1. Steerability

**Definition**: How much you can control what the AI does through prompting and configuration.

**What it enables**:

- Adjust tone (formal, casual, technical)
- Set behavior (ask questions, be concise, show step-by-step)
- Specify output format (JSON, bullet points, narrative)

**Limits**:

- Can't override fundamental model training
- Complex constraints sometimes conflict
- Personality isn't as flexible as you might want

---

### 2. Working Memory

**Definition**: What the AI is actively paying attention to in the current moment.

**What it enables**:

- Remembers recent conversation context
- Can reference earlier messages in same conversation
- Builds on previous reasoning

**Limits**:

- Context window has a token limit (200K for Opus)
- Attention quality degrades in very long conversations
- Early messages fade in importance over time
- Can't automatically recall conversations from previous sessions

---

### 3. Next Token Prediction

**Definition**: The core mechanism: AI predicts the statistically most likely next word/token based on training data and input.

**What it enables**:

- Generates fluent, coherent text
- Can complete patterns it learned during training
- Produces contextually relevant responses

**Limits**:

- Produces plausible-sounding wrong answers (hallucinations)
- Can't distinguish between confident knowledge and guesses
- Will "autocomplete" even when uncertain
- Drift accumulates over long conversations (keeps predicting next token without recalibration)

**Example**: "The capital of France is..." → AI predicts "Paris" (correct). But "The first person to walk on Mars was..." → AI might predict something plausible-sounding but false because it's extrapolating patterns, not retrieving fact.

---

### 4. Knowledge

**Definition**: What the AI actually learned during training.

**What it enables**:

- Understands concepts across many domains
- Can reason about patterns it learned
- Applies knowledge to new contexts (in-context learning)

**Limits**:

- Knowledge cutoff date (Claude's training data through January 2025)
- Can't access current events or real-time information
- May confuse similar concepts (rare things vs common things)
- May have gaps or biases from training data

---

## Two Training Stages

### Stage 1: Pre-training

- **What happens**: Model trained on massive amounts of publicly available text data (books, websites, code, etc.)
- **What it learns**: Patterns in language, concepts, reasoning, facts, writing styles
- **Result**: Raw predictive capability—can complete text given context
- **Not optimized for**: Safety, helpfulness, specific tasks

### Stage 2: Fine-tuning

- **What happens**: Model refined using curated feedback and RLHF (Reinforcement Learning from Human Feedback)
- **What it learns**: How to be helpful, safe, ethical, and aligned with human values
- **Result**: Claude becomes more useful, refuses harmful requests, is honest about limitations
- **Trade-off**: Sometimes more cautious or verbose than ideal

---

## Strong Points: What AI Does Well

✅ **Pattern recognition**: Identifies similarities, structures, and connections in text and data
✅ **Synthesis**: Combines information from multiple sources into coherent summaries
✅ **Generation**: Creates fluent, contextually relevant text
✅ **Speed and scale**: Processes vast information instantly
✅ **Explanation**: Can break down complex concepts in various ways
✅ **Consistency**: Applies rules uniformly without fatigue
✅ **Brainstorming**: Generates multiple ideas and perspectives quickly

---

## Weak Points: Where AI Struggles

❌ **Factual accuracy**: Hallucinates or confabulates when uncertain
❌ **Current events**: Can't access information after training cutoff
❌ **Rare or niche knowledge**: May not have seen enough examples
❌ **Common sense reasoning**: Sometimes misses obvious real-world constraints
❌ **Confidence calibration**: Can't reliably say "I'm not sure"
❌ **Real-time interaction**: Can't see what's on your screen or current system state
❌ **Ethical judgment**: Can apply rules but shouldn't replace human judgment on ethics

---

## The Capability-Limitation Intersection: Hallucinations

### How Hallucinations Happen

**Hallucinated Citation Example**:
> "According to research by Dr. Jane Smith at MIT (2022), AI exhibits properties X, Y, Z..."

This sounds authoritative because:

- **Capability**: AI learned to write in academic style from real citations
- **Limitation**: When uncertain, AI doesn't say "I don't know"—it pattern-completes with plausible-sounding details
- **Mechanism**: Next token prediction + knowledge gap = confident-sounding fabrication

**Why it happens**:

1. AI recognizes the pattern "citation format"
2. AI's training included many real citations
3. When asked to cite something in its knowledge gap, it predicts likely tokens
4. The result: Plausible but false

### The Zone Where This Occurs

| Confidence Level | What Happens |
|---|---|
| **High confidence + correct** | Solid answer ✅ |
| **High confidence + uncertain** | Hallucination ⚠️ |
| **Low confidence + uncertain** | Honest uncertainty 🤷 |
| **Very low confidence** | Usually refuses or hedges |

---

## Next Token Prediction Over Long Conversations

### The Drift Problem

**What happens**: As conversation extends, small prediction errors accumulate.

```
Turn 1:  "Analyze this document about solar energy"
         → Accurate analysis (fresh context)

Turn 5:  Building on earlier analysis...
         → Still mostly accurate

Turn 20: "Based on everything we discussed..."
         → Subtle drift—AI has made many predictions
            Errors compound; focus diffuses
            May contradict earlier accurate statements

Turn 50: "Let's continue from where we left off"
         → Significant drift possible
            May forget context priorities
            Reasoning becomes unfocused
```

**Why**:

- Each response is a new set of next-token predictions
- Predictions are probabilistic, not deterministic
- Small errors propagate forward
- Working memory (context) becomes diluted with accumulated conversation

**Mitigation**:

- Use `/compact` in Claude Code to summarize early conversation
- Refresh context periodically: "Here's what we've determined so far: X, Y, Z. Now let's focus on..."
- Keep important information in system prompt
- Don't rely on extremely long single conversations for accuracy

---

## Shadow Areas: Helpful BUT Problematic

AI's fine-tuning makes it helpful, but sometimes creates issues:

### 1. Sycophancy

- **What it is**: AI agrees with you even when you're wrong
- **Why**: Trained to be agreeable and not contradict
- **Problem**: You need honest feedback, not validation
- **Mitigation**: Explicitly ask "What could be wrong with this approach?" or "What would a critic say?"

### 2. Verbosity

- **What it is**: AI over-explains or adds unnecessary detail
- **Why**: Training emphasized thoroughness
- **Problem**: You asked for a summary, got a dissertation
- **Mitigation**: "Keep this to 2 sentences" or "Be as concise as possible"

### 3. Overcautiousness

- **What it is**: AI refuses requests that are actually harmless
- **Why**: Fine-tuning errs on side of safety
- **Problem**: False refusals slow down legitimate work
- **Mitigation**: Reframe request or explain the legitimate context

### 4. Loose Confidence Calibration

- **What it is**: AI seems equally confident about things it's sure of and things it's guessing
- **Why**: Next-token prediction doesn't distinguish confidence levels well
- **Problem**: You can't tell when to trust it
- **Mitigation**: Ask "How confident are you?" or "What's your source for this?" Force AI to show reasoning

---

## When Properties Collide: Key Interactions

### Collision 1: Steerability × Next Token Prediction

**The problem**: You steer the AI with instructions, but next-token prediction can override your intent.

**Example**:

- You: "Be concise. 1-2 sentences only."
- AI's training: "Thorough explanations are helpful"
- Result: AI might give 3 paragraphs because prediction weights learned patterns

**Resolution**: Be explicit about constraints. Use system prompt. Use temperature settings.

---

### Collision 2: Working Memory × Knowledge

**The problem**: AI might confuse what's in current conversation with what's in training.

**Example**:

- You mentioned "We work with customers X, Y, Z" (in conversation)
- AI treats this as established fact
- Later: "Your typical customers are X, Y, Z" (generalizing from one conversation to assumed pattern)

**Resolution**: Anchor important context repeatedly. Don't assume AI will remember context changes across conversations.

---

### Collision 3: Steerability × Knowledge

**The problem**: You can't steer AI to know things it wasn't trained on.

**Example**:

- "Act as an expert in proprietary algorithm X"
- AI can't actually know proprietary details; it will fabricate
- You steering with instructions doesn't solve the knowledge gap

**Resolution**: Provide the actual information in context, not just in persona instructions.

---

### Collision 4: Working Memory × Next Token Prediction

**The problem**: Long context → token prediction drift → accumulated errors.

**Example**: 50-turn conversation where small prediction errors compound into contradictions.

**Resolution**: Use context management (compaction, summaries, memory tool).

---

## Practical Application for Your Work

**When delegating to AI (using Delegation competency)**:

- Remember: Steerability has limits
- Structure requests clearly
- Don't rely on subtle hints

**When describing tasks (using Description competency)**:

- Be explicit about working memory scope
- Refresh context if conversation gets long
- Use system prompts for persistent instructions

**When evaluating outputs (using Discernment competency)**:

- Remember: Next token prediction ≠ knowledge
- Verify factual claims, especially citations
- Ask AI to show its reasoning

**When using responsibly (using Diligence competency)**:

- Understand knowledge limitations
- Don't rely on AI for current events without web search
- Don't trust confidence calibration—verify important facts
- Use AI as collaborative tool, not oracle

---

## Summary Table: What You Can and Can't Rely On

| Task Type | Reliable? | Why | Mitigation |
|---|---|---|---|
| Creative writing | ✅ | Steerability + generation | None needed |
| Coding | ✅ | Pattern matching, steerability | Test output |
| Summarization | ✅ | Synthesis capability | Verify key facts |
| Fact checking | ⚠️ | Knowledge gaps + hallucination | Always verify |
| Current events | ❌ | Knowledge cutoff | Use web search |
| Rare expertise | ❌ | Limited training data | Supplement with human expert |
| Confidence on dates/stats | ⚠️ | Loose calibration | Always source-check |
| Brainstorming | ✅ | Generation capability | Filter ideas yourself |

---
