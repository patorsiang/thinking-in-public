---
title: "LINE DEV Conf 2026: What I'm Taking Back from a Day of AI Talks"
date: 2026-10-17
summary: "A curated recap of LINE DEV Conf 2026 at BITEC: LINE API's next frontier, LINE MAN Wongnai's AI transformation, harnesses and skills for coding agents, and what it means for a junior developer."
tags: [events, ai, line, agents]
maturity: raw-note
lang: [en, th]
---

# LINE DEV Conf 2026: What I'm Taking Back from a Day of AI Talks

> สรุปจาก LINE DEV Conf 2026 ที่ BITEC — เฉพาะส่วนที่ภัทรจดไว้และคิดว่าเอาไปใช้ต่อได้

วันเสาร์ที่ 17 ตุลาคม 2026 ภัทรไปงาน **LINE DEV Conf** ที่ BITEC ค่ะ agenda แบ่งเป็นสองสายที่เดินพร้อมกัน (Deep Tech Conference Hall กับ Real World Usecase) ภัทรจึงฟังได้เฉพาะบาง session โพสต์นี้จึง *ไม่ใช่* สรุปทั้งหมด แต่เป็น **ส่วนที่จดไว้ และคิดว่าหยิบไปทำต่อได้จริง**

มีเรื่องหนึ่งที่โผล่มาซ้ำจนสังเกตได้: หลาย session พูดเรื่องเดียวกันด้วยคนละชื่อ ว่า **การเขียนโค้ดไม่ใช่คอขวดอีกแล้ว** — คอขวดย้ายไปอยู่ที่การ review, การส่งต่องาน และการตกลงกันว่า "สำเร็จ" หน้าตาเป็นยังไง ชื่อ session หนึ่งอันก็พูดไว้ตรง ๆ (*The Bottleneck Moved*) ที่เหลือข้างล่างคือสิ่งที่ภัทรเห็นว่าแต่ละที่ตอบคำถามนี้ยังไง

![Two rows of boxes: before, write code is the widest step; with agents, review, handoffs and agreeing what done means are the widest](../assets/line-dev-2026-bottleneck-moved.svg)

<sub>ภาพประกอบที่ภัทรวาดเองจากภาพรวมของทั้งวัน ไม่ใช่ข้อมูลที่วัดจริงค่ะ ความกว้างของกล่องแค่แทน "แรงที่ใช้"</sub>

---

## 1. LINE API: What's Next

ช่วง Tech Keynote และ *LINE API Next-Frontier with Live Demo* พูดถึงทิศทางของแพลตฟอร์มค่ะ ใจความที่ภัทรจดไว้เป็นภาษาอังกฤษคือ *"delivering the agent to the user is the key point"* — แอปเชื่อมกับ agent ส่วนฝั่ง agent → ผู้ใช้ โน้ตบอกว่า "may be more advanced"

- **LINE MCP** ภัทรจดไว้ว่าอยากหาโอกาสใช้ แต่ยังไม่ได้ศึกษาค่ะ
- API ที่ชุมชนอายุ 9 ปีเรียกว่า "next frontier": **Mini Apps**, **Edit Event webhook** (ใช้ได้เฉพาะ group chat), **Rich Menu insight API** (รอมาประมาณ 2 ปี), **LIFF SDK** (ใช้ได้ทั้ง bot, web และ Mini Apps)
- ใน LIFF ขอให้ผู้ใช้ "เพิ่มเพื่อน" ได้เลย แล้วกลับมาที่ chatbot โดยไม่ต้องให้ผู้ใช้เสียจังหวะไปกด add friend แยก — เป้าหมายคือให้ **journey ไม่สะดุด**
- **In-app purchase** สำหรับ Mini Apps (เฉพาะแอปที่ verified แล้ว ยืนยันผ่านอีเมล)

---

## 2. MINI Eats: Two Companies, One Experience

*Building MINI Eats* โชว์สไลด์ MINI Eats Solution ที่แสดงฝั่ง LINE (MyCustomer CRM, Restaurant Home Page, OA Plus, Core Subscription) กับฝั่ง LINE MAN Wongnai (Mobile Ordering, Wongnai Merchant App, Wongnai POS CRM) แล้วเส้นประแบ่งสองบริษัทออกจากกัน

สไลด์ซ้อนสามชั้นทับบนไดอะแกรมเดียวกัน: **Seamless Experience** (ชั้น Mini App/LIFF), **Collaborative Ownership** (ชั้น service — ขอบเขตชัด ความเชี่ยวชาญเสริมกัน พัฒนาร่วมกัน) และ **Leverage** (ชั้น platform/integration) บทเรียนง่าย ๆ คือ ถ้า journey เดียวต้องต่อสองผลิตภัณฑ์จากสองบริษัท *ผู้ใช้ต้องไม่รู้สึกถึงรอยต่อ* และ **ขอบเขตความเป็นเจ้าของต้องชัด** ก่อนจะไปถึงเรื่องเร็วขึ้น 10 เท่า (สไลด์ถัดมาคือ *10x Faster: Lean Process, Embrace AI, Collaborate*)

![MINI Eats Solution slide: LINE and LINE MAN Wongnai components split by a dashed line, with Seamless Experience, Collaborative Ownership and Leverage layers](../assets/line-dev-2026-mini-eats-layers.jpg)

<sub>สไลด์ MINI Eats Solution จากเซสชัน *Building MINI Eats* โดยคุณ Siraphob Rhompo (LINE) ภาพถ่ายโดยภัทร ครอบเฉพาะหน้าจอค่ะ</sub>

---

## 3. LINE MAN Wongnai: From Implementation to Intent

คุณ Virot Chiraphadhanakul (VP of AI, LINE MAN Wongnai ตามที่ LINE Developers Thailand ระบุในโพสต์สรุปเซสชัน) เล่าเรื่อง *Driving AI Transformation* ค่ะ ตัวเลขที่ภัทรจดไว้คือ: **"80% AI-assisted, not shipped 80% faster"** (โน้ตไม่ได้บอกว่า 80% แรกวัดจากอะไร) ซึ่งตรงกับเรื่องคอขวดข้างบนพอดี

สไลด์ชุดที่ทำให้ภาพชัดคือสามคู่ "จาก → ไปสู่" แยกตามบทบาท:

| จาก | ไปสู่ | วิศวกร | PM | ดีไซเนอร์ |
|---|---|---|---|---|
| Implementation | **Intent** | เขียน spec และ test ให้ agent วนจนผ่าน | เปลี่ยน PRD เป็น transcript ปัญหาดิบ + เกณฑ์สำเร็จ | กำหนด constraint และ visual intent แทน wireframe ตายตัว |
| Delivery | **Discovery** | ลองหลาย implementation พร้อมกัน แล้วเก็บอันที่ใช้ได้จริง | เอา prototype ที่ใช้ได้ไปประชุม ไม่ใช่ pitch deck | ทำ mockup ด้วย AI เร็ว ๆ ให้ลูกค้าปรับ interface เอง |
| Content | **Knowledge** | จด architecture decision และบทเรียนจาก incident ไม่ให้ agent ผิดซ้ำ | — | เปลี่ยน feedback จาก review เป็นหลักการที่ agent ทำตามได้ |

ประโยคจากสไลด์ *Delivery to Discovery* ที่ภัทรจดไว้: **"when building is cheap, the risk is building the wrong thing"** — และในโน้ตภัทรเขียนว่า "like parking 5 versions to deliver" ซึ่งก็คือช่อง "ลองหลาย implementation พร้อมกัน" ข้างบนนี่เองค่ะ

อีกสองสไลด์ที่เกี่ยวกับ "ระบบรอบ ๆ" มากกว่าตัวโค้ด:

- **Make the Company Queryable** — ทุกการกระทำสำคัญทิ้ง artifact ไว้, ประชุมมี AI note, การคุยย้ายจาก DM/อีเมลไปอยู่ใน channel ที่ agent เข้าร่วมได้, และใครก็ถามข้อมูลได้ *โดยมี access control ตามระดับความเสี่ยง*
- **Open Loop → Closed Loop** — จาก "ตัดสินใจ ลงมือ แทบไม่วัด" เป็น "ดู output ส่งกลับเข้าไป ปรับ"

ทั้งหมดนี้รวมเป็นภาพ **AI Software Factories** ของเขา: คนกำหนดว่าสำเร็จหน้าตาเป็นยังไง agent สร้างและวนจนผ่าน และคนเข้ามาเฉพาะ *review gate* ที่การตัดสินใจมีความเสี่ยงจริง สไลด์ปิดชุดบอกว่าระบบที่ "ทดสอบและไว้ใจได้" ต้องมีสามอย่าง: **Verification, Observability, Review gates**

---

## 4. Harnesses: Making an Agent Follow the Rules

สามเซสชันพูดเรื่องเดียวกันจากสามมุมค่ะ

### Harness & Loop Engineering (คุณ Chokchai Faroongsarng, LINE)

สไลด์ที่ภัทรเก็บมาคือข้อความที่ว่า กฎใน AGENTS.md ต้อง **"decidable, not aspirational"** — ตัวอย่างในสไลด์คือ *inspect before edit*, *smallest safe diff*, *tests with changes*, *never bypass pre-commit gates (fix the cause)* คือกฎที่ตรวจได้ด้วยคำสั่ง ไม่ใช่คำขวัญ

ก่อน commit ต้องผ่านสี่ชั้น: **format & lint → unit → integration → E2E ก่อน push** และ "each step covers a gap the one before leaves; fast checks fail first" ในตัวอย่างของเขาเป็น stack ของ LINE เอง (Go, MongoDB, Kafka, APISIX) ซึ่ง stack ของแต่ละทีมจะต่างกัน แต่โครงเดียวกันเอาไปใช้ได้ นอกจากนั้นโน้ตภัทรมีอีกสามข้อจาก session นี้: **prompt caching proxy** เพื่อลด token, **อย่าข้าม test**, และ **โจทย์ท้าทายคือการทำ UI ด้วย agent** (Figma MCP + Storybook + Playwright) ซึ่งในงานนี้หมายถึงการเอา Figma มาตรวจผลลัพธ์ที่โค้ดสร้างออกมา

![Slide: What has to pass before a commit, four checks: format and lint, unit tests, integration tests, E2E tests before push](../assets/line-dev-2026-precommit-gates.jpg)

<sub>สไลด์ *What has to pass before a commit* จากเซสชัน Harness & Loop Engineering โดยคุณ Chokchai Faroongsarng (LINE) ภาพถ่ายโดยภัทร ครอบเฉพาะหน้าจอค่ะ</sub>

### How to Teach Your AI Agent with Agent Skills (คุณ Tanitphon Paniwan, Apppi)

สไลด์ภาษาไทยที่เทียบสองอย่างนี้: **SKILL = บอกวิธีทำ, HOOK = คุมจุดตรวจ** — เปลี่ยนจาก "ให้ model คิดวิธีเอง" เป็น "ทำตาม process ที่ออกแบบไว้" แนวคิดคือ **knowledge distillation สำหรับ agent**: agent ตัวใหญ่เขียน SKILL.md กับ hook ให้ agent ตัวเล็กที่เร็วกว่าทำตาม ถ้าตัวเล็กทำผิดก็ส่งกลับให้ตัวใหญ่ทำ retrospective แล้วสร้าง skill/hook ใหม่ใช้ในรอบถัดไป

![Slide: SKILL tells how, HOOK controls the checkpoint, with the .claude folder layout for each](../assets/line-dev-2026-skill-vs-hook.jpg)

<sub>สไลด์จากเซสชัน *How to teach your AI Agent with Agent skills* โดยคุณ Tanitphon Paniwan (Apppi) ภาพถ่ายโดยภัทร ครอบเฉพาะหน้าจอค่ะ</sub>

![Diagram: a big agent writes a skill and hook, a small agent does the task, the hook checks, and a failure goes back to the big agent for a retrospective](../assets/line-dev-2026-skill-hook-loop.svg)

<sub>วงจรนี้ภัทรวาดใหม่เองจากสไลด์และโน้ตของ talk นี้ค่ะ</sub>

และมีคำเตือนเรียกว่า **Skill Hell** — trigger ทับกัน, คำสั่งชนกัน, และต้องอ่านมากเกินก่อนจะเริ่มทำ

### AI Infrastructure at Speed (คุณ Kajornsak Peerapathananont, Fastwork)

เริ่มจากปัญหาที่เขาเรียกว่า *chasing AI*: API key ใครเป็นเจ้าของ ใช้ที่ไหน, ใครใช้ provider ไหน, บิลแยกกัน, ค่าใช้จ่ายเซอร์ไพรส์ ทางออกคือ **LiteLLM เป็น gateway เดียว** (virtual key ต่อทีม, budget, rate limit, model allow-list) + **Langfuse** ดู trace + **Onyx** (ความรู้ธุรกิจ) + **Sourcebot** (ค้นโค้ด) ประโยคปิดที่ดีคือ *"You probably don't need to build an AI platform from scratch"* — **adopt** เครื่องมือ, **build** ส่วนเชื่อม, **own** สถาปัตยกรรม governance และ developer experience

![Slide: What does an internal AI platform actually need? Access, models, knowledge, observability, cost, developer experience](../assets/line-dev-2026-ai-platform-needs.jpg)

![Slide: Summary architecture with engineers, non-engineers, and products going through a LiteLLM AI gateway to Anthropic, OpenAI and Google Vertex, with Onyx, Sourcebot and Langfuse around it](../assets/line-dev-2026-fastwork-architecture.jpg)

<sub>สไลด์จากเซสชัน *AI Infrastructure at Speed: Governance Without the Drag* โดยคุณ Kajornsak Peerapathananont (Fastwork) ภาพถ่ายโดยภัทร ครอบเฉพาะหน้าจอค่ะ</sub>

---

## 5. Review by Tier

ใน *The Bottleneck Moved* (คุณ Kittikorn Prasertsak, BorntoDev) ภัทรจดแนวคิด **review ตามระดับความเสี่ยง** ไว้ว่า:

1. ชั้น 1: agent review
2. ชั้น 2: developer ที่เกี่ยวข้องกับ change นั้น review
3. ชั้น 3 (เช่น payment): senior review

และอีกประโยคที่จดไว้: "everyone is a builder, but build a system that enables the process" — โน้ตยังมีคำถามเปิดไว้ว่า **TDD กับ agent ต้องทำยังไงเมื่องานเริ่มจาก Jira card** ซึ่งโน้ตทิ้งไว้เป็นคำถามเปิด

หลังงาน LINE Developers Thailand โพสต์[สรุปเซสชันนี้](https://www.facebook.com/share/p/14yvojpxg5X/) ไว้ ภัทรเลยเอามาเติมในส่วนที่โน้ตจดไม่ทัน (ด้านล่างเป็นการสรุปความด้วยภาษาของภัทรจากโพสต์นั้น ไม่ใช่สไลด์ของผู้บรรยายโดยตรง)

**โจทย์ของ talk:** ทีมเล็ก 3 คนที่ใช้ AI coding agent เปิด PR ได้ 40 งานต่อวัน จากเดิม 3-5 งาน คอขวดจึงย้ายไปอยู่ที่ *คนรีวิวและการเข้าใจระบบให้ทัน* เมื่อขยายคอขวดด้วยการเพิ่มคนไม่ได้ ทางออกคือ **ลดสิ่งที่ต้องไหลผ่านคอขวด** ด้วยสามเลเยอร์:

1. **Context**: ให้ agent รู้ขอบเขตและเหตุผลก่อนเขียน เช่น bounded module, AGENTS.md ที่สั้น, ADR ที่บันทึก *ว่าทำไม* และ contract/type ที่ฝังหน่วยกับข้อตกลงไว้ในโค้ด
2. **Guardrails**: ให้เครื่องกรองก่อนถึงมือคน เช่น strict types, คุมด้วยสิทธิ์และ hook ไม่ใช่แค่สั่งใน prompt (เช่น PreToolUse hook ดักคำสั่งอันตราย, deny การอ่าน `.env`, แยก credential ของ agent จากของ developer), TDD แบบแยกวงจร และเรียง CI gate แบบ fail-fast
3. **Orchestration**: จัดลำดับความเสี่ยงให้คนดูเฉพาะสิ่งที่ควรดู ด้วย canary / staged rollout, reviewer subagent ที่ได้ context ใหม่และเห็นแค่ diff เทียบกับเกณฑ์ใน PLAN.md และการแบ่ง review เป็นสามระดับ

**สามระดับของ review** (แบ่งด้วยสคริปต์ที่ดูว่าแก้ไฟล์อะไร เหตุผลคือถ้าคนกด Approve รัว ๆ ถึงครั้งที่ 10 ก็จะเริ่มกดผ่านโดยไม่อ่าน):

- **Tier 0** (~5 นาที): แก้เฉพาะ docs, test หรือ refactor ที่ไม่เปลี่ยนพฤติกรรม และ CI เขียวหมด อ่านแค่ intent
- **Tier 1** (~20 นาที): ฟีเจอร์ทั่วไปในโมดูลเดียว ใช้คนรีวิว 1 คน
- **Tier 2** (~30 นาที + staged rollout): แตะไฟล์สำคัญ เช่น contract, auth, migration, payment, prod config หรือลบ flag เจ้าของระบบต้องตรวจละเอียด

โน้ตของภัทรจดเป็น "agent → developer ที่เกี่ยวข้อง → senior (เช่น payment)" ซึ่งใกล้กับโพสต์ แต่ไม่เหมือนกันเป๊ะ: ในโพสต์ agent review เป็นด่านแรกของทุก PR ส่วนระดับแบ่งตามไฟล์ที่แตะ ภัทรไม่แน่ใจว่าความต่างนี้มาจากที่โพสต์สรุปไว้หรือจากที่ภัทรจดผิด

**คำถาม TDD กับ agent:** โพสต์ตอบทิศทางไว้ว่าอย่าให้ agent เขียนทั้งโค้ดและ test เอง เพราะเป็น "วงจรปิด" (test ผิดไปพร้อมโค้ดได้) และอ้างข้อมูลจาก ImpossibleBench ว่าโมเดลชั้นนำราวครึ่งหนึ่งมักแอบแก้ test ให้ผ่านเมื่อ test ขัดกับ spec ทางแก้คือเริ่มจาก test ที่แดงก่อน คนเป็นผู้อนุมัติ test และล็อกไฟล์ `/tests/spec/` ด้วย CODEOWNERS กับ deny rule ภัทรยังไม่รู้ว่าผู้บรรยายตอบเรื่อง "เริ่มจาก Jira card" ตรงกับที่ภัทรถามไว้หรือเปล่า

**วัดผล:** โพสต์ปิดด้วยการวัด 5 ตัวเลขทุกเดือน ได้แก่ PR cycle time, time to first review, PR size, change failure rate และสัดส่วน PR ที่ merge โดยไม่มีคนรีวิว เหตุผลคืองานวิจัยที่อ้างพบว่านักพัฒนา *รู้สึก* ว่าเร็วขึ้น 20% แต่วัดจริงช้าลง 19% (ตัวเลขทั้งหมดในส่วนนี้มาจากโพสต์ ภัทรไม่ได้ตรวจกับต้นทาง)

![Diagram: three review tiers rising with risk: an agent, the developer involved in the change, and a senior for things like payments](../assets/line-dev-2026-review-tiers.svg)

<sub>ภาพประกอบที่ภัทรวาดเองจากโพสต์สรุปของ LINE Developers Thailand ไม่ใช่สไลด์ของผู้บรรยายค่ะ</sub>

---

## 6. The Base Comes First

สองเซสชันนี้พูดถึง workflow และตัว *คน* มากกว่าเครื่องมือ

**The Scale Saga: From Specs to 10x Engineering** (คุณ Pathai Suwannawiwat, LINE) ปิดด้วยสไลด์สรุป workflow ใหม่หกขั้น: **Recall before generate → Visual with HTML → Explore together → Document decisions → Harness → Approve changes** โน้ตภัทรขยายขั้นแรกไว้ว่า "recall, predict, compare" — คือเดาผลก่อนให้ AI สร้าง แล้วเทียบ และขั้น "visual with HTML" คือทำ artifact/mock ให้เห็น UX/UI และฐานข้อมูลก่อนเขียนจริง

**The Human Advantage: Outperform The Algorithm** (คุณ Kasidis Satangmongkol, DataRockie) เป็นเซสชันสุดท้ายของวัน ใจความคือ AI เป็น **ตัวคูณ** ของฐานที่เรามีอยู่ และ **ต้องทำงานนั้นได้เองโดยไม่มี AI** (ประโยคเต็มที่ภัทรจดไว้อยู่ท้ายโพสต์)

---

## 7. What I'm Taking Back

ภัทรแยกเป็นสามเรื่องค่ะ

**ฝั่งตัวเอง (career):** หา *ตำแหน่ง* ของตัวเองในฐานะ dev และหา flow ของตัวเอง ใช้ AI หาคุณค่าที่แท้จริง แก้ปัญหา และสร้างความเชี่ยวชาญเฉพาะทาง: รู้ context ของ domain และต่อจุดได้ เพราะ criticism จะสำคัญขึ้น ลองบอก AI ให้ **challenge เราหรือ grill เรา** แทนที่จะให้แค่ตอบ และหาสนามซ้อมที่เป็นปัญหาจริง เช่น hackathon

โน้ตภัทรมีอีกส่วนที่ยังไม่ได้ผูกกับ talk ไหน: ผู้บรรยายยกการทดลองที่ให้ developer ทำงานแบบมี AI เทียบกับไม่มี AI โดยสมมติฐานคือ **ทักษะ debug และความรับผิดชอบต่อผลลัพธ์หายไปเมื่อใช้ coding agent** — ต้องเข้าใจ change ที่เกิดขึ้น ถามคำถามให้ถูก ประเมินผลกระทบ และรู้ว่าจะรับมือผลนั้นยังไง ภัทรไม่ได้จดรายละเอียดของการทดลองนั้น

มีงานวิจัยที่ใกล้เคียงให้อ่านต่อ แต่ภัทรไม่รู้ว่าเป็นชิ้นเดียวกับที่ผู้บรรยายอ้างหรือไม่: [Anthropic ทำการทดลองแบบสุ่ม](https://www.anthropic.com/research/AI-assistance-coding-skills) (เผยแพร่ 29 มกราคม 2026 และ Anthropic คือผู้ทำเครื่องมือที่ภัทรใช้อยู่) กับวิศวกร 52 คนที่เรียนไลบรารี Trio กลุ่มที่ใช้ AI ทำควิซได้เฉลี่ย 50% ส่วนกลุ่มเขียนเองได้ 67% และ **ช่องว่างใหญ่ที่สุดอยู่ที่คำถามเรื่อง debugging** ผู้เขียนเตือนเองว่ากลุ่มตัวอย่างเล็ก วัดความเข้าใจทันทีหลังทำงาน และยังตอบไม่ได้ว่าผลระยะยาวเป็นยังไง

**ฝั่งงาน:** ภัทรชอบงาน UI เลยสนใจโจทย์ UI กับ agent ที่ Harness & Loop พูดถึง (ใช้ Figma ตรวจผลลัพธ์ที่โค้ดสร้างออกมา) แต่ยังไม่ได้ลองค่ะ

**ฝั่งทีม:** ภัทรสรุป flow ใหม่ที่แต่ละ session เสนอเป็นสไลด์ เพื่อเอาไปคุยในทีมว่าหัวข้อไหนหยิบมาใช้ได้

สองเรื่องที่ภัทรยังจดได้แค่ผิวเผิน:

**Lockdown my sassy AI agent** (คุณ Neutron Soutmun, LINE) โน้ตจดเคส Hugging Face กับ exploitGym ไว้ว่าเป็นความเสี่ยงสูง ส่วนแนวป้องกันที่ภัทรจำได้คือ ตั้ง **gateway** ไม่ให้ agent ออกนอกเส้นทางที่กำหนด เพื่อปกป้องชื่อเสียงของบริษัท (จากความจำ ยังรอสไลด์) ถ้าสงสัยว่า ExploitGym คืออะไร: เป็น benchmark 898 ข้อจากช่องโหว่จริงใน userspace, V8 และ Linux kernel ที่ให้ AI agent ต่อยอดจาก input ที่กระตุ้นช่องโหว่ไปเป็น exploit ที่ใช้ได้ ([arXiv 2605.11086](https://arxiv.org/abs/2605.11086), พฤษภาคม 2026) ภัทรไม่รู้ว่าผู้บรรยายอ้างถึงงานชิ้นเดียวกันหรือไม่

**TDD กับ agent เมื่อเริ่มจาก ticket** เป็นคำถามที่ภัทรจดไว้จาก *The Bottleneck Moved* คำตอบทิศทางอยู่ในส่วน Review by Tier ข้างบน แต่ยังเหลือเรื่อง ticket ที่ภัทรอยากเอาไปลองจริง

> ทำสิ่งที่มีประโยชน์และมีคุณค่าเป็นฐานตั้งต้นไว้ (เช่น มีค่าเท่ากับ 1 หรือ 10) AI จะเข้ามาทำหน้าที่เป็น "ตัวคูณพลัง" ที่เปลี่ยนจากสิ่งเล็ก ๆ ให้กลายเป็น Impact มหาศาลได้ในทุก ๆ วัน

<sub>ใจความจาก *The Human Advantage* (คุณ Kasidis Satangmongkol, DataRockie) ที่ภัทรจดจากความจำ ไม่ใช่คำพูดของผู้บรรยายแบบคำต่อคำค่ะ</sub>

---

## Sources

- Agenda: [LINE DEV CONF 2026](https://www.line-website.com/linedevconf2026-agenda)
- Session summary of *The Bottleneck Moved*: [LINE Developers Thailand on Facebook](https://www.facebook.com/share/p/14yvojpxg5X/)
- Slides are photographed from the talks and credited to the speakers named above; this post is my notes, not the speakers' words.
