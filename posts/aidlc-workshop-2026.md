---
title: "AI-DLC: Plan, Approve, Execute — What I Took from AWS's AI-Driven Development Lifecycle"
date: 2026-11-22
summary: "A recap of an AWS AI-DLC session: spec-driven development in Kiro, the AI-DLC phases, a worked example, pros and cons, and how I'd adapt it for my team and for AI Skill Wars."
tags: [events, ai, aws, kiro, workflow]
maturity: raw-note
lang: [en, th]
---

# AI-DLC: Plan, Approve, Execute

> สรุปจาก session AI-DLC ของ AWS — ส่วนที่ภัทรจดไว้ เติมด้วย docs ทางการ และวิธีที่ภัทรจะเอาไปใช้กับทีม

วันศุกร์ที่ 20 พฤศจิกายน 2026 ภัทรไปเข้า workshop **AI-DLC (AI-Driven Development Life Cycle)** ของ AWS ซึ่งเป็น workshop ของการแข่งขัน **AI Skill Wars** ที่ทีมภัทรสมัครไว้ค่ะ ใน workshop ใช้ **Kiro** อย่างเดียว โพสต์นี้มีสามหน้าที่:

1. บันทึกว่าได้อะไรจาก session (ส่วนที่มาจากโน้ตภัทร)
2. เป็นเอกสารที่ภัทรใช้อธิบายให้ทีมฟัง ทั้งทีมที่ทำงานและทีมที่แข่ง **AI Skill Wars**
3. เทียบกับมุมของ content creator ที่ภัทรติดตาม ว่าเขาจัด flow การทำงานกับ AI ยังไง

โน้ตของภัทรในวันนั้นสั้นมาก ส่วนที่อธิบายเพิ่มจึงมาจาก [repo AI-DLC ของ awslabs](https://github.com/awslabs/aidlc-workflows) และ [docs ของ Kiro](https://kiro.dev/docs/specs/) ภัทรแยกให้ดูทุกจุดว่าอะไรมาจากโน้ต อะไรมาจาก docs และอะไรเป็นความเห็นของภัทรเองค่ะ

---

## 1. Two Ideas in One Session

โน้ตภัทรเขียนสองเรื่องปนกัน พอกลับมาอ่าน docs ถึงเห็นว่าเป็นสองระดับ:

- **Spec-driven development (Kiro)** คือ loop เล็กของ *หนึ่งฟีเจอร์*: `requirements.md → design.md → tasks.md → implement` แต่ละขั้นมีปุ่มให้คนอนุมัติก่อนไปขั้นถัดไป
- **AI-DLC** คือ *ทั้ง lifecycle* ตั้งแต่จับ intent ไปจนถึง deploy และ operate โน้ตภัทรสรุปไว้สั้น ๆ ว่า **Plan → Approve → Execute** และ **Intent → Unit → QA**

ความสัมพันธ์ที่ภัทรเข้าใจคือ AI-DLC เป็น *วิธีการ* ส่วน Kiro เป็น *เครื่องมือ* ตัวหนึ่งที่รันวิธีการนี้ได้ ตาม README ของ repo ตอนนี้ AI-DLC (v2.11.4) รันได้ใน Claude Code, Kiro CLI, Kiro IDE, Codex CLI, Cursor, opencode และ GitHub Copilot คือไม่ได้ผูกกับ Kiro ค่ะ

หลักที่ทั้งสองเรื่องใช้ร่วมกัน: **AI ไม่ได้เริ่มจากเขียนโค้ด แต่เริ่มจากถามและวางแผน แล้วรอคนอนุมัติ**

---

## 2. The Steps

![AI-DLC flow: intent, then Inception (reverse engineering for brownfield, requirements, design, units of work), human approves the plan, then Construction per unit (tasks, code and tests, build and test), human approves each unit, then Operation; steering files and hooks are always on](../assets/aidlc-2026-flow.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude จากโน้ตและ docs ของ AI-DLC ค่ะ ตัดรายละเอียดออกเยอะ ของจริงมี 5 phase และ 33 stage</sub>

**ขั้น 0 — Steering files (ทำครั้งเดียวต่อโปรเจกต์)**
ใน Kiro คือไฟล์สามไฟล์ใน `.kiro/steering/`: `product.md` (ทำเพื่อใคร ทำอะไร), `tech.md` (stack และข้อจำกัด), `structure.md` (โครงโฟลเดอร์และ convention) AI อ่านทุกครั้งโดยไม่ต้องสั่ง เหมือน `CLAUDE.md` หรือ `AGENTS.md` (Kiro รองรับ `AGENTS.md` ด้วย)

**ขั้น 1 — Intent และ Intent Capture Questions**
เราพิมพ์สิ่งที่อยากได้หนึ่งประโยค (ใน AI-DLC คือ `/aidlc <what you want>`) แล้ว AI *ถามกลับก่อน* ว่าใครใช้ เกณฑ์ไหนถือว่าผ่าน ข้อมูลมาจากไหน ภัทรว่าขั้นนี้สำคัญที่สุด เพราะคำถามที่ AI ถามคือคำถามที่ทีมควรถามตัวเองตั้งแต่แรกอยู่แล้วค่ะ

**ขั้น 2 — `requirements.md`**
เขียนเป็น user story และเกณฑ์ผ่านแบบ **EARS**: `WHEN [เหตุการณ์] THE SYSTEM SHALL [พฤติกรรม]` ข้อดีคือแต่ละบรรทัดแปลงเป็น test ได้ตรง ๆ หนึ่งบรรทัดเท่ากับหนึ่ง test

**ขั้น 3 — `design.md`**
architecture, sequence, error path และ test strategy ของฟีเจอร์นี้

**ขั้น 4 — Units of work**
ในโน้ตภัทรเขียนไว้ว่า *"Unit??? — something to separate work"* พอไปอ่าน glossary ถึงชัด: **Unit of work คือชิ้นงานที่ implement แยกกันได้** มีไฟล์บอกว่า unit ไหนพึ่ง unit ไหน (dependency graph) ใน AI-DLC มีคำว่า **Bolt** ด้วย คือรอบส่งงานที่รวม unit ที่พึ่งกันไว้ด้วยกัน ภัทรเทียบเองว่าใกล้กับ sprint แต่สั้นกว่า

**ขั้น 5 — `tasks.md`**
รายการงานย่อยที่ติ๊กได้ ใน Kiro ถ้ากดรันทุก task มันจะดู dependency แล้วรัน task ที่ไม่พึ่งกันพร้อมกันเป็น "waves"

**ขั้น 6 — Implement ทีละ unit → QA → Deploy**
เขียนโค้ดพร้อม test ทีละ unit แล้วรัน build & test ครั้งเดียวตอนจบ ปิดด้วย deploy และ operation (dashboard, alarm, feedback)

**ตลอดทาง — Hooks**
ในโน้ตภัทรเขียนว่า "IDE HOOKS (.kiro.md)" แต่ docs บอกว่าไฟล์จริงอยู่ที่ `.kiro/hooks/<id>.json` ค่ะ (ภัทรจดผิดเอง) hook ทำงานตาม event เช่น `FileSave`, `PromptSubmit`, `AgentStop` หรือ `PreToolUse` แล้วรันคำสั่ง (เช่น lint, test) หรือส่ง prompt ให้ agent ในโน้ตภัทรเขียนว่า *"standard together"* คือ hook ทำให้ทั้งทีมใช้มาตรฐานเดียวกันโดยไม่ต้องพึ่งความจำของแต่ละคน

---

## 3. A Worked Example (Simulated)

เพื่อให้เห็นหน้าตาของแต่ละไฟล์ ภัทรลองเขียนตามรูปแบบของ AI-DLC กับโจทย์เล็ก ๆ ค่ะ **ส่วนนี้เป็นการจำลองบนกระดาษ** ภัทรเขียนไฟล์เอง ไม่ได้รันเครื่องมือจริง

**Intent:** แจ้งเตือนคนในเขตหนึ่งของกรุงเทพฯ ทาง LINE เมื่อค่า PM2.5 สูง

**Intent capture questions** ที่ควรถูกถามก่อนเขียนอะไร:

1. ใครได้รับแจ้งเตือน — คนที่กดรับเอง หรือทุกคนในเขต?
2. ช่องทางไหน — LINE, เว็บ หรือทั้งสองอย่าง?
3. "สูง" คือเกินเท่าไร และใช้มาตรฐานของใคร?
4. ข้อมูลมาจากไหน อัปเดตบ่อยแค่ไหน?
5. เป็น greenfield หรือต้องต่อกับระบบเดิม?

**`requirements.md`** (EARS):

```text
R1. WHEN a resident sends "subscribe" to the LINE bot
    THE SYSTEM SHALL store their user ID for the district.
R2. WHEN the hourly PM2.5 reading is above the configured threshold
    THE SYSTEM SHALL send one alert to each subscriber.
R3. WHILE the reading stays above the threshold
    THE SYSTEM SHALL NOT send a second alert within 6 hours.
R4. IF the air-quality API does not answer
    THEN THE SYSTEM SHALL log the failure and send no alert.
```

**Units of work:** Unit A = การสมัครรับแจ้งเตือน (R1), Unit B = อ่านค่าฝุ่นและตัดสินใจแจ้งเตือน (R2–R4) สองชิ้นนี้คุยกันผ่านตาราง subscribers ตารางเดียว ตกลง **contract** ของตารางนี้ก่อน แล้วสองคนแยกกันทำได้เลย

**`tasks.md`:** A1 webhook + test R1 · B1 ดึงค่าพร้อม timeout + test R4 · B2 threshold และ cooldown 6 ชั่วโมง + test R2, R3

สิ่งที่ภัทรเห็นจากการลองเขียนคือ **R3 กับ R4 ไม่โผล่ ถ้าไม่มีขั้นถาม** ถ้าสั่ง AI ว่า "ทำ bot แจ้งเตือนฝุ่น" ตรง ๆ ได้ bot ที่ส่งข้อความทุกชั่วโมงตอนฝุ่นสูง และเงียบไปเลยตอน API ล่มค่ะ

---

## 4. Brownfield vs Greenfield

ในโน้ตภัทรจดไว้แค่สองคำนี้ ใน docs ของ AI-DLC ความต่างอยู่ที่ขั้นเดียว: **Reverse Engineering** จะรันเฉพาะ brownfield (มีโค้ดเดิมอยู่แล้ว) AI อ่านโค้ดเดิมแล้วสรุปเป็นเอกสารก่อน ถึงจะเริ่มเขียน requirements ส่วน greenfield (เริ่มจากศูนย์) ข้ามขั้นนี้ไป

ภัทรว่างานจริงของทีมส่วนใหญ่เป็น brownfield ขั้นนี้จึงน่าลองที่สุด ถึงไม่ใช้ AI-DLC ทั้งชุด การให้ AI อ่านโค้ดแล้วเขียน `structure.md` ให้ก่อนก็มีประโยชน์แล้วค่ะ

---

## 5. Pick the Ceremony by the Size of the Work

AI-DLC ไม่บังคับให้ทุกงานผ่าน 33 stage มี **workflow profile** ให้เลือกตามขนาดงาน ตัวอย่างจาก docs:

- `express` — requirements ชัดแล้ว ต้องการทางสั้นที่สุดไปถึงโค้ดและ test (7 stage)
- `poc` — แค่อยากรู้ว่าทำได้ไหม (5 stage)
- `bugfix` — bug ที่รู้แล้ว แก้พร้อม regression test (6 stage)
- `feature` — ฟีเจอร์ที่จะขึ้น production (30 stage)
- `enterprise` — งานที่ต้อง audit ได้ เช่นงานที่มี compliance (30 stage, ละเอียดสุด)

ฝั่ง Kiro ก็มีแบบเดียวกัน: spec แบบ requirements-first, design-first, **Quick Spec** (สร้างสามไฟล์รวดเดียว ไม่มีด่านอนุมัติ) และ bugfix spec ที่แทน `requirements.md` ด้วย `bugfix.md`

---

## 6. Pros and Cons

ส่วนนี้เป็นความเห็นภัทรค่ะ ไม่ได้มาจาก session

**ข้อดี**

- **AI ถามก่อนทำ** ช่องว่างใน requirement โผล่ตั้งแต่ขั้นแรก ไม่ใช่ตอน review PR
- **Review ถูกลง** อ่าน requirements 10 บรรทัดง่ายกว่าอ่าน diff 500 บรรทัด และถ้าแผนผิด ก็ผิดตั้งแต่ก่อนมีโค้ด
- **Context ไม่หายระหว่างทาง** ทุกการตัดสินใจอยู่ในไฟล์ คนใหม่หรือ session ใหม่ของ AI อ่านต่อได้
- **Test มีที่มา** EARS หนึ่งบรรทัดคือ test หนึ่งตัว สอดคล้องกับ TDD โดยธรรมชาติ
- **แบ่งงานให้คนหลายคนได้** เพราะ units มี dependency ชัด

**ข้อเสีย**

- **ช้าและกิน token สำหรับงานเล็ก** ถ้าใช้ profile ใหญ่กับงานแก้ข้อความหนึ่งบรรทัด ต้องเลือก profile ให้ตรง
- **Approval fatigue** ถ้าด่านเยอะเกิน คนจะเริ่มกด approve โดยไม่อ่าน ซึ่งแย่กว่าไม่มีด่าน เพราะได้ความรู้สึกว่าปลอดภัยโดยไม่มีอะไรรับประกัน
- **Spec drift** ถ้าแก้โค้ดตรง ๆ โดยไม่กลับไปแก้ spec เอกสารจะโกหกในไม่กี่สัปดาห์
- **เครื่องมือยังเปลี่ยนเร็ว** แค่ใน README ของ repo มีหมายเหตุว่าชื่อ flag ของ Kiro สลับกันระหว่างเวอร์ชัน 2.11.3 กับ 2.11.4 ถ้าทีมจะใช้ ต้อง pin เวอร์ชัน
- **ไม่ได้แทน judgement** AI เขียน requirements ให้สวยได้ แต่คนยังต้องรู้ว่าอะไรคือของที่ควรสร้าง

---

## 7. A View I Respect: "My Claude Code team" (thangman22)

thangman22 เป็น content creator สาย dev ที่ภัทรติดตามค่ะ [โพสต์นี้](https://www.facebook.com/share/p/1EbhkdAHwg/) ของเขาจัด Claude Code แบบที่ session หลัก *ไม่เขียนโค้ดเอง* แต่แจกงานให้ agent ย่อยแต่ละสาย (web-dev, app-dev, ai-engineer, devops, tester, feedback-triage, project-onboarder, simplifier) โดยใช้ `CLAUDE.md` เป็นตัว routing ทุกตัวที่เขียนโค้ดต้องผ่าน code-simplification ก่อนส่งงาน และ flow ปิดท้ายคือ **build → test → review → push**

ภัทรชอบที่สองแนวนี้ตอบคนละคำถามค่ะ:

- **AI-DLC ตอบว่า "ทำอะไรก่อนหลัง"** (lifecycle: plan → approve → execute)
- **โพสต์ของ thangman22 ตอบว่า "ใครทำ"** (ทีมของ agent แบ่งตามความถนัด)

ที่น่าสนใจคือมีจุดที่เห็นต่างกันด้วย docs ของ AI-DLC เขียนไว้ว่าการมี specialist แคบ ๆ เยอะ ๆ คือการสร้าง *handoff chain แบบ waterfall* ขึ้นมาใหม่ เลยใช้ agent น้อยตัวที่ทำได้กว้าง ("small mob, broad agents") ส่วนโพสต์ของ thangman22 แบ่งตามสาย แต่ให้ session หลักถือภาพรวมไว้ ภัทรตีความเองว่าสองแนวนี้ใช้ร่วมกันได้: ใช้ AI-DLC กำหนด *ลำดับ* และด่านอนุมัติ แล้วใช้ทีม agent ทำงานใน *ช่วง Construction* (การตีความนี้เป็นของภัทร ไม่ใช่ของ thangman22 หรือ AWS)

---

## 8. Adapting It to Dev Life

![Mapping: steering files are your README, onboarding doc and ADRs; intent capture questions are refinement; requirements.md is acceptance criteria written as tests; design.md is a design doc; a unit of work is a PR-sized slice; tasks.md is a PR checklist; an approval gate is code review moved before the code; hooks are pre-commit and CI checks](../assets/aidlc-2026-adapt.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude ค่ะ การจับคู่เป็นความเห็นของภัทร</sub>

สิ่งที่ภัทรเห็นตอนจับคู่คือ **แทบไม่มีไฟล์ไหนใหม่จริง ๆ** ทีมส่วนใหญ่มี acceptance criteria, design doc และ code review อยู่แล้ว ส่วนที่ AI-DLC เปลี่ยนคือ *ลำดับ*: ย้าย review ขึ้นมาก่อนโค้ด และให้ AI เป็นคนร่างเอกสารพวกนี้แทนเรา

**สำหรับทีมที่ทำงาน** ภัทรจะเสนอให้เริ่มทีละขั้น ไม่ใช่ใช้ทั้งชุด:

1. เขียน steering files (หรือ `AGENTS.md`) ให้ repo หลักก่อน ใช้ได้ทุกเครื่องมือ
2. เลือกฟีเจอร์ถัดไปหนึ่งอัน แล้วให้ AI เขียน `requirements.md` แบบ EARS ให้ทีมอ่านก่อนเขียนโค้ด
3. เทียบกับฟีเจอร์ที่ทำแบบเดิม ว่ารอบ review ลดลงไหม

**สำหรับ AI Skill Wars** (ทีม 3–4 คน รู้โจทย์จริงในวันแข่ง) ข้อเสนอข้างล่างเป็นความเห็นของภัทรคนเดียว ไม่ใช่แผนที่ทีมตกลงกันค่ะ:

1. **เตรียม `tech.md` กับ `structure.md` ไว้ก่อนวันแข่ง** stack กับโครงโปรเจกต์ตกลงกันได้ตั้งแต่ตอนนี้ เหลือ `product.md` ไว้เขียนตอนได้โจทย์
2. **วันแข่งใช้ profile เล็ก** (`express` หรือ `poc`) เวลาจำกัดเกินกว่าจะผ่าน 30 stage
3. **ใช้ intent capture questions เป็นช่วงคุยโจทย์ของทีม** ใช้เวลาสั้น ๆ ตอบคำถามพวกนี้ด้วยกันก่อนแยกย้าย
4. **หนึ่งคนหนึ่ง unit** ตกลง contract ระหว่าง unit ก่อน แล้วแยกกันทำ
5. **ตั้ง hook ไว้ล่วงหน้า** lint และ test ทำงานเองทุกครั้งที่ save จะได้ไม่ต้องคอยเตือนกันตอนเร่ง

---

## 9. What I'm Taking Back

- **ขั้นที่คุ้มที่สุดคือขั้นถาม** ถึงไม่ใช้เครื่องมือไหนเลย การให้ AI ถามคำถามก่อนลงมือ ก็ทำได้ด้วย prompt เดียว
- **"Unit" คือคำที่ภัทรไม่เข้าใจในห้อง** และเป็นคำที่สำคัญที่สุดสำหรับงานทีม เพราะมันคือวิธีแบ่งงานให้คนหลายคนทำพร้อมกันได้
- **ภัทรยังไม่ได้รัน AI-DLC กับงานจริง** นอกจากใน workshop ตัวอย่างในข้อ 3 เป็นการจำลองบนกระดาษ ข้อดีข้อเสียในข้อ 6 จึงเป็นสิ่งที่คาดไว้ ไม่ใช่ผลที่วัดได้ค่ะ

---

## Sources

- AI-DLC workflows (awslabs): [repo](https://github.com/awslabs/aidlc-workflows) · [phases and stages](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/04-phases-and-stages.md) · [workflow profiles](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/workflow-profiles.md) · [glossary](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/glossary.md)
- AWS blog: [AI-Driven Development Life Cycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- Kiro docs: [specs](https://kiro.dev/docs/specs/) · [steering](https://kiro.dev/docs/steering/) · [hooks](https://kiro.dev/docs/hooks/)
- thangman22: ["My Claude Code team"](https://www.facebook.com/share/p/1EbhkdAHwg/)
- Numbers (5 phases, 33 stages, stage counts per profile, v2.11.4) are from the AI-DLC docs, read 2026-11-22. This post is my notes, not the speakers' words.
