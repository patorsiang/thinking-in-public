# What I Learned from 4 Months Without AI Coding Tools (and 2 Months with Them)

> Probation without any agentic AI, then Claude and Antigravity — and what actually changed

I finished my MSc in Advanced Computer Science at the University of Kent and recently came back to work. My first months back were spent on probation with a small product team building a **CTF and cybersecurity learning platform** — no Claude, no agentic AI, just me and the codebase, while everyone who had already passed probation had access to AI-assisted tools.

ภัทรเรียนจบ MSc Advanced Computer Science ที่ University of Kent แล้วเพิ่งกลับมาทำงานอีกครั้ง ช่วงแรกที่กลับมาคือช่วงทดลองงานกับทีมพัฒนา product เล็กๆ ที่ทำ **แพลตฟอร์มเรียนรู้ด้าน CTF และ Cybersecurity** ตอนนั้นภัทรยังไม่มี Claude หรือ AI Agent ใดๆ เลย มีแค่ตัวเองกับ codebase ในขณะที่ทุกคนที่ผ่านโปรแล้วมีสิทธิ์ใช้เครื่องมือ AI ช่วยทำงานค่ะ

This post is not a "how AI made me 10x" story. It is a note about what those two periods actually felt like, and what I am still figuring out.

บทความนี้ไม่ใช่เรื่อง "AI ทำให้ภัทรเก่งขึ้น 10 เท่า" แต่เป็นบันทึกว่าสองช่วงเวลานั้นเป็นยังไงจริงๆ และตอนนี้ภัทรยังหาจุดลงตัวอะไรอยู่บ้าง

---

## 1. The Setup

The company is small, so everyone wears every hat. In a given week I might touch **BA, SA, frontend, backend, DevOps, QA, and UX/UI designer**.

บริษัทเป็นบริษัทเล็ก ทุกคนเลยต้องทำได้หลายบทบาท ในหนึ่งสัปดาห์ภัทรอาจได้แตะทั้ง **BA, SA, Frontend, Backend, DevOps, QA และ UX/UI Designer**

That matters for this story: when a team works this way, AI leverage (or the lack of it) does not only show up in coding. It shows up everywhere.

จุดนี้สำคัญกับเรื่องนี้มาก เพราะเมื่อทีมทำงานแบบนี้ การมีหรือไม่มี AI ช่วย จะไม่ได้ส่งผลแค่ตอนเขียนโค้ด แต่ส่งผลกับทุกงาน

During probation — about four months — I did all of it without any AI coding tool.

ตลอดช่วงทดลองงานประมาณ 4 เดือน ภัทรทำงานทั้งหมดนี้โดยไม่มี AI ช่วยเขียนโค้ดเลย

That was intentional: the company wanted to see how I handled tasks **without** AI first. In a way, it matched how I had worked academically too — during my MSc, I rarely used AI for serious coding work, so I was used to learning by reading, trying, and debugging slowly. Probation became a clearer test of that baseline: could I read an unfamiliar codebase, follow conventions, and ship something correct on my own?

นี่เป็นความตั้งใจของบริษัทค่ะ บริษัทอยากเห็นก่อนว่าถ้า **ไม่มี AI** ภัทรจะรับมือกับงานได้แค่ไหน ซึ่งจริงๆ ก็ใกล้กับวิธีที่ภัทรเรียนมาตอน MSc ด้วย เพราะตอนเรียนภัทรแทบไม่ได้ใช้ AI กับงาน coding จริงจังมากนัก เลยคุ้นกับการเรียนจากการอ่าน ลองเอง debug เอง และค่อยๆ ทำความเข้าใจ ช่วงทดลองงานเลยกลายเป็นการวัด baseline ที่ชัดขึ้นว่า ภัทรอ่าน codebase ที่ไม่คุ้นเคยได้ไหม ทำตาม convention ได้ไหม และส่งงานที่ถูกต้องด้วยตัวเองได้ไหม

Thinking about it that way changed how I felt about the four months. It was not just "everyone else got the good tools and I did not." The company was taking a baseline, and honestly, that was useful.

พอคิดได้แบบนี้ ความรู้สึกต่อ 4 เดือนนั้นก็เปลี่ยนไปค่ะ มันไม่ใช่แค่ "คนอื่นได้เครื่องมือดีๆ แต่เราไม่ได้" แต่บริษัทกำลังวัดพื้นฐานของภัทร และพูดตรงๆ มันก็เป็นเรื่องที่มีประโยชน์มาก

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

After probation I got access to **Claude (chat and Claude Code)**, AI-assisted design workflows, and the **Antigravity CLI (Google's agentic coding tool)**. This is my first time working with agentic AI in a real job.

หลังผ่านโปร ภัทรได้ใช้ **Claude (ทั้ง chat และ Claude Code)**, workflow ด้าน design ที่มี AI ช่วย และ **Antigravity CLI (เครื่องมือ agentic coding ของ Google)** นี่เป็นครั้งแรกที่ภัทรได้ทำงานกับ Agentic AI ในงานจริง

The speed-up was real. Work that would have taken me **2–3 days** started landing in **3–5 hours**.

ความเร็วที่เพิ่มขึ้นคือเรื่องจริง งานที่เมื่อก่อนต้องใช้ **2–3 วัน** เริ่มเสร็จได้ใน **3–5 ชั่วโมง**

But the tasks got harder too. Faster delivery meant harder tickets, not lighter weeks.

แต่งานก็ยากขึ้นด้วย พอทำได้เร็วขึ้น งานที่ได้รับก็ยากขึ้นตาม ไม่ได้แปลว่าสัปดาห์จะสบายขึ้น

Honestly, some of the newer and harder tickets were the kind of work I do not think I could have finished at that pace without Claude.

พูดตรงๆ คืองานที่ใหม่และยากขึ้นบางชิ้น ถ้าไม่มี Claude ภัทรไม่คิดว่าจะทำให้เสร็จในจังหวะนั้นได้ค่ะ

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

## 5. Necessary, or Just Not Optional?

Here is the honest version: after two months with Claude, I still do not think agentic AI is strictly **necessary**. The four months proved that. The work shipped — slower, but it shipped, and I understood every line I sent for review.

ขอเล่าตามตรงนะคะ หลังจากใช้ Claude มาสองเดือน ภัทรก็ยังไม่คิดว่า Agentic AI เป็นสิ่งที่ **จำเป็น** ขนาดนั้น เพราะ 4 เดือนก่อนหน้าก็พิสูจน์แล้วว่างานยังเดินได้ ช้ากว่าจริง แต่มันเสร็จ และภัทรเข้าใจโค้ดทุกบรรทัดที่ส่งไปรีวิว

But "necessary" turns out to be the wrong bar. Working alone, AI is optional. On a team where other people already use it well, the pace of the work is set by the team's workflow, not just by me. Being the only one not using it does not just make me slower — it can make me the slow step inside someone else's task.

แต่คำว่า "จำเป็น" อาจไม่ใช่เกณฑ์ที่ถูกค่ะ ถ้าทำงานคนเดียว AI เป็นแค่ตัวเลือก แต่ในทีมที่คนอื่นใช้มันได้คล่องอยู่แล้ว จังหวะของงานจะถูกตั้งโดย workflow ของทีม ไม่ใช่โดยภัทรคนเดียว การเป็นคนเดียวที่ไม่ได้ใช้ ไม่ได้แปลว่าแค่เราช้า แต่บางครั้งแปลว่าเรากลายเป็นขั้นตอนที่ช้าอยู่ในงานของคนอื่นด้วย

That was the real pressure during those four months — not that I could not do the work, but that I was doing it at a different speed from everything around me. So when I finally got access, the goal was never just "use AI." It was **use it well enough to match the team on both speed and quality**.

นั่นคือแรงกดดันจริงๆ ของ 4 เดือนนั้น ไม่ใช่ว่าภัทรทำงานไม่ได้ แต่คือภัทรทำงานด้วยความเร็วที่ต่างจากทุกอย่างรอบตัว พอได้สิทธิ์ใช้จริงๆ เป้าหมายเลยไม่ใช่แค่ "ใช้ AI ให้เป็น" แต่คือ **"ใช้ให้ดีพอที่จะตามทีมให้ทัน ทั้งความเร็วและคุณภาพ"**

At the same time, I cannot let the fundamentals go. The four months proved that work can still ship without agentic AI. The last two months proved something else: harder work can move much faster with it, but only if I can still review the output. So I am trying to hold both at once: move at the team's pace, and keep learning the things that do not come from a prompt.

แต่ในขณะเดียวกัน ภัทรก็ทิ้งพื้นฐานไม่ได้ 4 เดือนแรกพิสูจน์ว่างานยังเดินได้แม้ไม่มี Agentic AI ส่วน 2 เดือนหลังพิสูจน์อีกอย่างว่า งานที่ยากขึ้นสามารถเดินได้เร็วขึ้นมากถ้ามีเครื่องมือช่วย แต่ต้องเป็นกรณีที่ภัทรยังรีวิวผลลัพธ์ของมันได้จริง ภัทรเลยพยายามถือสองอย่างนี้ไว้พร้อมกัน คือวิ่งให้ทันจังหวะของทีม และเรียนรู้สิ่งที่ไม่ได้มาจากการพิมพ์ prompt ต่อไปค่ะ

> AI was never necessary. It just stopped being optional.

---

## 6. What I Am Still Figuring Out

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

The risk I see now is losing the review habit by delegating everything. So the thing I am working on is not really a config problem — it is choosing, deliberately, what to hand to AI and what to keep doing myself.

ความเสี่ยงที่ภัทรเห็นตอนนี้คือการเสียนิสัยการรีวิวไปเพราะโยนงานให้ AI ทำหมด สิ่งที่ภัทรกำลังแก้จึงไม่ใช่แค่เรื่อง config แต่คือการ "เลือกอย่างตั้งใจ" ว่าอะไรจะให้ AI ทำ และอะไรที่เราควรทำเอง

If those four months gave me a baseline, this is the part worth protecting: not the slowness, but the judgement that lets me tell whether the tool is helping or quietly drifting away from the codebase.

ถ้า 4 เดือนนั้นทำให้ภัทรเห็น baseline ของตัวเอง สิ่งที่ควรรักษาไว้จริงๆ ไม่ใช่ความช้า แต่คือ judgement ที่ทำให้ภัทรดูออกว่าเครื่องมือกำลังช่วยอยู่ หรือกำลังค่อยๆ พาโค้ดหลุดจากทิศทางของ codebase ค่ะ

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
