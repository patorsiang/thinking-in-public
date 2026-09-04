# TH-AI Passport Gave Me Four Prompt Frameworks. A 20-Minute Talk Gave Me the Better Question.

> Reviewing TH-AI Passport, Anthropic's free courses, and the 4Ds

<!-- TODO: insert TH-AI Passport image here, e.g. ![TH-AI Passport](../assets/ai-passport-th.png) -->

Over the past few months I learned about working with AI from three places, in this order: **a pair of Google community events** in March, then **Anthropic's free course catalogue** on Skilljar, and **TH-AI Passport** last. I did not plan them as a sequence. But the order turned out to matter more than any one of them did on its own.

หลายเดือนที่ผ่านมาภัทรเรียนรู้เรื่องการทำงานกับ AI จากสามที่ค่ะ เรียงตามลำดับคือ **งาน community ของ Google สองงาน** เมื่อเดือนมีนาคม ตามด้วย **คอร์สฟรีของ Anthropic** บน Skilljar และปิดท้ายด้วย **TH-AI Passport** ตอนแรกภัทรไม่ได้วางแผนให้มันเป็นลำดับแบบนี้เลย แต่กลายเป็นว่าลำดับการเรียนสำคัญกว่าตัวมันแต่ละอันเสียอีก

This is a review of all three, and I am going to be honest about them — including the parts I think are marketing.

บทความนี้เป็นรีวิวทั้งสามค่ะ และภัทรจะพูดตรงๆ ทุกอัน รวมถึงส่วนที่ภัทรคิดว่าเป็นการตลาดด้วย

---

## 1. The Setup

None of this started with a course. It started with a job.

เรื่องทั้งหมดนี้ไม่ได้เริ่มจากคอร์สค่ะ แต่เริ่มจากงาน

This is my first job where using an **agentic AI coding tool** is part of the work — I wrote about that transition separately, in [What I Learned From 4 Months Without AI Coding Tools](./four-months-without-ai-2026.md). What that post does not cover is the other half: I did not really know how to *talk* to these tools. I could review what they produced. I could not reliably ask for the right thing in the first place. Everything below is me closing that gap, and each source closed a different part of it.

นี่เป็นงานแรกของภัทรที่ต้องใช้ **AI coding agent** เป็นส่วนหนึ่งของงานจริงค่ะ ภัทรเคยเขียนเรื่องช่วงเปลี่ยนผ่านนี้ไว้แล้วที่ [What I Learned From 4 Months Without AI Coding Tools](./four-months-without-ai-2026.md) แต่สิ่งที่บทความนั้นยังไม่ได้พูดถึงคืออีกครึ่งหนึ่ง คือตอนนั้นภัทร *สื่อสาร* กับเครื่องมือพวกนี้ไม่ค่อยเป็น ภัทรรีวิวสิ่งที่มันสร้างออกมาได้ แต่ขอสิ่งที่ต้องการให้ถูกตั้งแต่แรกไม่ค่อยได้ ทุกอย่างข้างล่างนี้คือการที่ภัทรพยายามปิดช่องว่างนั้น และแต่ละแหล่งก็ปิดคนละส่วนกัน

**The Google events came first, and they were not a course at all.** On 22 March 2026 I went to ChaiyoGCP Season 6 in the morning and Build with AI Bangkok in the afternoon — a full day of talks, no curriculum, no certificate. That day was the first time anyone had explained prompting to me as a thing with structure, rather than something you improvise until it works. I came away with a page of notes I did not fully understand yet.

**งาน Google มาก่อน และมันไม่ใช่คอร์สเลย** วันที่ 22 มีนาคม 2026 ภัทรไปงาน ChaiyoGCP Season 6 ตอนเช้า แล้วต่อด้วย Build with AI Bangkok ตอนบ่าย เป็นวันที่เต็มไปด้วย talk ไม่มีหลักสูตร ไม่มีใบประกาศ วันนั้นเป็นครั้งแรกที่มีคนอธิบายให้ภัทรฟังว่าการเขียน prompt มีโครงสร้างของมัน ไม่ใช่แค่การลองไปเรื่อยๆ จนกว่ามันจะได้ผล ภัทรกลับมาพร้อมโน้ตหนึ่งหน้าที่ตอนนั้นยังเข้าใจไม่หมด

**Anthropic's Skilljar courses came next, and they went deeper.** I found them while looking for official Claude Code material for work, then discovered the whole catalogue was free. Two things there landed hardest, and neither was prompting: the **ethics** material, and the technical explanations of how these systems actually work. A lot of what I had been doing at work by pattern-matching finally had a reason attached to it.

**ต่อมาคือคอร์สของ Anthropic บน Skilljar ซึ่งลงลึกกว่ามาก** ภัทรเจอตอนหาเอกสารทางการของ Claude Code สำหรับงาน แล้วพบว่าคอร์สทั้งหมดเรียนฟรี มีสองเรื่องที่โดนที่สุด และไม่ใช่เรื่องการเขียน prompt เลยค่ะ คือเรื่อง **จริยธรรม** กับคำอธิบายเชิงเทคนิคว่าระบบพวกนี้ทำงานยังไงจริงๆ หลายอย่างที่ภัทรทำในงานแบบจำๆ ตามกันมา ในที่สุดก็มีเหตุผลรองรับ

**TH-AI Passport came last, and it is by far the newest thing here.** It is a Thai government programme under the Ministry of Digital Economy and Society: registration opened on 19 August 2026, the AiPASS platform went live on 28 August, and it gives Thai citizens aged 15 and over free access to premium-tier models from more than a dozen providers for about a year, alongside AI literacy material in Thai. It is the kind of thing you can hand to a non-technical colleague without a long explanation first. What I took from it was the discovery that there are *many* ways to write a prompt: several named frameworks, each with its own order and emphasis. That was genuinely new to me, and section 3 is what I think about it now.

**TH-AI Passport มาเป็นอันสุดท้าย และเป็นอันที่ใหม่ที่สุดในนี้แบบทิ้งห่าง** มันคือโครงการของรัฐภายใต้กระทรวงดิจิทัลเพื่อเศรษฐกิจและสังคม เปิดลงทะเบียนวันที่ 19 สิงหาคม 2026 แพลตฟอร์ม AiPASS เปิดใช้งานวันที่ 28 สิงหาคม ให้คนไทยอายุ 15 ปีขึ้นไปใช้โมเดลระดับพรีเมียมจากผู้ให้บริการกว่าสิบเจ้าได้ฟรีประมาณหนึ่งปี พร้อมเนื้อหาความรู้ด้าน AI เป็นภาษาไทย เป็นแบบที่ส่งให้เพื่อนร่วมงานสาย non-tech ได้เลยโดยไม่ต้องอธิบายอะไรยาวๆ ก่อน สิ่งที่ภัทรได้จากมันคือการค้นพบว่าการเขียน prompt มีวิธี *หลายแบบ* มาก มี framework ที่มีชื่อเรียกหลายตัว แต่ละตัวก็มีลำดับและจุดเน้นของตัวเอง ตอนนั้นมันใหม่สำหรับภัทรจริงๆ ค่ะ และหัวข้อที่ 3 คือสิ่งที่ภัทรคิดกับมันตอนนี้

**One caveat before the rest of this post, and it is not a small one.** I am writing this in the first week of September 2026. The Google events are five months behind me and the Anthropic courses ran across the months in between — I have lived with both. TH-AI Passport I have had for days. So read the TH-AI Passport parts of what follows as a first impression, not a verdict. A week is long enough to see the shape of something. It is not long enough to be sure you were right about it.

**ขอออกตัวก่อนหนึ่งเรื่อง และไม่ใช่เรื่องเล็กด้วยค่ะ** ภัทรเขียนบทความนี้ในสัปดาห์แรกของเดือนกันยายน 2026 งาน Google ผ่านมาแล้วห้าเดือน ส่วนคอร์สของ Anthropic ก็เรียนต่อเนื่องมาตลอดช่วงระหว่างนั้น สองอันนี้ภัทรอยู่กับมันมานาน แต่ TH-AI Passport ภัทรเพิ่งได้ใช้ไม่กี่วัน เพราะฉะนั้นส่วนที่พูดถึง TH-AI Passport ในบทความนี้ ขอให้อ่านในฐานะความรู้สึกแรก ไม่ใช่คำตัดสินนะคะ หนึ่งสัปดาห์นานพอจะเห็นรูปร่างของอะไรบางอย่าง แต่ไม่นานพอจะมั่นใจว่าเราคิดถูก

And the order is the part I keep thinking about. By the time I opened TH-AI Passport, I had already been through AI Fluency — so I was not meeting its prompting frameworks cold. I was reading them against a map I already had. And that map, it turned out, was the thing that finally explained a slide I had seen in March and filed away without understanding.

และลำดับนี่แหละคือสิ่งที่ภัทรคิดถึงบ่อยที่สุดค่ะ เพราะตอนที่ภัทรเปิด TH-AI Passport ภัทรผ่าน AI Fluency มาแล้ว ภัทรเลยไม่ได้เจอ framework การเขียน prompt ของมันแบบมือเปล่า แต่กำลังอ่านมันโดยเทียบกับแผนที่ที่มีอยู่แล้วในหัว และแผนที่อันนั้นเองที่ทำให้ภัทรเข้าใจสไลด์แผ่นหนึ่งที่เคยเห็นตั้งแต่เดือนมีนาคม แล้วเก็บเข้าลิ้นชักไปโดยไม่เข้าใจมัน

> One gave me a question. One gave me a way of working. One gave me tools. The order decided which was which.

---

## 2. Where the Question Started

I wrote that March day up separately — [Vibe Coding & Agentic AI: Key Takeaways from ChaiyoGCP & Build with AI Bangkok 2026](./gdg-buildwithai-2026.md) — so I will not repeat the whole thing here. But one slide from it belongs in this post, and I only understood why months later.

ภัทรเขียนสรุปวันนั้นไว้แยกต่างหากแล้วค่ะ ที่ [Vibe Coding & Agentic AI: Key Takeaways from ChaiyoGCP & Build with AI Bangkok 2026](./gdg-buildwithai-2026.md) เลยจะไม่เล่าซ้ำทั้งหมด แต่มีสไลด์แผ่นหนึ่งจากงานนั้นที่ควรอยู่ในบทความนี้ และภัทรเพิ่งเข้าใจว่าทำไมตอนผ่านไปหลายเดือน

In the Vibe Coding talk, Saad Hamid put up a short list contrasting a **powerful prompt** with a **lazy prompt**:

ในเซสชัน Vibe Coding คุณ Saad Hamid ขึ้นลิสต์สั้นๆ เปรียบเทียบระหว่าง **powerful prompt** กับ **lazy prompt** ไว้ว่า

- give a role
- define the goal
- **does it need AI?**
- create the vibe
- optional: add a visual

Five bullets on a conference slide, in a twenty-minute talk, with nothing to sell. I copied them into my notes as a prompting tip list and moved on, because that is what they look like.

ห้าข้อบนสไลด์งานสัมมนา ใน talk ยี่สิบนาที ที่ไม่ได้ขายอะไรเลย ภัทรก็ก๊อปลงโน้ตในฐานะลิสต์เทคนิคเขียน prompt แล้วก็ผ่านไป เพราะหน้าตามันก็เป็นแบบนั้นจริงๆ

Four of them are prompting tips. One of them is not, and it took two more courses before I could see which.

สี่ข้อในนั้นเป็นเทคนิคการเขียน prompt จริงค่ะ แต่มีอยู่ข้อหนึ่งที่ไม่ใช่ และภัทรต้องเรียนอีกสองคอร์สกว่าจะมองออกว่าเป็นข้อไหน

> A conference slide, filed and forgotten. It took two curricula to explain what was on it.

---

## 3. Four Frameworks, One Job

The most concrete thing TH-AI Passport gave me was a set of prompting frameworks. Four of them: **GCCTFE**, **CREATE**, **PARTS**, and **GROW**.

สิ่งที่จับต้องได้ที่สุดที่ TH-AI Passport ให้ภัทรคือชุด framework สำหรับเขียน prompt ค่ะ มีสี่อันคือ **GCCTFE**, **CREATE**, **PARTS** และ **GROW**

| Framework | Expansion | Optimizes for | Best fit | Where it gets thin |
| --- | --- | --- | --- | --- |
| **GCCTFE** | Goal, Context, Constraints, Task, Format, Example | Task precision | One-shot work with a known deliverable | Says nothing about audience or tone |
| **CREATE** | Character, Request, Examples, Adjustments, Type of output, Extras | Voice and iteration | Content work you expect to refine | Loose on hard constraints |
| **PARTS** | Persona, Aim, Recipient, Theme, Structure | Audience fit | Communication — email, slides, teaching material | No slot for examples or constraints |
| **GROW** | Goal, Reality, Options, Way forward | Thinking a decision through | Planning, coaching, exploring options | Not really a prompt frame at all |

<!-- TODO: confirm the CREATE and GROW expansions against the course material — these are the common versions, but the courses may teach different ones. -->

Two things stood out once I put them side by side.

พอเอามาวางเรียงกัน ภัทรเห็นสองอย่างค่ะ

**First: three of them are the same framework wearing different hats.** GCCTFE, CREATE, and PARTS are all the same ingredients in a different order — who the AI should be, what you want, who it is for, what shape the answer takes, and an example if you have one. GCCTFE leads with the task. PARTS leads with the reader. CREATE leads with the voice. That ordering is not nothing — it tells you what the framework thinks you are most likely to forget — but they are not four different skills.

**อย่างแรก: สามอันแรกคือ framework เดียวกันที่ใส่หมวกคนละใบ** GCCTFE, CREATE และ PARTS ใช้ส่วนประกอบชุดเดียวกันแต่เรียงคนละลำดับ คือ AI ควรเป็นใคร เราต้องการอะไร ผลลัพธ์ไปถึงใคร ออกมาหน้าตาแบบไหน และมีตัวอย่างไหม GCCTFE ขึ้นต้นด้วย task, PARTS ขึ้นต้นด้วยคนอ่าน, CREATE ขึ้นต้นด้วยน้ำเสียง ลำดับนี้ไม่ใช่เรื่องไร้ความหมายนะคะ เพราะมันบอกว่า framework นั้นคิดว่าเรามักจะลืมอะไรมากที่สุด แต่มันก็ไม่ใช่ทักษะสี่อย่างที่ต่างกัน

**Second: GROW does not belong in this list.** Goal, Reality, Options, Way forward is a coaching model. It structures a *conversation*, not a prompt. Using it to write a single message is a category error — it only makes sense across several turns, where the AI asks you about your reality before offering options. I actually like it more than the other three for that reason, but it is answering a different question.

**อย่างที่สอง: GROW ไม่ควรอยู่ในลิสต์เดียวกัน** Goal, Reality, Options, Way forward คือโมเดลการโค้ชค่ะ มันจัดโครงสร้างให้ *บทสนทนา* ไม่ใช่ให้ prompt เดียว การเอามันมาเขียนข้อความเดียวจบคือการใช้ผิดประเภท เพราะมันจะมีความหมายก็ต่อเมื่อคุยกันหลายรอบ ให้ AI ถามถึงสถานการณ์จริงของเราก่อนจะเสนอทางเลือก จริงๆ ภัทรชอบ GROW มากกว่าสามอันแรกด้วยซ้ำ แต่มันตอบคนละคำถามค่ะ

> Memorising four acronyms is not four skills. It is one skill and three mnemonics.

---

## 4. The 4Ds Are the Layer Underneath

Here is where the order I took these in matters. I met the 4Ds in Anthropic's **AI Fluency** course *before* I met most of the frameworks above — so I never had to unlearn anything. I just had somewhere to file them.

ตรงนี้แหละค่ะที่ลำดับการเรียนมีผล ภัทรเจอ 4Ds ในคอร์ส **AI Fluency** ของ Anthropic *ก่อน* ที่จะเจอ framework ส่วนใหญ่ข้างบน ภัทรเลยไม่ต้องมานั่งลบความเข้าใจเดิมทิ้ง แค่มีที่ให้เก็บมันเท่านั้นเอง

AI Fluency is built on four moves, the **4Ds**:

AI Fluency สร้างจากสี่การกระทำที่เรียกว่า **4Ds** คือ

- **Delegation** — what should I do, and what should the AI do?
    **Delegation** — งานไหนเราทำ งานไหนให้ AI ทำ
- **Description** — how do I communicate what I want, clearly?
    **Description** — จะสื่อสารสิ่งที่ต้องการให้ชัดได้ยังไง
- **Discernment** — how do I evaluate what comes back?
    **Discernment** — จะประเมินสิ่งที่ AI ตอบกลับมายังไง
- **Diligence** — am I taking responsibility for this output?
    **Diligence** — เรารับผิดชอบต่อผลลัพธ์นี้อยู่หรือเปล่า

Look at where the four prompting frameworks land: **all of them are Description.** Every one. GCCTFE, CREATE, PARTS — they are all techniques for the second D, and they say nothing at all about the other three.

ลองดูว่าสี่ framework ตกอยู่ตรงไหน: **ทั้งหมดคือ Description ค่ะ** ทุกอันเลย ทั้ง GCCTFE, CREATE, PARTS ล้วนเป็นเทคนิคของ D ตัวที่สอง และไม่ได้พูดถึงอีกสามตัวเลย

Now go back to the slide in section 2. Give a role, define the goal, create the vibe, add a visual — four Description tips. And then, sitting in the middle of them: **does it need AI?**

ทีนี้ย้อนกลับไปดูสไลด์ในหัวข้อที่ 2 ค่ะ give a role, define the goal, create the vibe, add a visual คือเทคนิค Description สี่ข้อ แล้วก็มีข้อที่แทรกอยู่ตรงกลางว่า **does it need AI?**

That is not a prompting tip. That is **Delegation** — the first D — asked in plain language on a community-event slide by someone with twenty minutes and nothing to sell. None of the four acronyms ask it. GCCTFE, CREATE, and PARTS all begin *after* the answer is yes: you have already decided to prompt, and they are helping you prompt tidily.

นั่นไม่ใช่เทคนิคการเขียน prompt ค่ะ แต่คือ **Delegation** ซึ่งเป็น D ตัวแรก ถูกถามด้วยภาษาบ้านๆ บนสไลด์งาน community โดยคนที่มีเวลายี่สิบนาทีและไม่ได้ขายอะไร ไม่มี framework ตัวย่อสักอันที่ถามคำถามนี้ เพราะ GCCTFE, CREATE และ PARTS เริ่มต้น *หลังจาก* ที่คำตอบเป็น "ใช่" ไปแล้ว คือเราตัดสินใจจะ prompt เรียบร้อยแล้ว มันแค่มาช่วยให้เรา prompt ได้เรียบร้อยขึ้น

I could not have seen that in March, and I could not have seen it from the frameworks alone. It took the 4Ds to give the missing bullet a name.

ภัทรมองไม่เห็นเรื่องนี้ตอนเดือนมีนาคมค่ะ และก็มองไม่เห็นถ้าดูจาก framework อย่างเดียวด้วย ต้องมี 4Ds ก่อน ถึงจะเรียกชื่อข้อที่หายไปนั้นได้

That matters because Description is the D that fails most visibly and least expensively. A bad prompt gives you a bad answer, you notice, you try again. **Delegation failures are worse:** you hand the AI something you should have done yourself, and you find out weeks later. **Discernment failures are worse still:** the output looks right, so you ship it. The AI Fluency course spends real time on the loop — describe, discern, refine, integrate — rather than on getting the first prompt perfect.

เรื่องนี้สำคัญเพราะ Description เป็น D ที่พังแบบเห็นชัดที่สุดและเสียหายน้อยที่สุด prompt แย่ก็ได้คำตอบแย่ เราเห็นเอง แล้วก็ลองใหม่ แต่ **Delegation พังหนักกว่า** คือเรายกงานที่ควรทำเองให้ AI ทำ แล้วมารู้ตัวอีกทีตอนผ่านไปหลายสัปดาห์ และ **Discernment พังหนักที่สุด** คือผลลัพธ์ดูถูก เราเลยส่งงานไปเลย คอร์ส AI Fluency ใช้เวลาไปกับ loop คือ describe, discern, refine, integrate มากกว่าจะไปเน้นให้ prompt แรกสมบูรณ์แบบ

If I had taken the frameworks courses alone, I would have come out a better prompt writer and no better at deciding what to delegate — which, after four months of working without AI tools at all, is the part I actually needed. And I suspect I would not have noticed the gap, because a better prompt *feels* like progress.

ถ้าภัทรเรียนแค่คอร์สที่สอน framework อย่างเดียว ภัทรคงเขียน prompt ได้ดีขึ้น แต่ไม่ได้เก่งขึ้นเลยในเรื่องการตัดสินใจว่าจะยกงานไหนให้ AI ซึ่งหลังจากผ่านสี่เดือนที่ทำงานโดยไม่มีเครื่องมือ AI เลย นั่นคือส่วนที่ภัทรต้องการจริงๆ ค่ะ และภัทรสงสัยว่าตัวเองคงไม่ทันสังเกตช่องว่างนี้ด้วยซ้ำ เพราะการเขียน prompt ได้ดีขึ้นมัน *รู้สึก* เหมือนเราเก่งขึ้นแล้ว

> A framework tells you how to ask. It does not tell you whether you should have asked.

---

## 5. What Other People Ran Into

I am not the only person who took these courses, and some of the reports from others are worth repeating — with the caveat that these are **their** findings, not mine. I have not reproduced them myself.

ภัทรไม่ใช่คนเดียวที่เรียนคอร์สพวกนี้ค่ะ และมีบางเรื่องที่คนอื่นเจอแล้วน่าเอามาเล่าต่อ แต่ขอออกตัวไว้ก่อนว่านี่เป็นสิ่งที่ **คนอื่น** เจอ ไม่ใช่ภัทร และภัทรยังไม่ได้ลองทำซ้ำเอง

**The generated images.** Within days of the AiPASS platform opening, people were posting AI-generated images where Thai script came out as unreadable shapes — text that looks like Thai at a glance and dissolves into nothing when you actually read it. Faces of well-known people came out wrong, object details drifted, and generated video moved unnaturally. ([MGR Online](https://mgronline.com/onlinesection/detail/9690000086185), [iPhone-Droid](https://www.iphone-droid.net/th-ai-passport-thai-text-image-errors/))

**เรื่องภาพที่เจนออกมา** หลังแพลตฟอร์ม AiPASS เปิดได้ไม่กี่วัน ก็มีคนเอาภาพที่ AI สร้างมาโพสต์กัน ภาพที่ตัวอักษรไทยกลายเป็นรูปทรงที่อ่านไม่ออก คือมองผ่านๆ เหมือนภาษาไทย แต่พอตั้งใจอ่านจริงๆ กลับไม่เป็นคำ ใบหน้าคนดังก็ออกมาไม่ตรง รายละเอียดของวัตถุเพี้ยน และวิดีโอที่สร้างออกมาก็เคลื่อนไหวไม่เป็นธรรมชาติ ([MGR Online](https://mgronline.com/onlinesection/detail/9690000086185), [iPhone-Droid](https://www.iphone-droid.net/th-ai-passport-thai-text-image-errors/))

**What I think that actually shows.** Here is where I want to separate the pile-on from the finding, because they are not the same thing. Thai script rendering is a known weak spot in image models generally — it is not something this platform invented, and the same prompt against the same model outside AiPASS would likely fail in the same way. What launch week exposed was less a broken platform than a gap between what "premium AI, free for a year" sounds like and what these models can currently do with Thai. That gap is a **Discernment** problem, and it arrived for a million people at once, most of whom had no reason to expect it.

**สิ่งที่ภัทรคิดว่ามันสะท้อนจริงๆ** ตรงนี้ภัทรอยากแยกระหว่าง "กระแสถล่ม" กับ "สิ่งที่ค้นพบ" ออกจากกันค่ะ เพราะมันไม่ใช่เรื่องเดียวกัน การเรนเดอร์ตัวอักษรไทยเป็นจุดอ่อนที่รู้กันอยู่แล้วของโมเดลสร้างภาพโดยทั่วไป ไม่ใช่เรื่องที่แพลตฟอร์มนี้สร้างขึ้นมาเอง และถ้าเอา prompt เดียวกันไปใช้กับโมเดลเดียวกันนอก AiPASS ก็คงพังแบบเดียวกัน สิ่งที่สัปดาห์แรกเปิดโปงออกมาจึงไม่ใช่แพลตฟอร์มที่พัง แต่เป็นช่องว่างระหว่างคำว่า "AI ระดับพรีเมียม ใช้ฟรีหนึ่งปี" กับสิ่งที่โมเดลพวกนี้ทำกับภาษาไทยได้จริงในตอนนี้ ช่องว่างนั้นคือปัญหาเรื่อง **Discernment** ค่ะ และมันมาถึงคนเป็นล้านพร้อมกัน โดยที่คนส่วนใหญ่ไม่มีเหตุผลอะไรให้คาดคิดมาก่อนเลย

**The shape of the access.** You reach the models through the AiPASS portal, not by logging into ChatGPT or Claude directly. Access is tiered, the premium models carry quotas rather than open use, and accounts can be suspended after around ten days of inactivity. ([MeMarketThink](https://www.memarketthink.com/post/th-aipassport))

**รูปแบบของสิทธิ์ที่ได้** เราเข้าถึงโมเดลผ่านพอร์ทัล AiPASS ค่ะ ไม่ใช่การล็อกอินเข้า ChatGPT หรือ Claude ตรงๆ สิทธิ์แบ่งเป็นระดับ โมเดลพรีเมียมมีโควตาจำกัดไม่ใช่ใช้ได้ไม่อั้น และบัญชีอาจถูกระงับชั่วคราวถ้าไม่ได้ล็อกอินประมาณสิบวัน ([MeMarketThink](https://www.memarketthink.com/post/th-aipassport))

For me that is the most practically limiting part, and it is not a complaint about quality. It means the thing I would most want this for — wiring a model into my own tooling at work — is not what this is. It is a place to sit and use AI, not a key you take away with you.

สำหรับภัทร นี่คือข้อจำกัดที่กระทบการใช้งานจริงมากที่สุดค่ะ และไม่ใช่การบ่นเรื่องคุณภาพเลย มันแปลว่าสิ่งที่ภัทรอยากใช้มันมากที่สุด คือการต่อโมเดลเข้ากับเครื่องมือของตัวเองในงาน ไม่ใช่สิ่งที่โครงการนี้ให้ มันคือที่ที่เราไปนั่งใช้ AI ไม่ใช่กุญแจที่เราถือกลับบ้านได้

**And it has an end date.** The access runs for about a year. After that, if you want to keep the tools, you buy them. The programme has also drawn political argument over whether 1.6 billion baht was good value, with People's Party leader Natthaphong Ruengpanyawut among those saying it was not. ([Khaosod English](https://www.khaosodenglish.com/politics/2026/09/01/natthaphong-says-1-6bn-baht-th-ai-passport-poor-value-raises-concerns-over-restrictions/), [The Nation](https://www.nationthailand.com/business/tech/40070079))

**และมันมีวันหมดอายุ** สิทธิ์นี้ใช้ได้ประมาณหนึ่งปีค่ะ หลังจากนั้นถ้าอยากใช้เครื่องมือพวกนี้ต่อ ก็ต้องซื้อเอง โครงการนี้ยังมีข้อถกเถียงทางการเมืองด้วยว่างบ 1,600 ล้านบาทคุ้มค่าหรือไม่ โดยคุณณัฐพงษ์ เรืองปัญญาวุฒิ หัวหน้าพรรคประชาชน เป็นหนึ่งในคนที่มองว่าไม่คุ้ม ([Khaosod English](https://www.khaosodenglish.com/politics/2026/09/01/natthaphong-says-1-6bn-baht-th-ai-passport-poor-value-raises-concerns-over-restrictions/), [The Nation](https://www.nationthailand.com/business/tech/40070079))

I have no useful opinion on the budget. But the shape underneath it is the thing this whole post has been circling, and it is worth saying plainly.

ภัทรไม่มีความเห็นที่เป็นประโยชน์อะไรเรื่องงบประมาณค่ะ แต่รูปร่างที่อยู่ข้างใต้มันคือสิ่งที่บทความนี้วนอยู่รอบๆ มาตลอด และควรพูดออกมาตรงๆ

> Free for a year, and then you buy it. That is not an accusation — it is the model, stated out loud.

---

## 6. A Showroom, Not a Classroom

Here is my honest read on TH-AI Passport.

นี่คือความเห็นตรงๆ ของภัทรต่อ TH-AI Passport ค่ะ

It works like a **car showroom**. You walk in, you test drive several models in one afternoon, a salesperson explains what each one is good at, and you leave knowing which one you liked. The course puts several AI tools in front of you, gives you a framework to try on each, and lets you feel the difference.

มันทำงานเหมือน **โชว์รูมรถ** ค่ะ เราเดินเข้าไป ได้ลองขับหลายรุ่นในบ่ายเดียว มีเซลส์อธิบายว่าแต่ละรุ่นเด่นเรื่องอะไร แล้วเราก็เดินออกมาโดยรู้ว่าชอบรุ่นไหน คอร์สนี้เอาเครื่องมือ AI หลายตัวมาวางตรงหน้า ให้ framework ไปลองใช้กับแต่ละตัว แล้วปล่อยให้เรารู้สึกถึงความต่างเอง

And a test drive is genuinely useful. It is also, structurally, how a dealership sells cars. Every tool in the showroom has a subscribe button at the end of the trial, and a course that teaches you tool-by-tool is a course whose natural endpoint is a paid plan. That is not a scandal — it is just worth naming, because it shapes what gets taught. You learn *this tool's* interface, not a transferable way of thinking.

การได้ลองขับมีประโยชน์จริงค่ะ แต่ในเชิงโครงสร้าง มันก็คือวิธีที่โชว์รูมใช้ขายรถเหมือนกัน เครื่องมือทุกตัวในโชว์รูมมีปุ่ม subscribe รออยู่ตอนหมดช่วงทดลอง และคอร์สที่สอนแบบไล่ทีละเครื่องมือ ปลายทางตามธรรมชาติของมันคือแพ็กเกจแบบเสียเงิน นี่ไม่ใช่เรื่องน่าตกใจนะคะ แต่ควรพูดออกมาตรงๆ เพราะมันกำหนดว่าคอร์สจะสอนอะไร เราจะได้เรียนหน้าตาของ *เครื่องมือตัวนั้น* ไม่ใช่วิธีคิดที่เอาไปใช้ต่อได้

**I watched most of it at 2x.** That is probably the most honest thing I can tell you about my experience of the course. I already knew most of what was being explained, so I sped through looking for the parts that were new — which turned out to be the framework names in section 3, and not a great deal else. I am not reporting that as a flaw. I am reporting it as a fact about who I was when I opened it.

**ภัทรดูส่วนใหญ่ที่ความเร็ว 2x ค่ะ** นี่น่าจะเป็นสิ่งที่ตรงที่สุดที่ภัทรบอกได้เกี่ยวกับประสบการณ์การเรียนคอร์สนี้ ภัทรรู้เรื่องที่มันอธิบายอยู่แล้วเกือบหมด เลยเร่งดูผ่านๆ เพื่อหาส่วนที่ใหม่จริงๆ ซึ่งกลายเป็นว่ามีแค่ชื่อ framework ในหัวข้อที่ 3 และแทบไม่มีอะไรอื่นอีกเลย ภัทรไม่ได้เล่าเรื่องนี้ในฐานะข้อเสียนะคะ แต่เล่าในฐานะข้อเท็จจริงว่าตอนที่ภัทรเปิดมัน ภัทรยืนอยู่ตรงไหน

A course you can watch at 2x is not a bad course. It is a course aimed at someone who is not you. Those are very different findings, and reviews confuse them constantly.

คอร์สที่เราดูที่ 2x ได้ ไม่ใช่คอร์สที่แย่ค่ะ แต่คือคอร์สที่ตั้งใจทำให้คนอื่นที่ไม่ใช่เรา สองอย่างนี้เป็นคนละเรื่องกันเลย และรีวิวส่วนใหญ่ก็มักจะสับสนระหว่างสองอย่างนี้

**But the showroom shape is right for beginners, and I want to be fair about that.** You should not hand a beginner a model card or an API doc. You should put three models in front of them and let them notice that the same prompt produces three different answers. That noticing is the start of Discernment, even if the course never uses the word. For a colleague who has never opened an AI tool, TH-AI Passport is the thing I would send — and being in Thai matters more than people who read English documentation tend to remember.

**แต่รูปแบบโชว์รูมเหมาะกับมือใหม่จริงๆ และภัทรอยากให้เครดิตตรงนี้ด้วย** เราไม่ควรยื่น model card หรือเอกสาร API ให้มือใหม่ค่ะ เราควรเอาโมเดลสามตัวมาวางตรงหน้าแล้วให้เขาสังเกตเองว่า prompt เดียวกันให้คำตอบต่างกันสามแบบ การสังเกตเห็นตรงนั้นคือจุดเริ่มต้นของ Discernment ถึงแม้คอร์สจะไม่เคยใช้คำนี้เลยก็ตาม ถ้าเป็นเพื่อนร่วมงานที่ไม่เคยเปิดเครื่องมือ AI เลย TH-AI Passport คือสิ่งที่ภัทรจะส่งให้ และการที่มันเป็นภาษาไทยสำคัญกว่าที่คนอ่านเอกสารภาษาอังกฤษได้จะนึกถึงมากค่ะ

And I should hold my own metaphor to the standard I used in section 5: a week is a test drive too. This is what the showroom looks like from the doorway.

และภัทรก็ควรใช้มาตรฐานเดียวกับที่ใช้ในหัวข้อที่ 5 กับคำเปรียบเทียบของตัวเองด้วยค่ะ คือหนึ่งสัปดาห์ก็เป็นแค่การทดลองขับเหมือนกัน นี่คือภาพของโชว์รูมที่มองจากตรงประตูทางเข้าเท่านั้น

> A test drive teaches you the car. It does not teach you to drive.

---

## 7. Anthropic's Courses: Free, and You Keep Them

Anthropic's Skilljar catalogue is free, and I want to be careful here too — it is also marketing. Anthropic teaches you AI fluency, and you happen to learn it inside Claude's interface. Nobody is doing this out of pure goodwill.

คอร์สของ Anthropic บน Skilljar เรียนฟรีค่ะ และภัทรอยากพูดให้แฟร์ตรงนี้เหมือนกันว่ามันก็เป็นการตลาดเช่นกัน Anthropic สอน AI fluency ให้เรา แล้วบังเอิญว่าเราเรียนมันผ่านหน้าจอของ Claude ไม่มีใครทำเรื่องนี้ด้วยความหวังดีล้วนๆ หรอกค่ะ

The difference is **what you are left holding when you close the tab**. The 4Ds are not Claude features. Delegation, Description, Discernment, Diligence work with any model — I have used them with Antigravity at work, with no adjustment. The AI Fluency course is genuinely about working with AI, not about working with Claude.

ความต่างอยู่ที่ **สิ่งที่ยังอยู่ในมือเราตอนปิดแท็บ** ค่ะ 4Ds ไม่ใช่ฟีเจอร์ของ Claude เพราะ Delegation, Description, Discernment, Diligence ใช้ได้กับทุกโมเดล ภัทรเอาไปใช้กับ Antigravity ในงานได้เลยโดยไม่ต้องปรับอะไร คอร์ส AI Fluency พูดเรื่องการทำงานร่วมกับ AI จริงๆ ไม่ใช่การทำงานกับ Claude

The part I did not expect to value was the **ethics** material. At work, questions like what I am allowed to paste into a prompt, what I have to disclose, and what I am still accountable for had come up as vague discomfort rather than anything I could reason about. Diligence — the fourth D — gave that discomfort a structure. No prompting framework I have seen goes anywhere near it, and it is the part of this that will still matter when every acronym in section 3 is obsolete.

ส่วนที่ภัทรไม่คิดว่าจะชอบแต่กลับได้ประโยชน์มากคือเนื้อหาเรื่อง **จริยธรรม** ค่ะ ในงานจริง คำถามอย่างเราวางอะไรลงใน prompt ได้บ้าง ต้องบอกใครไหมว่าใช้ AI และเรายังต้องรับผิดชอบอะไรอยู่ มันเคยเป็นแค่ความรู้สึกอึดอัดลอยๆ ที่ภัทรคิดต่อไม่เป็น Diligence ซึ่งเป็น D ตัวที่สี่ ทำให้ความอึดอัดนั้นมีโครงสร้างขึ้นมา ยังไม่เคยเห็น framework การเขียน prompt ตัวไหนแตะเรื่องนี้เลย และนี่คือส่วนที่จะยังสำคัญอยู่ ตอนที่ตัวย่อทุกตัวในหัวข้อที่ 3 ล้าสมัยไปแล้ว

The rest of the catalogue is more product-specific — Claude API, MCP, subagents, agent skills — but those are advertised as what they are. Nobody is pretending the MCP course is vendor-neutral. And even there, MCP itself is an open protocol, so the concepts travel further than the branding suggests.

ส่วนคอร์สที่เหลือจะผูกกับ product มากกว่า เช่น Claude API, MCP, subagents และ agent skills แต่คอร์สพวกนี้ก็บอกตรงๆ ว่ามันคืออะไร ไม่มีใครแกล้งทำเป็นว่าคอร์ส MCP เป็นกลางกับทุกเจ้า และถึงอย่างนั้น MCP เองก็เป็น open protocol แนวคิดเลยเดินทางไปได้ไกลกว่าที่แบรนด์บอกไว้ค่ะ

> Both courses are marketing. One of them leaves you with a framework; the other leaves you with a trial account.

---

## Personal Reflection / มุมมองส่วนตัว

If I could only send one to a beginner, I would still send **TH-AI Passport** — in Thai, low friction, and a showroom is the right first room to stand in.

ถ้าเลือกส่งให้มือใหม่ได้แค่อันเดียว ภัทรก็ยังจะส่ง **TH-AI Passport** ค่ะ เพราะเป็นภาษาไทย เข้าถึงง่าย และโชว์รูมก็เป็นห้องแรกที่ถูกต้องแล้วสำหรับการเริ่มต้น

If I could only take one myself, it would be **AI Fluency**. The acronyms taught me to write a tidier prompt. The 4Ds taught me to ask whether I should be prompting at all — and that is the question that was actually costing me something at work.

แต่ถ้าเลือกเรียนเองได้แค่อันเดียว ภัทรจะเลือก **AI Fluency** ค่ะ ตัวย่อพวกนั้นสอนให้ภัทรเขียน prompt ได้เรียบร้อยขึ้น แต่ 4Ds สอนให้ภัทรถามตัวเองว่าควรจะ prompt ตั้งแต่แรกหรือเปล่า และนั่นคือคำถามที่กำลังทำให้ภัทรเสียอะไรบางอย่างในงานจริงๆ

But the honest answer is that I would not change the order, and I would not drop the conference talk either — the least structured thing on the list. Starting in a lecture hall in March and finishing in TH-AI Passport meant each one was checking the one before it. Taking only the best one would have left me with nothing to check it against.

แต่คำตอบที่ตรงที่สุดคือ ภัทรจะไม่เปลี่ยนลำดับเลยค่ะ และจะไม่ตัดงานสัมมนาออกด้วย ทั้งที่มันเป็นอย่างที่มีโครงสร้างน้อยที่สุดในลิสต์ การเริ่มที่ห้องบรรยายเมื่อเดือนมีนาคม แล้วไปจบที่ TH-AI Passport ทำให้แต่ละอันคอยตรวจสอบอันก่อนหน้า ถ้าเลือกเอาแค่อันที่ดีที่สุดอันเดียว ภัทรก็จะไม่มีอะไรไว้เทียบกับมันเลย

The best question I got in all of this came from the source with the least authority behind it — a twenty-minute talk, not a curriculum. That is worth remembering the next time I decide something is too informal to take notes on.

คำถามที่ดีที่สุดที่ภัทรได้จากทั้งหมดนี้ มาจากแหล่งที่มีความเป็นทางการน้อยที่สุดค่ะ คือ talk ยี่สิบนาที ไม่ใช่หลักสูตร เรื่องนี้น่าจำไว้ เผื่อคราวหน้าที่ภัทรจะตัดสินว่าอะไรสักอย่าง "ไม่เป็นทางการพอ" จนไม่ต้องจดโน้ต

The thing I keep coming back to is that all three courses are, in the end, someone's funnel. That is fine. The question is not whether a free course is marketing — it always is. The question is whether the thing it teaches you still works after you cancel the subscription.

สิ่งที่ภัทรคิดวนอยู่คือ สุดท้ายแล้วคอร์สทั้งสามก็คือ funnel ของใครบางคนค่ะ ซึ่งก็ไม่เป็นไร คำถามไม่ใช่ว่าคอร์สฟรีเป็นการตลาดไหม เพราะมันเป็นเสมอ แต่คำถามคือสิ่งที่มันสอนเรายังใช้ได้อยู่ไหมหลังจากเรายกเลิก subscription ไปแล้ว

> Learn the framework, not the interface.

---

### Resources & Credits

**My own notes and posts**

- [Vibe Coding & Agentic AI: ChaiyoGCP & Build with AI Bangkok 2026 — my post](./gdg-buildwithai-2026.md)
- [GDG Cloud Bangkok 2026 — my raw notes](../notes/03-2026/gdg_cloud_bangkok_2026.md)
- [AI Fluency: Framework & Foundations — my notes](../notes/05-2026/ai_fluency_framework_foundations/README.md)
- [AI Fluency for Educators — my notes](../notes/08-2026/ai-fluency-for-educators.md)
- [AI Fluency for Students — my notes](../notes/08-2026/ai-fluency-for-students.md)

**The courses and the programme**

<!-- TODO: add the Anthropic Skilljar catalogue link, and the specific TH-AI Passport learning module you took. -->

- [TH-AI Passport — official FAQ (aipass.go.th)](https://aipass.go.th/faq)

**Sources cited in section 5 — what other people ran into**

These are other people's reports and reviews, not mine. Linked so you can read them yourself rather than take my summary for it.

นี่คือรายงานและรีวิวของคนอื่น ไม่ใช่ของภัทรค่ะ ใส่ลิงก์ไว้ให้ไปอ่านเองได้ ไม่ต้องเชื่อบทสรุปของภัทร

- [โซเชียลฯ ถล่ม! "TH-AI Passport" ภาพเจนสุดหลอน! ตั้งคำถามงบ 1,600 ล้านคุ้มค่าหรือไม่? — MGR Online](https://mgronline.com/onlinesection/detail/9690000086185)
- [ผู้ใช้ TH-AI Passport แชร์ผลงานสร้างภาพ พบข้อความภาษาไทยเพี้ยนจนอ่านไม่ออก — iPhone-Droid](https://www.iphone-droid.net/th-ai-passport-thai-text-image-errors/)
- [ข้อจำกัด TH-AI Passport ที่หลายคนอาจจะยังไม่รู้ — MeMarketThink](https://www.memarketthink.com/post/th-aipassport)
- [Natthaphong says 1.6bn-baht TH-AI Passport poor value, raises concerns over restrictions — Khaosod English](https://www.khaosodenglish.com/politics/2026/09/01/natthaphong-says-1-6bn-baht-th-ai-passport-poor-value-raises-concerns-over-restrictions/)
- [TH-AI Passport tops 1m sign-ups as minister defends data safeguards — The Nation](https://www.nationthailand.com/business/tech/40070079)
- [เสียงสะท้อน TH-AI Passport วันแรก มีประโยชน์ แต่ยังไม่ตอบโจทย์ทุกงาน — The Standard](https://thestandard.co/th-ai-passport-first-day-feedback/)
- [ทดลองใช้ AI Pass !! ปชช.แห่ รีวิวผลงานการ gen รูปด้วย TH-AI Passport — YouTube](https://www.youtube.com/watch?v=_FquN1jB9aY)
- [รีวิว TH-AI Passport — YouTube](https://www.youtube.com/watch?v=8cAg8oVpcCg) <!-- TODO: confirm this video's actual title and channel; I could not read it. -->

<!-- TODO: insert TH-AI Passport video here. GitHub markdown will not inline-play a local file — either upload the video to a GitHub comment and paste the resulting URL, or use a thumbnail image linking out. -->

---

tags:

- AIPassportTH
- Anthropic
- AIFluency
- PromptEngineering
- AILiteracy
- LearningInPublic
- ThaiTech
- GDGCloudBangkok

---

Written by Pat (Napatchol) | Full-Stack Developer
