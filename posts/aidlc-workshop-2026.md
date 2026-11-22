---
title: "AI-DLC: Plan, Approve, Execute — What I Took from AWS's AI-Driven Development Lifecycle"
date: 2026-11-22
summary: "Notes from the AWS AI-DLC workshop on using Kiro with AI-DLC: the steps, a worked example, grilling a requirements.md, brownfield vs greenfield, choosing the ceremony, pros and cons, ideas to swap with my team before AI Skill Wars, and how a junior or a one-person team can use it without overengineering."
tags: [events, ai, aws, kiro, workflow]
maturity: raw-note
lang: [en, th]
---

# AI-DLC: Plan, Approve, Execute

> โน้ตจาก workshop AI-DLC ของ AWS — ส่วนที่ภัทรจด เติมด้วย docs ทางการ และไอเดียที่อยากชวนทีมคุยแลกเปลี่ยนกันค่ะ

วันศุกร์ที่ 20 พฤศจิกายน 2026 ภัทรไปเข้า workshop **AI-DLC (AI-Driven Development Life Cycle)** ของ AWS ซึ่งเป็น workshop ของการแข่งขัน **AI Skill Wars** ที่ทีมภัทรสมัครไว้ค่ะ workshop นี้เน้นแนะนำ **Kiro** กับ AI-DLC แล้วให้ผู้เข้าร่วมลองใช้เองมากกว่าลงรายละเอียดลึก ส่วนในวันแข่งรอบสุดท้าย กติกาคือ **ใช้ได้แค่ Kiro** โดยผู้จัดให้ token pool มาใช้ร่วมกัน

ภัทรเขียนโพสต์นี้เพื่อสองอย่าง:

1. บันทึกสิ่งที่ได้จาก workshop
2. เป็นจุดเริ่มคุยกับทีม ทั้งทีมที่ทำงานและทีมที่แข่ง ภัทรไม่ได้มาบอกว่าทีมต้องทำแบบนี้ แค่อยากเอาสิ่งที่ได้ฟังมาแชร์ แล้วฟังว่าแต่ละคนคิดยังไงค่ะ

ในวันนั้นภัทรจดไว้เฉพาะคำที่อยากกลับมาค้นต่อ และจุดที่อยากเน้น โพสต์นี้จึงเป็นการตามค้นคำเหล่านั้นใน [repo AI-DLC ของ awslabs](https://github.com/awslabs/aidlc-workflows) และ [docs ของ Kiro](https://kiro.dev/docs/specs/) ตรงไหนที่เป็นความเห็นของภัทรเอง จะบอกไว้ค่ะ

---

## 1. Kiro and AI-DLC: Two Layers

คำที่ภัทรจดมามีสองเรื่องปนกัน พอกลับมาค้นใน docs ถึงเห็นว่าเป็นสองชั้น:

- **Spec-driven development (Kiro)** คือ loop เล็กของ *หนึ่งฟีเจอร์*: `requirements.md → design.md → tasks.md → implement` แต่ละขั้นมีปุ่มให้คนอนุมัติก่อนไปขั้นถัดไป
- **AI-DLC** คือ *ทั้ง lifecycle* ตั้งแต่จับ intent ไปจนถึง deploy และ operate ภัทรจดไว้ว่า **Plan → Approve → Execute** และ **Intent → Unit → QA**

AI-DLC เป็น *วิธีการ* ส่วน Kiro เป็น *เครื่องมือ* ที่รันวิธีการนี้ได้ ตาม README ของ repo ตอนนี้ AI-DLC (v2.11.4) รันได้ทั้งใน Kiro, Claude Code, Codex CLI, Cursor, opencode และ GitHub Copilot ใน Kiro ตั้งค่าด้วย `aidlc config --harness kiro` แล้วเลือก agent ชื่อ **aidlc** ในช่องแชท

หลักที่ทั้งสองชั้นใช้ร่วมกัน: **AI ไม่ได้เริ่มจากเขียนโค้ด แต่เริ่มจากถามและวางแผน แล้วรอคนอนุมัติ**

ถ้าดูดี ๆ นี่คือ SDLC ที่เราคุ้นอยู่แล้ว (requirement → design → build → test → deploy) แค่คนร่างแต่ละขั้นเปลี่ยนจากคนเป็น AI ตรงกับที่คุณ thangman22 (Co-Founder และ Chief Product Officer ของ Wisesight และ Google Developer Expert สาย Web Technologies) เขียนไว้ว่า:

> "เรายังเชื่อนะว่า ต่อให้คนเขียน code จะเปลี่ยนไป แต่ SDLC เดิมก็ควรยังอยู่ไม่ใช่ทิ้งมันไปหมด"
>
> — thangman22

---

## 2. The Steps

![AI-DLC flow from left to right: intent with questions, then Inception (reverse engineering for brownfield, requirements, design, units of work), a human approval gate, Construction per unit (tasks, code and tests, build and test), a second gate, then Operation; steering files and hooks run underneath the whole flow](../assets/aidlc-2026-flow.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude จากโน้ตและ docs ของ AI-DLC ค่ะ ตัดรายละเอียดออกเยอะ ของจริงมี 5 phase และ 33 stage</sub>

**ขั้น 0 — Steering files (ทำครั้งเดียวต่อโปรเจกต์)**
ใน Kiro คือไฟล์สามไฟล์ใน `.kiro/steering/`: `product.md` (ทำเพื่อใคร ทำอะไร), `tech.md` (stack และข้อจำกัด), `structure.md` (โครงโฟลเดอร์และ convention) AI อ่านทุกครั้งโดยไม่ต้องสั่ง เหมือน `CLAUDE.md` หรือ `AGENTS.md` (Kiro รองรับ `AGENTS.md` ด้วย)

**ขั้น 1 — Intent และ Intent Capture Questions**
เราพิมพ์สิ่งที่อยากได้หนึ่งประโยค (`/aidlc <what you want>`) แล้ว AI *ถามกลับก่อน* คำถามถูกเขียนลงไฟล์ และแต่ละข้อมีป้ายบอกว่าใครควรตอบ เช่น `[Product owner]` หรือ `[Developer]` เราเลือกได้ว่าจะตอบแบบให้ AI พาถามทีละข้อ (Guide me), เขียนตอบในไฟล์เอง (Edit file) หรือคุยกันแล้วให้ AI สรุปเอง (Chat) ภัทรว่าขั้นนี้สำคัญที่สุด เพราะคำถามที่ AI ถามคือคำถามที่ทีมควรถามตัวเองตั้งแต่แรกอยู่แล้วค่ะ

**ขั้น 2 — `requirements.md`**
เขียนเป็น user story และเกณฑ์ผ่านแบบ **EARS**: `WHEN [เหตุการณ์] THE SYSTEM SHALL [พฤติกรรม]` ข้อดีคือแต่ละบรรทัดแปลงเป็น test ได้ตรง ๆ หนึ่งบรรทัดเท่ากับหนึ่ง test

**ขั้น 3 — `design.md`**
architecture, sequence, error path และ test strategy ของฟีเจอร์นี้

**ขั้น 4 — Units of work**
ในโน้ตภัทรเขียนไว้ว่า *"Unit??? — something to separate work"* พอไปอ่าน glossary ถึงชัด: **Unit of work คือชิ้นงานที่ implement แยกกันได้** มีไฟล์บอกว่า unit ไหนพึ่ง unit ไหน (dependency graph) AI-DLC ยังมีคำว่า **Bolt** คือรอบส่งงานที่รวม unit ที่พึ่งกันไว้ด้วยกัน ภัทรเทียบเองว่าใกล้กับ sprint แต่สั้นกว่า

**ขั้น 5 — `tasks.md`**
รายการงานย่อยที่ติ๊กได้ ใน Kiro ถ้ากดรันทุก task มันจะดู dependency แล้วรัน task ที่ไม่พึ่งกันพร้อมกันเป็น "waves"

**ขั้น 6 — Implement ทีละ unit → QA → Deploy**
เขียนโค้ดพร้อม test ทีละ unit แล้วรัน build & test ครั้งเดียวตอนจบ ปิดด้วย deploy และ operation (dashboard, alarm, feedback)

ช่วงนี้คือช่วงที่ "ใครเป็นคนลงมือ" สำคัญ ใน [โพสต์ "My Claude Code team"](https://www.facebook.com/share/p/1EbhkdAHwg/) thangman22 ให้ session หลักไม่เขียนโค้ดเอง แต่แจกงานให้ agent แต่ละสาย (web-dev, app-dev, devops, tester ฯลฯ) โดยใช้ `CLAUDE.md` เป็นตัว routing และปิดด้วย **build → test → review → push** ภัทรมองว่าสองแนวนี้ต่อกันได้: AI-DLC กำหนด *ลำดับ* และด่านอนุมัติ ส่วนทีม agent ตอบว่า *ใครทำ* แต่ละ unit (การต่อกันแบบนี้เป็นการตีความของภัทรค่ะ) มีจุดที่ต้องระวังด้วย docs ของ AI-DLC เขียนไว้ว่าการมี specialist แคบ ๆ เยอะเกินไปคือการสร้าง *handoff chain แบบ waterfall* ขึ้นมาใหม่ เลยเลือกใช้ agent น้อยตัวที่ทำได้กว้าง ("small mob, broad agents")

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

## 4. When You Only Have a `requirements.md`

บ่อยครั้งเราไม่ได้เริ่มจากศูนย์ แต่มี requirement ที่ใครสักคนเขียนไว้แล้ว อาจเป็น ticket, PRD หรือ `requirements.md` ที่เขียนเร็ว ๆ คำถามคือจะ *grill* มันยังไงให้เจอช่องโหว่ก่อนเริ่ม design ภัทรเห็นสองทางที่ใช้ร่วมกันได้ค่ะ

**ทาง Kiro — ใช้ spec เป็นตัว grill**
เปิด spec แบบ **requirements-first** แล้วให้ไฟล์ที่มีเป็นจุดตั้งต้น สั่งให้ Kiro เขียนใหม่เป็น EARS และกว่าจะผ่านไป design ได้ เราต้องกดอนุมัติ requirements ก่อน ช่วงก่อนกดอนุมัตินี่แหละที่ใช้ grill ได้ เช่นสั่งว่า *"อย่าเพิ่งไป design ให้ list สิ่งที่ requirement นี้ยังไม่ได้ตอบ เป็นคำถาม"* (prompt นี้เป็นของภัทรเองค่ะ)

**ทาง AI-DLC — ให้ Intent Capture และ Requirements Analysis ถาม**
ตาม docs ส่งไฟล์เข้าไปได้ตรง ๆ:

```text
/aidlc Read ./requirements.md and build what it describes
```

AI-DLC จะอ่านไฟล์ แล้วเขียนคำถามที่ไฟล์ยังไม่ได้ตอบลงไฟล์คำถาม (ติดป้ายว่าใครควรตอบ) ก่อนจะเขียน requirements ฉบับที่อนุมัติได้ docs แนะนำให้มีหัวข้อ **"Open questions"** ในเอกสารที่ส่งเข้าไปด้วย เพราะ AI-DLC จะเปลี่ยนมันเป็นคำถามตั้งแต่ต้น แทนที่จะไปโผล่เป็นเรื่องเซอร์ไพรส์ตอน design

**Checklist ที่ภัทรใช้ grill เอง** (ไล่ตามรูปแบบของ EARS แต่ละแบบตอบคำถามคนละอย่าง):

- **`WHEN`** — มีเหตุการณ์ไหนที่ระบบต้องตอบสนอง แต่ยังไม่มีบรรทัดไหนพูดถึง?
- **`WHILE`** — ระบบอยู่ในสถานะไหนได้บ้าง และพฤติกรรมเปลี่ยนไหมในแต่ละสถานะ? (R3 ในตัวอย่างมาจากคำถามนี้)
- **`IF … THEN`** — ถ้า API ล่ม, input ผิด หรือผู้ใช้ไม่มีสิทธิ์ ระบบทำอะไร? (R4)
- **`WHERE`** — มีฟีเจอร์ที่เปิด/ปิดได้ หรือใช้เฉพาะบางกลุ่มไหม?
- **`SHALL CONTINUE TO`** — อะไรที่ *ต้องไม่เปลี่ยน* (Kiro ใช้รูปนี้ใน bugfix spec สำหรับงานที่มีระบบเดิม)
- **วัดได้ไหม** — คำว่า "เร็ว", "ง่าย", "ปลอดภัย" แปลงเป็นตัวเลขหรือ test ได้หรือยัง?

ถ้าบรรทัดไหนเขียนเป็น test ไม่ได้ บรรทัดนั้นยังไม่ใช่ requirement ค่ะ

---

## 5. Brownfield vs Greenfield: Two Ways In

ใน workshop สองคำนี้ถูกพูดถึงเป็นจุดแยกทาง และใน docs ก็เป็นอย่างนั้นจริง สิ่งแรกที่ AI-DLC ทำหลังเรากด `/aidlc` คือ **Workspace Detection**: ดูว่าโปรเจกต์มีโค้ดอยู่แล้วหรือยัง คำตอบนี้เปลี่ยนว่าเราควรเตรียมอะไรเข้าไป และ flow จะเดินทางไหน

![Two lanes. Greenfield: write a short vision (what, for whom, in and out of scope, open questions), write steering files from decisions, then requirements, design, units, and build a walking skeleton first. Brownfield: write current state and what must not change, reverse engineering reads the code into nine documents, approve them, generate steering from the code, then requirements with unchanged-behaviour lines, and use the bugfix or refactor profile for small changes](../assets/aidlc-2026-brown-green.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude จาก docs ของ AI-DLC และ Kiro ค่ะ</sub>

**Greenfield (เริ่มจากศูนย์)**

1. **เขียน vision สั้น ๆ** docs แนะนำสี่หัวข้อ: กำลังสร้างอะไรให้ใคร, อะไรอยู่ในรอบแรก, อะไร *ไม่* อยู่ในรอบแรก และคำถามที่ยังไม่มีคำตอบ
2. **เขียน steering files จากการตัดสินใจ** ยังไม่มีโค้ดให้อ่าน `tech.md` กับ `structure.md` จึงเป็นสิ่งที่ทีมต้อง *ตกลงกัน* ไม่ใช่สิ่งที่ AI ไปค้นมา
3. **ข้าม Reverse Engineering** แล้วเดินตามขั้นปกติ: requirements → design → units
4. **ทำโครงกระดูกให้วิ่งได้ก่อน** AI-DLC มีตัวเลือกที่เรียกว่า *walking skeleton* คือทำเส้นทางบาง ๆ ที่วิ่งได้ตั้งแต่ต้นจนจบก่อน แล้วค่อยเติมเนื้อทีละ unit

**Brownfield (มีระบบเดิมอยู่แล้ว)**

1. **เขียนสภาพปัจจุบัน และสิ่งที่ต้องไม่เปลี่ยน** docs บอกว่าหัวข้อ *"What must NOT change"* สำคัญที่สุด เพราะ AI อ่านโค้ดได้ แต่ไม่รู้ว่าส่วนไหนห้ามแตะ มีแค่ทีมที่รู้
2. **Reverse Engineering** AI อ่านโค้ดแล้วเขียนเอกสาร 9 ไฟล์ (เช่น architecture, API, tech stack, code quality) เราตรวจและอนุมัติก่อน ถึงจะไปขั้น requirements
3. **ให้ AI ร่าง steering จากโค้ดที่มี** แล้วทีมตรวจ ส่วนนี้ประหยัดเวลาที่สุด เพราะ `structure.md` ของระบบเก่ามักไม่มีใครเขียนไว้
4. **Requirements ต้องมีบรรทัด "ไม่เปลี่ยน"** แบบ `SHALL CONTINUE TO` เพื่อกัน regression
5. **เลือก profile ให้เล็กตามงาน** แก้ bug ใช้ `bugfix` ปรับโครงสร้างโค้ดโดยพฤติกรรมไม่เปลี่ยนใช้ `refactor`

ภัทรว่างานจริงของทีมส่วนใหญ่เป็น brownfield ขั้นที่น่าลองก่อนจึงเป็น Reverse Engineering ถึงไม่ได้ใช้ AI-DLC ทั้งชุด แค่ได้เอกสารที่อธิบายระบบเดิมก็คุ้มแล้วค่ะ

---

## 6. Pick the Ceremony by the Size of the Work

*Ceremony* คือขั้นตอนที่ใส่ไว้เพื่อความปลอดภัย: จำนวนด่านอนุมัติ, เอกสารที่ต้องเขียนละเอียดแค่ไหน และ test ที่ต้องเข้มแค่ไหน ทีมเราทำแบบนี้อยู่แล้วโดยไม่ได้ตั้งชื่อ เช่นแก้คำผิดหนึ่งคำไม่ต้องเขียน design doc แต่เปลี่ยนระบบจ่ายเงินต้องมีคน review หลายรอบ

AI-DLC ทำให้การเลือกนี้ชัดขึ้น ถ้า ceremony มากเกินงาน ได้แต่ความช้าและ token ที่เสียไป และคนจะเริ่มกด approve โดยไม่อ่าน ถ้าน้อยเกินงาน ช่องโหว่ใน requirement จะไปโผล่ตอน production AI-DLC จึงไม่บังคับให้ทุกงานผ่าน 33 stage แต่มี **workflow profile** ให้เลือก และถ้าเราไม่เลือกเอง มันจะอ่านคำอธิบายงานแล้วเสนอ profile ให้เรายืนยันก่อนเริ่ม ตัวอย่างจาก docs:

- `poc` — แค่อยากรู้ว่าทำได้ไหม (5 stage)
- `bugfix` — bug ที่รู้แล้ว แก้พร้อม regression test (6 stage)
- `express` — requirements ชัดแล้ว ต้องการทางสั้นที่สุดไปถึงโค้ดและ test (7 stage)
- `refactor` — ปรับโค้ดโดยพฤติกรรมไม่เปลี่ยน (7 stage)
- `mvp` — ของจริงชิ้นแรก แต่ยังไม่ต้องมี operation (20 stage)
- `feature` — ฟีเจอร์ที่จะขึ้น production (30 stage)
- `enterprise` — งานที่ต้อง audit ได้ เช่นงานที่มี compliance (30 stage, ละเอียดสุด)

ฝั่ง Kiro ก็มีแบบเดียวกัน: spec แบบ requirements-first, design-first, **Quick Spec** (สร้างสามไฟล์รวดเดียว ไม่มีด่านอนุมัติ) และ bugfix spec

หลักที่ภัทรใช้เลือกเอง: **ถามว่าถ้าผิดแล้วแก้ยากแค่ไหน** ไม่ใช่ถามว่างานใหญ่แค่ไหน งานเล็กที่แตะ auth หรือ migration ควรได้ ceremony มากกว่างานใหญ่ที่เป็นแค่หน้า UI ใหม่ค่ะ

---

## 7. Pros and Cons

ส่วนนี้เป็นความเห็นภัทรค่ะ ไม่ได้มาจาก workshop

**ข้อดี**

- **AI ถามก่อนทำ** ช่องว่างใน requirement โผล่ตั้งแต่ขั้นแรก ไม่ใช่ตอน review PR
- **Review ถูกลง** อ่าน requirements 10 บรรทัดง่ายกว่าอ่าน diff 500 บรรทัด และถ้าแผนผิด ก็ผิดตั้งแต่ก่อนมีโค้ด
- **Context ไม่หายระหว่างทาง** ทุกการตัดสินใจอยู่ในไฟล์ คนใหม่หรือ session ใหม่ของ AI อ่านต่อได้
- **Test มีที่มา** EARS หนึ่งบรรทัดคือ test หนึ่งตัว สอดคล้องกับ TDD โดยธรรมชาติ
- **แบ่งงานให้คนหลายคนได้** เพราะ units มี dependency ชัด

**ข้อเสีย**

- **ช้าและกิน token สำหรับงานเล็ก** ถ้าเลือก profile ใหญ่เกินงาน
- **Approval fatigue** ถ้าด่านเยอะเกิน คนจะเริ่มกด approve โดยไม่อ่าน ซึ่งแย่กว่าไม่มีด่าน เพราะได้ความรู้สึกว่าปลอดภัยโดยไม่มีอะไรรับประกัน
- **Spec drift** ถ้าแก้โค้ดตรง ๆ โดยไม่กลับไปแก้ spec เอกสารจะโกหกในไม่กี่สัปดาห์
- **เครื่องมือยังเปลี่ยนเร็ว** แค่ใน README ของ repo มีหมายเหตุว่าชื่อ flag ของ Kiro สลับกันระหว่างเวอร์ชัน 2.11.3 กับ 2.11.4 ถ้าทีมจะใช้ ต้อง pin เวอร์ชัน
- **ไม่ได้แทน judgement** AI เขียน requirements ให้สวยได้ แต่คนยังต้องรู้ว่าอะไรคือของที่ควรสร้าง

---

## 8. Adapting It to Dev Life

![Mapping from AI-DLC and Kiro to what a team already has: steering files to README, onboarding doc and ADRs; intent capture questions to refinement; requirements.md to acceptance criteria written as tests; design.md to a design doc; a unit of work to a PR-sized slice; tasks.md to a PR checklist; an approval gate to code review moved before the code; hooks to pre-commit and CI checks](../assets/aidlc-2026-adapt.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude ค่ะ การจับคู่เป็นความเห็นของภัทร</sub>

ตอนจับคู่ ภัทรเห็นว่า **แทบไม่มีไฟล์ไหนใหม่จริง ๆ** ตรงกับคำของ thangman22 ข้างบนว่า SDLC เดิมยังอยู่ ทีมส่วนใหญ่มี acceptance criteria, design doc และ code review อยู่แล้ว สิ่งที่ AI-DLC เปลี่ยนคือ *ลำดับ*: ย้าย review ขึ้นมาก่อนโค้ด และให้ AI ร่างเอกสารพวกนี้แทนเรา

**ที่อยากชวนทีมที่ทำงานคุย** — ภัทรไม่ได้คิดว่าต้องใช้ทั้งชุด แต่อยากลองถามกันว่าขั้นไหนช่วยเราได้จริง เช่น:

- ถ้า repo หลักมี steering files (หรือ `AGENTS.md`) AI ที่แต่ละคนใช้จะเขียนโค้ดเข้ากับโปรเจกต์มากขึ้นไหม?
- ถ้าลองให้ AI เขียน `requirements.md` แบบ EARS ให้ทีมอ่านก่อนเริ่มฟีเจอร์ถัดไป รอบ review จะลดลงไหม?
- งานแบบไหนที่ทีมคิดว่าไม่คุ้มกับ ceremony เลย?

**สำหรับ AI Skill Wars** (ทีม 3–4 คน รู้โจทย์จริงในวันแข่ง วันแข่งใช้ได้แค่ Kiro และใช้ token pool จากผู้จัด):

1. **ซ้อมใน Kiro ตั้งแต่ตอนนี้** วันแข่งไม่มีเวลามาเรียนเครื่องมือ ให้ทุกคนคุ้นกับ spec, steering และ hook ใน Kiro ก่อน
2. **ใช้ token ให้คุ้ม** token pool มีจำกัด เลือก profile เล็ก (`express` หรือ `poc`) และใช้เวลาคิดกับคนมากกว่าให้ AI ร่างใหม่ซ้ำ ๆ
3. **เตรียม `tech.md` กับ `structure.md` ไว้ก่อน** stack กับโครงโปรเจกต์ตกลงกันได้ตั้งแต่ตอนนี้ เหลือ `product.md` ไว้เขียนตอนได้โจทย์
4. **เตรียม repo ส่วนตัวไว้ก่อน แล้วค่อย ๆ commit ขึ้น repo สาธารณะ** ข้อนี้มาจากพี่ที่ภัทรปรึกษาค่ะ เตรียมโครงและ steering ใน repo ส่วนตัวให้พร้อม แล้วทยอย commit ขึ้น repo สาธารณะทีละส่วน
5. **ใช้ intent capture questions เป็นช่วงคุยโจทย์** ใช้เวลาสั้น ๆ ตอบคำถามพวกนี้ด้วยกันก่อนแยกย้าย
6. **หนึ่งคนหนึ่ง unit** ตกลง contract ระหว่าง unit ก่อน แล้วแยกกันทำ
7. **ตั้ง hook ไว้ล่วงหน้า** lint และ test ทำงานเองทุกครั้งที่ save จะได้ไม่ต้องคอยเตือนกันตอนเร่ง

ทั้งหมดนี้เป็นไอเดียตั้งต้นให้ทีมคุยกันต่อค่ะ ใครเห็นต่างหรือมีวิธีที่ดีกว่า ภัทรอยากฟัง

---

## 9. Who Should Use It, and How Much

### Juniors: use it, but write before you read

ภัทรเป็น junior เอง เลยคิดเรื่องนี้เยอะค่ะ คำตอบของภัทรคือ **ควรใช้ แต่ใช้เป็นเครื่องฝึก ไม่ใช่ทางลัด**

ความเสี่ยงของ junior ไม่ใช่การใช้ AI-DLC แต่คือ **การกด approve สิ่งที่เรายังตัดสินไม่ได้** AI เขียน `design.md` ที่ดูดีได้เสมอ ถ้าเราไม่รู้ว่าทำไมมันเลือกแบบนั้น ด่านอนุมัติก็ไม่มีความหมาย และเราก็ไม่ได้เรียนอะไรจากมัน

วิธีที่ภัทรจะใช้เอง:

1. **เขียนเองก่อน แล้วค่อยให้ AI เขียน** ก่อนกด `/aidlc` ลองเขียน requirement 3–5 บรรทัด หรือตอบ intent questions ด้วยตัวเองก่อน แล้วค่อยเทียบกับของ AI ช่องว่างระหว่างสองฉบับคือสิ่งที่เราต้องเรียน (ตรงกับขั้น "recall before generate" ที่ภัทรเคยจดจาก LINE DEV Conf)
2. **อนุมัติเฉพาะสิ่งที่อธิบายได้** ถ้าอธิบายไม่ได้ว่าทำไม design ถึงเป็นแบบนี้ ให้ถาม AI กลับจนอธิบายได้ ก่อนกดผ่าน
3. **ฝึกที่ `requirements.md` ก่อน** EARS เป็นทักษะที่ใช้ได้ทุกที่ แม้วันที่ไม่ได้ใช้ AI-DLC แล้ว

**ไม่ให้กลายเป็น overengineering** — สัญญาณที่ภัทรใช้เตือนตัวเอง:

- เอกสาร spec ยาวกว่าโค้ดที่ได้
- เปลี่ยนแค่ 20 บรรทัด แต่ผ่านมาสามด่าน
- steering files ยาวกว่า README และไม่มีใครอ่านจบ
- กด approve ติดกันโดยไม่ได้อ่าน

หลักง่าย ๆ ของภัทร: **ถ้าอธิบายงานได้ในประโยคเดียว และย้อนกลับได้ใน commit เดียว ไม่ต้องมี spec** ให้ AI ถามคำถามเรา 3 ข้อก่อนลงมือก็พอ ถ้าไม่ใช่ ค่อยเปิด spec หรือ profile เล็ก (`express`, `bugfix`) แล้วขยายเมื่องานบังคับเท่านั้น

### Grill vs Spec

ภัทรใช้ทั้งสองอย่าง และเคยสับสนว่ามันต่างกันยังไง:

- **Grill** คือให้ AI ซักเรา ถามจี้ทีละข้อจนเจอจุดที่เรายังไม่ได้คิด (ภัทรใช้ skill ที่ทำหน้าที่นี้ใน Claude Code) ผลลัพธ์คือ *การตัดสินใจ* และความเข้าใจในหัวเรา
- **Spec** (ของ Kiro หรือ AI-DLC) คือ *เอกสาร* ที่ AI ร่าง คนอนุมัติ และเป็นตัวกำหนดว่าจะสร้างอะไร ผลลัพธ์คือไฟล์ที่คนอื่นและ AI session ถัดไปอ่านต่อได้

![Grill versus spec. Grill: AI questions you; the output is decisions in your head; best before you know what to build; cheap to throw away. Spec: AI drafts, you approve; the output is files others can read; best once you know what to build; it gates the build. Use grill to decide, then spec to record and build.](../assets/aidlc-2026-grill-spec.png)

<sub>ภาพนี้ภัทรสร้างด้วย Claude ค่ะ การเทียบเป็นความเห็นของภัทร</sub>

สองอย่างนี้ไม่ได้แข่งกัน **grill ใช้ตัดสินใจ spec ใช้บันทึกและสร้าง** ลำดับที่ภัทรใช้คือ grill ก่อน (ควรทำไหม ทำเพื่อใคร อะไรอยู่นอก scope) แล้วเอาคำตอบไปเป็น input ของ spec จริง ๆ แล้ว intent capture questions ของ AI-DLC ก็คือ grill รอบสั้นที่ฝังไว้ในขั้นแรกของ spec นั่นเองค่ะ ถ้าข้ามการ grill แล้วไปเปิด spec เลย AI จะช่วยเรา *สร้างสิ่งที่ยังไม่แน่ใจว่าควรสร้าง* ได้อย่างเป็นระเบียบมาก

### Side projects and the one-person team

ทั้ง side project และคนที่เป็น dev คนเดียวในบริษัท มีปัญหาเดียวกัน: **ไม่มีใครมา review** ด่านอนุมัติของ AI-DLC ตั้งอยู่บนสมมติฐานว่ามีคนอ่าน ถ้าคนอ่านคือเราคนเดียว ด่านต้องน้อยลง และทุกด่านที่เหลือต้องอ่านจริง

สิ่งที่ภัทรแนะนำ (จากการทำ side project ของตัวเอง ยังไม่ได้ลองกับ AI-DLC เต็มรูปแบบ):

1. **Steering files คุ้มที่สุด** เขียน `AGENTS.md` หรือ steering สามไฟล์ครั้งเดียว ได้ผลทุก session และใช้ได้ทุกเครื่องมือ ไม่ต้องใช้ Kiro ก็ได้
2. **Grill ตอนเลือกว่าจะทำอะไร spec ตอนทำของที่มีความเสี่ยง** side project ตายเพราะสร้างของที่ไม่มีใครใช้บ่อยกว่าเพราะโค้ดพัง ใช้ grill กับคำถาม "ควรทำไหม" ส่วน spec เก็บไว้ใช้กับงานที่แตะข้อมูล, auth หรือเงิน
3. **ใช้ profile เล็ก** `poc` สำหรับลองไอเดีย `mvp` เมื่อจะให้คนใช้จริง ข้าม Operation phase ไปก่อนจนกว่าจะมีผู้ใช้
4. **ให้ hook ทำหน้าที่แทน reviewer** lint, type check และ test ที่รันเองทุกครั้ง คือ reviewer ที่ไม่เหนื่อย
5. **ใช้ AI ตัวที่สองเป็น reviewer** ถ้าไม่มีคน ให้ AI จากอีกค่ายอ่าน diff หรือ spec แทน แต่ต้องตรวจสิ่งที่มันบอกเหมือนตรวจ comment ใน PR ไม่ใช่ทำตามทันที
6. **คนเดียวในบริษัท: spec คือเอกสารส่งต่อ** วันที่มีคนมาแทนหรือมาช่วย `requirements.md` กับ `design.md` คือสิ่งที่อธิบายว่าทำไมระบบเป็นแบบนี้ โดยไม่ต้องมีเราอยู่ด้วย (ลด bus factor) ข้อนี้ภัทรว่าคุ้มกว่าตอนมีทีมเสียอีก

---

## 10. What I'm Taking Back

- **ขั้นที่คุ้มที่สุดคือขั้นถาม** ถึงไม่ใช้เครื่องมือไหนเลย การให้ AI ถามคำถามก่อนลงมือ ก็ทำได้ด้วย prompt เดียว
- **"Unit" คือคำที่ภัทรไม่เข้าใจในห้อง** และเป็นคำที่สำคัญที่สุดสำหรับงานทีม เพราะมันคือวิธีแบ่งงานให้คนหลายคนทำพร้อมกันได้
- **ภัทรยังไม่ได้รัน AI-DLC กับงานจริง** นอกจากใน workshop ตัวอย่างในข้อ 3 เป็นการจำลองบนกระดาษ ข้อดีข้อเสียในข้อ 7 จึงเป็นสิ่งที่คาดไว้ ไม่ใช่ผลที่วัดได้ค่ะ

---

## Sources

- AI-DLC workflows (awslabs): [repo](https://github.com/awslabs/aidlc-workflows) · [phases and stages](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/04-phases-and-stages.md) · [workflow profiles](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/workflow-profiles.md) · [interaction modes](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/07-interaction-modes.md) · [writing a vision document](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/writing-inputs/vision-document-guide.md) · [glossary](https://github.com/awslabs/aidlc-workflows/blob/main/docs/guide/glossary.md)
- AWS blog: [AI-Driven Development Life Cycle](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)
- Kiro docs: [specs](https://kiro.dev/docs/specs/) · [steering](https://kiro.dev/docs/steering/) · [hooks](https://kiro.dev/docs/hooks/)
- thangman22: ["My Claude Code team"](https://www.facebook.com/share/p/1EbhkdAHwg/)
- Numbers (5 phases, 33 stages, stage counts per profile, v2.11.4) are from the AI-DLC docs, read 2026-11-22. This post is my notes, not the speakers' words.
