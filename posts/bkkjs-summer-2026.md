# Insights from BKK.js Summer 2026

![BKK.js Summer 2026](https://creatorsgarten.org/cdn-cgi/image/width=360,height=360,fit=crop,format=webp,quality=85/https://usercontent.creatorsgarten.org/c/v1774442419/644c35a6802c02345887f156/image_jri94k.webp)

**Original Content Reference:** [Facebook Live @ BKK.js](https://www.facebook.com/share/v/1DLp4BWZfj)

The tech scene in Bangkok is heating up! I recently attended **BKK.js Summer 2026** and captured some high-level highlights from the speakers. From the complexities of high-performance web gaming to the new era of AI-driven "Vibe Coding," here is what you missed.

> จากงาน BKK.js Summer 2026: สิ่งที่ฉันได้เรียนรู้เกี่ยวกับ AI, Web, และอนาคตของนักพัฒนา

---

## 1. Game Engines on the Web: How Hard Could It Be?

**Speaker:** Phoomparin Mano

Building a game engine in JavaScript is a challenge because JS is traditionally single-threaded and relies on `async/await`, whereas games require heavy parallel processing.
การสร้าง Game Engine บน JS นั้นท้าทายมาก เพราะปกติ JS จะรอประมวลผลทีละขั้นตอน (Async/Await) แต่ Game Engine ต้องทำงานแบบขนาน (Parallel)

- **Parallelism & Performance:** To avoid blocking the main thread, we must move heavy tasks to **Web Workers** and use **WebAssembly (Wasm)** for near-native speed.
    ย้ายงานหนักๆ ไปไว้ที่ Web Workers และใช้ WebAssembly เพื่อความเร็วระดับ Native
- **The Rendering Pipeline:** Use **DAG (Directed Acyclic Graph)** combined with **Topological Sort** to create an efficient render graph.
    ใช้ DAG และ Toposort ในการจัดการลำดับการ Render
- **Offscreen Canvas:** Utilizing `OffscreenCanvas` with `WebGL2Context` allows rendering to happen outside the main thread.
    ใช้ OffscreenCanvas เพื่อให้การวาดภาพไม่ไปกวนการทำงานหลักของเบราว์เซอร์
- **Optimization:** Solve synchronization bottlenecks with **PBO (Pixel Buffer Objects)** and `fenceSync` for asynchronous pixel reading.
    แก้ปัญหาคอขวดด้วย PBO และ `fenceSync` เพื่อการอ่านข้อมูล Pixel แบบ Async

---

## 2. WebMCP: The Bridge Between Frontend & AI

**Speaker:** Warat Wongmanneekit

The Model Context Protocol (MCP) is changing how frontends interact with AI.
WebMCP กำลังเปลี่ยนวิธีที่ Frontend คุยกับ AI

- **Direct Interaction:** Frontends can now provide specialized JavaScript tools for AI to call directly.
    Frontend สามารถเตรียมชุดคำสั่งให้ AI เรียกใช้งานได้โดยตรง
- **On-Device vs. Cloud:** We are seeing a shift towards integrating Cloud AI with **On-Device AI** for specialized, local tasks.
    การผสมผสานระหว่าง AI บนคลาวด์และ AI บนเครื่องเพื่อทำงานเฉพาะทาง
- **Structural Future:** While MCP is currently "messy," the goal is to make it more structured so developers can implement AI capabilities without needing deep AI expertise.
    อนาคตของ MCP จะมีโครงสร้างที่ชัดเจนขึ้น ทำให้ Dev ทั่วไปนำไปใช้ได้ง่ายโดยไม่ต้องเป็นผู้เชี่ยวชาญ AI

---

## 3. Vibe Coding Without Leaving Tech Debt

**Speaker:** Thada Wangthammang

"Vibe Coding" (coding entirely via AI prompts) can reduce a 3-month project to 3 weeks, but it often leaves behind massive technical debt.
"Vibe Coding" หรือการเขียนโค้ดตาม "Vibe" ผ่าน AI อาจช่วยย่อเวลาจาก 3 เดือนเหลือ 3 สัปดาห์ แต่ก็มักจะทิ้ง Tech Debt กองโตไว้

- **The Trap:** AI often ignores architecture, design patterns, and documentation, leading to "Strategic Fatigue" for humans who must constantly make prompting decisions.
    AI มักข้ามเรื่อง Architecture และ Document ทำให้คนจูนต้องเหนื่อยกับการตัดสินใจ (Strategic Fatigue)
  - Why Tech Debt Happens
    - Technical Problems
      - No architecture
      - No design patterns
      - No documentation
      - Context overload
    - Mindset Problems
      - Rushing decisions
      - Poor prompt quality
      - “Refactor later” thinking

> Bad prompt = bad architecture

- **The Solution: The Rule-Human-AI Triangle:**
  - **Rules (System > Human)**
    - **Define:**
      - Spec
      - Context
      - Goal
      - Validation
    - **Use templates:**
      - Project scaffolding
      - Design patterns
      - Type safety rules

    Example: Set strict templates (like [`thaitype-stack`](https://github.com/thaitype/thaitype-stack-mongodb-template)). 

    one topic in his [design patterns](https://github.com/thaitype/thaitype-stack-mongodb-template/blob/main/docs/DESIGN_PATTERNS.md) is about define clear boundaries for type-safety using **Zod** or **TypeBox**.

  - **Human:** Move decisions out of your head. Use frameworks like **[Chief Agent Framework](https://github.com/thaitype/chief-agent-framework)** to let agents review code or suggest specs.
        เอาการตัดสินใจออกจากหัว ใช้ Agent ช่วยรีวิวโค้ดและเสนอแนะ
  - **Checking:** Automated checks (Lint, Unit Tests, Format) are non-negotiable to ensure AI output stays high-quality.
        ต้องมีระบบตรวจอัตโนมัติ (Lint, Test) เพื่อคุมคุณภาพโค้ดจาก AI
    - example of skill: [Grill-me-Skill](https://github.com/mattpocock/skills/blob/main/grill-me/SKILL.md)

> AI doesn’t reduce responsibility
> It **amplifies your decisions**

-> If your system is weak → AI makes it worse
-> If your system is strong → AI makes you 10x faster

---

## 4. Reliable Event-Driven Apps (Without the Bloat)

**Speaker:** Dheerapat Tookkane

You don't always need Kafka or RabbitMQ. For low-to-medium traffic, **Postgres** is enough.
ไม่จำเป็นต้องใช้ Kafka เสมอไป สำหรับ Traffic ระดับกลาง Postgres ก็เอาอยู่

- **The Tech Stack:** Bun + TypeScript + Postgres (via **pg-boss**).
- **The Secret Sauce:** Use `SELECT ... FOR UPDATE SKIP LOCKED` to handle workers without race conditions.
    ใช้คำสั่ง `SKIP LOCKED` เพื่อให้ Worker หลายตัวทำงานพร้อมกันได้โดยไม่แย่งงานกัน
- **Pros:** Low complexity, transactional consistency out of the box, and low operational costs.
    ข้อดีคือซับซ้อนน้อย คุม Data ง่าย และประหยัดค่าดูแล (Ops cost)
- **Cons:** Not suitable for extreme high-throughput or complex polyglot environments.
    ข้อเสียคือไม่เหมาะกับงานที่ต้องการความเร็วสูงมากๆ (High-throughput)

---

## 5. Fully Type-Safe: Server to Client

**Speaker:** Kongkeit Khynpanitchot

Achieving end-to-end type safety is the holy grail of modern web development.
การทำให้ Type ปลอดภัยตั้งแต่ Server ถึง Client คือหัวใจของยุคนี้

- **Beyond tRPC:** While tRPC is great, newer frameworks like **Elysia** offer faster type inference and easier API documentation.
    นอกจาก tRPC แล้ว ยังมี Elysia ที่เก่งเรื่อง Type Inference และทำ Doc ง่ายกว่า
- **Integrated Validation:** Use **TypeBox** with Elysia for automatic validation and OpenAPI documentation.
    ใช้ TypeBox คู่กับ Elysia เพื่อทำ Validation และสร้าง API Doc อัตโนมัติ
- **Database Safety:** Tools like **Drizzle** or **Kysely** ensure that if your DB schema changes, your frontend code breaks immediately (in a good way!), preventing runtime errors.
    ใช้ Drizzle หรือ Kysely เพื่อให้ Type จาก Database เชื่อมถึงหน้าบ้าน ถ้า DB เปลี่ยน โค้ดต้องฟ้องทันที

> It is **production safety**

---

## Personal Reflection / มุมมองส่วนตัว

Watching BKK.js Summer 2026 made me realize that the boundary between "Web Developer" and "System Engineer" is blurring. The performance requirements for web-based game engines and the precision needed for AI agent orchestration mean we can no longer just "write UI."

**My Takeaway:** I am particularly excited about WebAssembly. The ability to run heavy logic or ML models directly on the client side opens up so many possibilities. My next goal? Learning how to compile Rust or C++ into Wasm to build something high-performance!

การได้ดู BKK.js ครั้งนี้ทำให้เห็นว่าเส้นแบ่งระหว่าง Web Dev และ System Engineer กำลังจางลงเรื่อยๆ เราไม่ได้แค่เขียน UI อีกต่อไป แต่ต้องเข้าใจไปถึงเรื่อง Performance และการคุม AI Agent

**สิ่งที่อยากทำต่อ:** ภัทรสนใจ WebAssembly มากๆ การที่สามารถรัน Logic หนักๆ หรือ ML บนเบราว์เซอร์ได้โดยตรงมันเปิดโอกาสใหม่ๆ เยอะมาก เป้าหมายต่อไปของภัทรคือฝึก WebAssembly เพื่อลองสร้างอะไรที่ High-performance ดู

> **Let’s evolve, not panic.**

---

### Resources & Credits

- [BKK.js 24 Summer 2026 Live Stream](www.facebook.com/share/v/1DLp4BWZfj)

---

tags:

- BKKjs
- WebDevelopment
- JavaScript
- AI
- VibeCoding
- Programming
- TechInBangkok

---

Written by Pat (Napatchol) | Full-Stack Developer
