# What I Learned from 4 Months Without AI Coding Tools (and 2 Months with Them)

> Probation without any agentic AI, then Claude and Antigravity — and what actually changed

I finished my MSc in Advanced Computer Science at the University of Kent and recently came back to work. My first months back were spent on probation with a small dev team building a **CTF and cybersecurity learning platform** — no Claude, no agentic AI, just me and the codebase, while four colleagues on the same team worked with full Claude access.

ภัทรเรียนจบ MSc Advanced Computer Science ที่ University of Kent แล้วเพิ่งกลับมาทำงานอีกครั้ง ช่วงแรกที่กลับมาคือช่วงทดลองงานกับทีมเล็กๆ ที่ทำ **แพลตฟอร์มเรียนรู้ด้าน CTF และ Cybersecurity** ตอนนั้นภัทรยังไม่มี Claude หรือ AI Agent ใดๆ เลย มีแค่ตัวเองกับ codebase ในขณะที่เพื่อนร่วมทีมอีก 4 คนใช้ Claude ได้เต็มที่ค่ะ

This post is not a "how AI made me 10x" story. It is a note about what those two periods actually felt like, and what I am still figuring out.

บทความนี้ไม่ใช่เรื่อง "AI ทำให้ภัทรเก่งขึ้น 10 เท่า" แต่เป็นบันทึกว่าสองช่วงเวลานั้นเป็นยังไงจริงๆ และตอนนี้ภัทรยังหาจุดลงตัวอะไรอยู่บ้าง

---

## 1. The Setup

The company is small, so everyone wears every hat. In a given week I might touch **BA, SA, frontend, backend, DevOps, QA, and UX/UI design**.

บริษัทเป็นบริษัทเล็ก ทุกคนเลยต้องทำได้หลายบทบาท ในหนึ่งสัปดาห์ภัทรอาจได้แตะทั้ง **BA, SA, Frontend, Backend, DevOps, QA และ UX/UI Design**

That matters for this story: when a team works this way, AI leverage (or the lack of it) does not only show up in coding. It shows up everywhere.

จุดนี้สำคัญกับเรื่องนี้มาก เพราะเมื่อทีมทำงานแบบนี้ การมีหรือไม่มี AI ช่วย จะไม่ได้ส่งผลแค่ตอนเขียนโค้ด แต่ส่งผลกับทุกงาน

During probation — about four months — I did all of it without any AI coding tool.

ตลอดช่วงทดลองงานประมาณ 4 เดือน ภัทรทำงานทั้งหมดนี้โดยไม่มี AI ช่วยเขียนโค้ดเลย

I do not think that was an accident. My read is that the company wanted to see how I handled tasks **without** AI first — whether I could read an unfamiliar codebase, follow conventions, and ship something correct on my own. Probation is the one window where they can actually measure that, because once the tools are on, it gets hard to tell where my judgement ends and the model's output begins.

ภัทรไม่คิดว่านี่เป็นความบังเอิญนะคะ ภัทรเข้าใจว่าบริษัทอยากเห็นก่อนว่าถ้า **ไม่มี AI** ภัทรจะรับมือกับงานได้แค่ไหน อ่าน codebase ที่ไม่คุ้นเคยได้ไหม ทำตาม convention ได้ไหม และส่งงานที่ถูกต้องด้วยตัวเองได้ไหม ช่วงทดลองงานเป็นช่วงเดียวที่วัดเรื่องนี้ได้จริง เพราะพอเปิดเครื่องมือให้ใช้แล้ว มันจะแยกยากมากว่าอันไหนคือการตัดสินใจของเรา และอันไหนคือผลลัพธ์ที่โมเดลสร้างขึ้นมา

Knowing that changed how I felt about the four months. It was not "everyone else got the good tools and I did not." They were taking a baseline — and honestly, that is fair.

พอคิดได้แบบนี้ ความรู้สึกต่อ 4 เดือนนั้นก็เปลี่ยนไปค่ะ มันไม่ใช่ "คนอื่นได้เครื่องมือดีๆ แต่เราไม่ได้" แต่มันคือการวัดพื้นฐานของเรา ซึ่งพูดตรงๆ ก็เป็นการวัดที่แฟร์ดี

---

## 2. Working Without AI Tools

A large part of those months was spent reading. I reviewed my colleagues' pull requests — many of them AI-assisted — and left comments on **component reuse, frontend structure, and styling conventions**.

เวลาส่วนใหญ่ในช่วงนั้นหมดไปกับการ "อ่าน" ภัทรรีวิว Pull Request ของเพื่อนร่วมทีม ซึ่งหลายอันเขียนด้วย AI แล้วคอมเมนต์เรื่อง **การ reuse component, โครงสร้างของ Frontend และ convention ของ style**

The interesting part: the codebase is **Vue**, but my background is **React and Next.js**.

จุดที่น่าสนใจคือ codebase เป็น **Vue** แต่พื้นฐานของภัทรคือ **React และ Next.js**

- **What transferred:** structural review. Whether a component should be split, whether logic was duplicated, whether the folder structure made sense — none of that is framework-specific.
    **สิ่งที่ข้ามเฟรมเวิร์กได้:** การรีวิวเชิงโครงสร้าง เช่น component นี้ควรแยกไหม, logic ซ้ำกันหรือเปล่า, โครงสร้างโฟลเดอร์สมเหตุสมผลไหม เรื่องพวกนี้ไม่ผูกกับเฟรมเวิร์ก
- **What did not transfer:** framework idioms. I could not confidently review **Vuex** usage or Vue-specific patterns, because I simply had not learned them yet.
    **สิ่งที่ข้ามไม่ได้:** สำนวนเฉพาะของเฟรมเวิร์ก ภัทรยังรีวิวเรื่อง **Vuex** หรือ pattern เฉพาะของ Vue ได้ไม่มั่นใจ เพราะยังไม่ได้เรียนรู้มันจริงๆ

On the backend it was slower but more straightforward — I could follow the team's existing patterns and rules. It just took time.

ส่วนงาน Backend จะช้ากว่าแต่ตรงไปตรงมากว่า ภัทรทำตาม pattern และ rule ที่ทีมวางไว้ได้ แค่ใช้เวลานานหน่อย

> Reading code every day turned out to be its own kind of training.

---

## 3. Getting Access to Claude

After probation I got access to **Claude (chat, Claude Code, and Design)** and the **Antigravity CLI (Google's agentic coding tool)**. This is my first time working with agentic AI in a real job.

หลังผ่านโปร ภัทรได้ใช้ **Claude (ทั้ง chat, Claude Code และ Design)** และ **Antigravity CLI (เครื่องมือ agentic coding ของ Google)** นี่เป็นครั้งแรกที่ภัทรได้ทำงานกับ Agentic AI ในงานจริง

The speed-up was real. Work that would have taken me **2–3 days** started landing in **3–5 hours**.

ความเร็วที่เพิ่มขึ้นคือเรื่องจริง งานที่เมื่อก่อนต้องใช้ **2–3 วัน** เริ่มเสร็จได้ใน **3–5 ชั่วโมง**

But the tasks got harder too. Faster delivery meant harder tickets, not lighter weeks.

แต่งานก็ยากขึ้นด้วย พอทำได้เร็วขึ้น งานที่ได้รับก็ยากขึ้นตาม ไม่ได้แปลว่าสัปดาห์จะสบายขึ้น

Honestly, some of those tasks I do not think I would have finished at all without Claude.

พูดตรงๆ คืองานบางชิ้น ถ้าไม่มี Claude ภัทรก็คงทำไม่เสร็จเลยค่ะ

---

## 4. What Changed in How I Work

A few things I noticed, stated plainly:

สิ่งที่ภัทรสังเกตเห็น ขอเล่าตรงๆ ดังนี้

- **I started asking Claude to do everything.** Only when I get close to my usage limit do I switch to small frontend bugs by hand. That means my usage limit — not my judgement — is deciding what I practice.
    **ภัทรเริ่มให้ Claude ทำทุกอย่าง** พอ limit ใกล้หมด ถึงจะกลับมาแก้บั๊ก Frontend เล็กๆ ด้วยมือ แปลว่าตัวที่ตัดสินใจว่าภัทรจะได้ฝึกอะไร คือ limit ไม่ใช่การตัดสินใจของภัทรเอง
- **Claude does not always match the codebase.** It sometimes misses the team's **logger pattern**, or reaches for `localStorage` where the codebase uses **Vuex**.
    **Claude ไม่ได้เข้ากับ codebase เสมอไป** บางครั้งมันข้าม **logger pattern** ของทีม หรือเลือกใช้ `localStorage` ทั้งที่ codebase ใช้ **Vuex**

That second point is not really a Claude problem — it is a **context problem**. Nobody told Claude those conventions.

ข้อที่สองนี้จริงๆ ไม่ใช่ปัญหาของ Claude แต่เป็น **ปัญหาเรื่อง context** เพราะไม่มีใครบอก convention พวกนั้นกับมันเลย

I had been avoiding writing skills, config, and context files because I thought they would eat my usage limit faster. Looking at it again, the math runs the other way: when Claude misses a convention, I re-prompt and it **regenerates the whole task** — sometimes twice. A short context file costs a fraction of that, once per session.

ก่อนหน้านี้ภัทรเลี่ยงการเขียน skill, config และไฟล์ context เพราะคิดว่าจะทำให้ limit หมดเร็วขึ้น แต่พอกลับมามองใหม่ มันกลับกัน เพราะเวลาที่ Claude พลาด convention ภัทรต้องสั่งใหม่ แล้วมัน **generate งานทั้งชิ้นใหม่หมด** บางทีสองรอบ ในขณะที่ไฟล์ context สั้นๆ ใช้ token น้อยกว่านั้นมาก และเสียแค่ครั้งเดียวต่อ session

> Skipping context to save tokens costs more tokens in retries.

---

## 5. What I Am Still Figuring Out

I am still tuning the setup. Right now that means:

ตอนนี้ภัทรยังปรับจูนอยู่ค่ะ สิ่งที่กำลังทำคือ

- **Learning properly.** I am going through Anthropic's official courses — Claude basics, Claude Code, MCP, subagents, and agent skills — and keeping notes as I go.
    **เรียนให้เข้าใจจริง** ภัทรกำลังเรียนคอร์สทางการของ Anthropic ทั้ง Claude เบื้องต้น, Claude Code, MCP, subagents และ agent skills แล้วจดโน้ตไว้ระหว่างเรียน
- **Writing context down.** A short `CLAUDE.md` for the work repo — logger pattern, state management rules, which components to reuse — instead of re-explaining every session.
    **เขียน context เก็บไว้** ทำไฟล์ `CLAUDE.md` สั้นๆ ในโปรเจกต์งาน ใส่ logger pattern, กฎการจัดการ state, component ที่ควร reuse แทนที่จะอธิบายใหม่ทุกครั้ง
- **Deciding what to delegate on purpose.** The better question is not "how much limit do I have left?" but **"can I catch it if Claude gets this wrong?"**
    **เลือกว่าจะให้ AI ทำอะไร โดยตั้งใจเลือก** คำถามที่ดีกว่าไม่ใช่ "ยังมี limit เหลือไหม" แต่คือ **"ถ้า Claude ทำผิด ภัทรจับได้ไหม"**
- **Keeping the review habit.** The reading skill from those four months is the thing that lets me check AI output at all. It is worth protecting.
    **รักษานิสัยการรีวิวไว้** ทักษะการอ่านโค้ดจาก 4 เดือนนั้นคือสิ่งที่ทำให้ภัทรตรวจงานของ AI ได้ เลยเป็นสิ่งที่ควรรักษาไว้

If the workflow settles into something that actually works, I would like to write a follow-up about the courses and the full setup — Claude Code, Antigravity CLI, and the other tools I use at work.

ถ้าเวิร์กโฟลว์เริ่มลงตัวจริงๆ ภัทรอยากเขียนบทความต่อ เล่าเรื่องคอร์สที่เรียนและการเซ็ตอัปทั้งหมด ทั้ง Claude Code, Antigravity CLI และเครื่องมืออื่นๆ ที่ใช้ในงานค่ะ

---

## Personal Reflection / มุมมองส่วนตัว

The four months without AI tools were slower, but they built a habit of reading and reviewing code closely. That habit is exactly what makes the last two months useful — it is how I notice when Claude's output does not fit the codebase.

4 เดือนที่ไม่มี AI นั้นช้ากว่าจริง แต่มันสร้างนิสัยการอ่านและรีวิวโค้ดอย่างละเอียด และนิสัยนั้นแหละที่ทำให้ 2 เดือนหลังมีประโยชน์ เพราะมันคือสิ่งที่ทำให้ภัทรรู้ว่าโค้ดจาก Claude ชิ้นไหนไม่เข้ากับ codebase

The risk I see now is losing that habit by delegating everything. So the thing I am working on is not really a config problem — it is choosing, deliberately, what to hand to AI and what to keep doing myself.

ความเสี่ยงที่ภัทรเห็นตอนนี้คือการเสียนิสัยนั้นไปเพราะโยนงานให้ AI ทำหมด สิ่งที่ภัทรกำลังแก้จึงไม่ใช่แค่เรื่อง config แต่คือการ "เลือกอย่างตั้งใจ" ว่าอะไรจะให้ AI ทำ และอะไรที่เราควรทำเอง

Which brings me back to the baseline. If those four months were a test of what I can do without AI, the thing being measured turned out to be the same thing that makes the tools worth having. Protecting it is not nostalgia for the slow months — it is keeping the part of the job that AI cannot check for me.

ซึ่งพอคิดแบบนี้ก็วนกลับมาที่เรื่องการวัดพื้นฐานอีกครั้ง ถ้า 4 เดือนนั้นคือการทดสอบว่าถ้าไม่มี AI ภัทรทำอะไรได้บ้าง สิ่งที่ถูกวัดในตอนนั้นก็คือสิ่งเดียวกับที่ทำให้เครื่องมือพวกนี้มีค่าในวันนี้ การรักษามันไว้จึงไม่ใช่การคิดถึงวันที่ทำงานช้าๆ แต่คือการรักษาส่วนของงานที่ AI ตรวจแทนเราไม่ได้ค่ะ

> Still tuning. Still learning.

---

tags:

- ClaudeCode
- Antigravity
- AgenticAI
- CareerGrowth
- CodeReview
- JuniorDeveloper
- LearningInPublic

---

Written by Pat (Napatchol) | Full-Stack Developer
