---
title: "Vibe Coding & Agentic AI: Key Takeaways from ChaiyoGCP & Build with AI Bangkok 2026"
date: 2026-03-22
summary: "AI-assisted development, agentic systems, GenUI, and event reflections."
tags: [events, ai, genui]
maturity: published
lang: [en, th]
---

# Vibe Coding & Agentic AI: Key Takeaways from ChaiyoGCP & Build with AI Bangkok 2026

> How AI is reshaping developers — from writing code to designing intelligent systems

![Buit with AI](https://res.cloudinary.com/startup-grind/image/upload/c_fill,dpr_2.0,f_auto,g_center,h_1080,q_100,w_1080/v1/gcs/platform-data-goog/events/blob_o3IC4RX)

## <span lang="th">ก้าวข้ามขีดจำกัดการพัฒนาซอฟต์แวร์ด้วย AI Agent และ GenUI</span>

Attending two major tech events in a single day is exhausting but incredibly rewarding. On March 22, 2026, I had the chance to attend the **ChaiyoGCP Season 6 Kick-off** in the morning and **Build with AI Bangkok** in the afternoon.

<span lang="th">การเข้าร่วมงาน Tech 2 งานใหญ่ในวันเดียวอาจจะเหนื่อยหน่อย แต่สิ่งที่ได้รับคุ้มค่ามาก เมื่อวันที่ 22 มีนาคม 2026 ที่ผ่านมา ภัทรได้มีโอกาสเข้าร่วมงาน **ChaiyoGCP Season 6 Kick-off** ในช่วงเช้า และต่อด้วย **Build with AI Bangkok** ในช่วงบ่าย นี่คือสรุปประเด็นสำคัญที่ได้เก็บตกมาฝากกันค่ะ</span>

This post is not a full workshop recap, but rather a **curated highlight of key insights** that changed how I think about AI, development, and the future of software engineering

<span lang="th">บทความนี้ไม่ได้สรุป workshop ทั้งหมด แต่เป็น **insight สำคัญที่เปลี่ยนมุมมองของภัทรเกี่ยวกับ AI และการพัฒนา software**</span>

---

## 1. ChaiyoGCP Kick-off: The Rise of the AI Developer

### Getting Started with Google Antigravity

*By Jirayut Nimsaeng*

The idea of “vibe coding” was introduced — but not in a lazy way.

It’s about **structured AI-assisted development**, not just prompting randomly.

The concept of **"Vibe Coding"** isn't just about fun; it’s about structured planning.
<span lang="th">การทำ "Vibe Coding" ไม่ใช่แค่การเขียนโค้ดตามความรู้สึก แต่คือการวางแผนที่เป็นระบบ:</span>

- AI development still requires **engineering discipline**:
  - **Planning**
  - **Rules & Standards:** We need clear code generation and style guides.
  - **SKILL.md:** A new way to define skills for AI, including Code Review, Unit Testing, and QA.
  - **The AI Developer:** Developers aren't disappearing. Instead, we are evolving into "AI Developers" who must accelerate growth (Junior to Senior) within just one year.

> AI compresses the learning curve, but **only if you structure your workflow properly**

### Evaluating AI Agents with Vertex AI

*By Rewat Airamaneerat*

Context is king. If an agent lacks context, it fails.
<span lang="th">บริบท (Context) คือหัวใจสำคัญ หาก Agent ขาดบริบทที่ถูกต้อง ก็ไม่สามารถทำงานได้จริง:</span>

- **Agent Architecture:** AI Agent -> MCP (Model Context Protocol) -> LLM.
- **Evaluation is Key:** Using Vertex AI to grade agents via:
  - Matching strategies:
    - Exact match (rule-based)
    - In-order match (workflow validation)
    - Any-order match
    - Single-tool usage

  - Metrics:
    - Precision / Recall
    - Semantic evaluation (meaning-based)
    - LLM-as-a-judge
    - RAG metrics

> AI evaluation is becoming a **first-class engineering problem**, not just experimentation.

---

---

## 2. Build with AI: Moving from "Chatting" to "Doing"

### Vibe Coding & Rapid Prototyping

*By Saad Hamid*

The workflow has shifted: **Think -> Build -> Publish.**
<span lang="th">กระบวนการทำงานเปลี่ยนไปเป็น: **คิด -> สร้าง -> เผยแพร่**</span>

- **Tools:** Using AI Studio for prototypes, Antigravity for agentic IDEs, and Gemini CLI for terminal smarts.
- **Powerful Prompting:** Don't be lazy. Define roles, goals, and create a "vibe" to get the best results.
  - Good prompts outperform lazy prompts:
    - Assign a **role**
    - Define clear **goals**
    - **Decide** if AI is needed
    - Set the “vibe” (**context**)
    - Optional: include visuals

### Designing Agentic AI Systems in Google ADK

*By Joan Santoso*

We are moving from **Assistants** (Task-oriented) to **Agents** (Goal-oriented).
<span lang="th">เรากำลังเปลี่ยนจากผู้ช่วย (Assistant) ที่ทำตามสั่ง เป็น Agent ที่มุ่งเน้นผลลัพธ์ (Goal-oriented)</span>

- **Design Patterns:**
  - **Sequential:** Step-by-step pipeline.
  - **Parallel**
  - **Review & Critique:** One agent generates, another reviews.
  - **Coordinator** dynamic routing
  - **Human-in-the-loop:** Vital for sensitive cases; humans approve before the final response.
- **Evolution:** Start simple and evolve as workloads or AI capabilities grow

#### ADK Capabilities

- Multi-agent systems (sub-agents)
- State management
- Callback systems (e.g., safety checks)

#### Phases of AI System Design

1. **Assessment**
   - Task complexity
   - Performance needs
   - Budget
   - Human involvement

2. **Decision**
   - Single-agent vs Multi-agent

3. **Evolution**
   - Systems must adapt:
     - Workload changes
     - Business needs evolve
     - New AI capabilities emerge

> AI architecture is **never final — it evolves continuously**

### Dynamic UIs with GenUI and Gemini

*By Amorn Apichattanakul*

The future of UI is **Agentic UI**.
<span lang="th">อนาคตของ UI คือ "Agentic UI" หรือ UI ที่ปรับเปลี่ยนตามสถานการณ์</span>

- **A2UI Protocol:** Supports React, Angular, Flutter, and Lit (with SwiftUI/Jetpack Compose coming Q2 2026).
- Static screens are becoming **Adaptive UX**—personalized and dynamic interfaces generated in real-time by AI.

> Frontend is shifting from **designing screens → designing experiences powered by AI**

---

## Personal Reflection / มุมมองส่วนตัว

This day made one thing clear: **The barrier to building has dropped, but the bar for "Architectural Thinking" has risen.** In the past, we spent 80% of our time writing syntax. Now, AI handles the syntax, but we must spend that 80% on **System Design, Context Management, and Evaluation.** If you can "vibe" with the AI and guide it with the right architecture, you can build products at a speed that was impossible two years ago.

<span lang="th">สิ่งที่ภัทรเห็นได้ชัดจากทั้งสองงานคือ **"กำแพงในการสร้าง (Building) นั้นต่ำลง แต่มาตรฐานของการคิดเชิงสถาปัตยกรรม (Architectural Thinking) นั้นสูงขึ้น"**</span>

<span lang="th">ในอดีตเราอาจใช้เวลา 80% ไปกับการเขียน Syntax แต่ตอนนี้ AI จัดการตรงนั้นให้เราแล้ว เราจึงต้องเอา 80% นั้นมาใช้ในการ **ออกแบบระบบ, จัดการบริบท (Context), และการวัดผล (Evaluation)** แทน ถ้าคุณสามารถ "Vibe" ไปกับ AI และชี้นำมันด้วย Architecture ที่ถูกต้อง คุณจะสร้าง Product ได้เร็วในระดับที่เมื่อสองปีที่แล้วยังทำไม่ได้เลยค่ะ</span>

And honestly…

That’s both exciting and terrifying.

---

### Resources & Credits

- [ChaiyoGCP Season 6 Live Stream](https://www.youtube.com/live/0OFoRF2b1NE)

- [Build with AI Bangkok 2026 Live Stream](https://www.youtube.com/live/p9WMHTTPdWk)

---

tags:

- GDGCloudBKK
- ChaiyoGCP
- BuildWithAI
- GoogleCloud
- GenAI
- VibeCoding

---

Written by Pat (Napatchol) | Full-Stack Developer
