---
title: "The Two Ways a Gate Lies"
date: 2026-09-21
summary: "Building a security-first delivery flow, and catching two tools — then my own shipped gate — reporting success while missing the thing they were built to catch."
tags: [ai, workflow, security]
maturity: published
lang: [en, th]
---

# The Two Ways a Gate Lies

> Building a security-first delivery flow, and catching two tools — then my own shipped
> gate — reporting success while missing the thing they were built to catch.

<span lang="th">สร้าง flow การส่งงานที่เอาความปลอดภัยเป็นอันดับแรก แล้วจับได้ว่าเครื่องมือสองตัว — แล้วก็ gate ที่ภัทร merge ขึ้น production เอง — รายงานว่าผ่าน ทั้งที่พลาดสิ่งที่มันถูกสร้างมาเพื่อจับ</span>

I spent a day and a half turning a checklist of fifty saved tools into an actual delivery
flow — the kind with a security gate that cannot be skipped and has to leave evidence behind.
Three tools passed outright, one failed on defaults and only passed once reconfigured, one got
dropped back into the queue. That part is unremarkable. What made the day worth writing about is what the passing
tools did on the way to passing: **two of them reported success while being blind to the thing
they were supposed to check, and I shipped a third failure in the opposite direction myself —
on top of the very flow built to catch this kind of thing.**

<span lang="th">ภัทรใช้เวลาวันครึ่งเปลี่ยนลิสต์เครื่องมือที่เซฟไว้ 50 ตัว ให้กลายเป็น flow การส่งงานจริง — แบบที่มี security gate ที่ข้ามไม่ได้ และต้องทิ้งหลักฐานไว้ด้วย เครื่องมือสามตัวผ่านตรงๆ หนึ่งตัวพังตอนใช้ค่า default แต่ผ่านหลัง config หนึ่งตัวถูกโยนกลับเข้าคิว ส่วนนั้นไม่มีอะไรน่าเล่า แต่ที่น่าเล่าคือสิ่งที่เครื่องมือที่ "ผ่าน" ทำระหว่างทางไปสู่การผ่านนั้น **เครื่องมือสองตัวรายงานว่าสำเร็จ ทั้งที่มันมองไม่เห็นสิ่งที่มันควรต้องเช็ค แล้วภัทรก็ไปทำพลาดแบบตรงข้ามกันเองเป็นตัวที่สาม บน flow ที่สร้างมาเพื่อกันเรื่องแบบนี้โดยเฉพาะ</span>

## The one rule this flow is built on

The whole flow — fourteen steps across four movements, two loops, three enforcement tiers —
comes down to one sentence: **the tool may record; only a human may bless.** A security check
can fail a gate on its own authority. It can never pass one. A false alarm costs ten minutes.
A false pass costs a vulnerability that shipped with a green check as its only record.

<span lang="th">flow ทั้งหมด — 14 ขั้นตอน 4 ช่วง 2 loop 3 ระดับการบังคับ — สรุปได้เป็นประโยคเดียว: **เครื่องมือมีสิทธิ์แค่บันทึก มีแต่คนเท่านั้นที่ให้ผ่านได้** เครื่องมือ security check ตัดสินใจเองได้ว่าจะ fail gate แต่ตัดสินใจเองไม่ได้ว่าจะ pass การแจ้งเตือนผิดๆ เสียเวลาแค่สิบนาที แต่การ pass ผิดๆ อาจแปลว่ามีช่องโหว่หลุดออกไปพร้อม green check เป็นหลักฐานเดียวที่เหลืออยู่</span>

That rule sounds obvious written down. It got tested twice in one afternoon, by two different
tools I trialled for exactly this flow, and both times the tool's own printed output was the
thing arguing against the rule.

<span lang="th">เขียนออกมาแล้วฟังดูเป็นเรื่องพื้นฐานมาก แต่กฎนี้โดนทดสอบจริงสองครั้งในบ่ายเดียว จากเครื่องมือสองตัวที่ภัทรลองใช้เพื่อ flow นี้โดยเฉพาะ และทั้งสองครั้ง สิ่งที่พิมพ์ออกมาจากตัวเครื่องมือเองนั่นแหละ ที่กำลังแย้งกับกฎข้อนี้</span>

## The first way a gate lies: staying quiet

I trialled a tool called `repomix` — it packs a whole repository into one file so an agent can
read it in a single pass, and the reason it clears my "no employer code leaves the machine"
rule is that it claims to strip credential-shaped files before packing. I planted five kinds of
fake secret across six files — a GitHub token, a Slack token, an AWS access key, an AWS secret
key, both AWS values together, and an RSA private key block — and ran it.

<span lang="th">ภัทรลองเครื่องมือชื่อ `repomix` — มันรวมทั้ง repo ให้เหลือไฟล์เดียว เพื่อให้ agent อ่านได้ในรอบเดียว เหตุผลที่มันผ่านกฎ "โค้ดบริษัทห้ามออกจากเครื่อง" ของภัทรได้ เพราะมันอ้างว่าจะกรองไฟล์ที่มีลักษณะเป็น credential ออกก่อนแพ็ค ภัทรปลูก secret ปลอม 5 แบบใน 6 ไฟล์ — GitHub token, Slack token, AWS access key, AWS secret key, ทั้งสองตัวของ AWS อยู่ด้วยกัน และ RSA private key แล้วก็รันดู</span>

It caught two of six. The GitHub token and the Slack token got excluded, as promised. The
complete AWS key pair and the RSA private key went into the packed output **verbatim**, and the
tool printed:

<span lang="th">มันจับได้แค่ 2 จาก 6 GitHub token กับ Slack token ถูกกรองออกตามที่โฆษณาไว้ แต่ AWS key ทั้งคู่และ RSA private key หลุดเข้าไปในไฟล์ที่แพ็คออกมา **แบบเต็มๆ** และเครื่องมือขึ้นข้อความว่า</span>

```
✔ No suspicious files detected.
```

To make it worse in a way that matters: I put the same AWS key inside a real source file the
repo actually needs — not a file named `secret.ts` — and it still printed the same clean
checkmark, at line 30,000-something of a 361,000-token pack.

<span lang="th">ที่แย่กว่านั้นในแบบที่สำคัญคือ ภัทรเอา AWS key ตัวเดียวกันไปแปะไว้ในไฟล์ source จริงที่ repo ต้องใช้ — ไม่ใช่ไฟล์ที่ชื่อ `secret.ts` — แล้วมันก็ยังขึ้น checkmark สะอาดแบบเดิม อยู่ที่บรรทัดประมาณ 30,000 กว่าของไฟล์ที่แพ็คออกมา 361,000 token</span>

A few hours later, working through a different candidate at a different step, I hit the exact
same shape of failure. `dependency-cruiser` draws a module graph and can fail a build when code
crosses an architectural boundary it shouldn't — I gave it one rule: nothing in the app layer
may import from the legacy directory it's meant to replace. First run: **49 modules, no
violations found — while a deliberate violation was sitting right there in the code.** The
repo has roughly 360 TypeScript modules. It had resolved a compiler for about an eighth of them
and reported a clean bill of health for the whole thing anyway.

<span lang="th">อีกไม่กี่ชั่วโมงถัดมา ระหว่างลองเครื่องมืออีกตัวในขั้นตอนอื่น ภัทรเจอความล้มเหลวรูปแบบเดียวกันเป๊ะ `dependency-cruiser` วาดกราฟความสัมพันธ์ของโมดูล และทำให้ build fail ได้ถ้าโค้ดข้ามเส้นสถาปัตยกรรมที่ไม่ควรข้าม ภัทรตั้งกฎไว้ข้อเดียว: โค้ดชั้น app ห้าม import จาก legacy directory ที่กำลังจะถูกแทนที่ รอบแรก: **cruise ได้ 49 module ไม่พบการละเมิด — ทั้งที่ภัทรปลูกการละเมิดไว้ตรงนั้นจริงๆ** repo นี้มีโมดูล TypeScript ประมาณ 360 ตัว มัน resolve compiler ได้แค่ประมาณหนึ่งในแปดของทั้งหมด แล้วก็ยังรายงานว่าทุกอย่างสะอาดดี</span>

Both tools were telling the truth about what they checked. Neither was lying about what it
found. What they were both doing was **reporting success on the scope they could see, with
nothing in the output distinguishing that from success on the scope I asked for.** A green
checkmark does not carry its own denominator.

<span lang="th">ทั้งสองเครื่องมือไม่ได้โกหกเรื่องที่มันเช็ค และไม่ได้โกหกเรื่องที่มันเจอ สิ่งที่ทั้งคู่ทำเหมือนกันคือ **รายงานว่าสำเร็จ ในขอบเขตที่มันมองเห็น โดยไม่มีอะไรในผลลัพธ์บอกความต่างจากความสำเร็จในขอบเขตที่ภัทรต้องการจริงๆ** เครื่องหมายถูกสีเขียวมันไม่ได้บอกตัวหารของมันเองมาด้วย</span>

## The second way a gate lies: crying wolf

The fix for the first failure mode looks obvious once you've seen it twice: give the tool
something it must catch, and confirm it catches that specific thing, before you trust a clean
run. I wrote that rule into the flow that same afternoon — after I had already shipped a
security gate of my own that morning, using only half of it.

<span lang="th">ทางแก้ของความล้มเหลวแบบแรกดูชัดเจนมากพอเจอสองรอบ: เอาอะไรสักอย่างที่เครื่องมือ "ต้องจับได้" ไปให้มันลอง แล้วเช็คว่ามันจับได้จริงๆ ก่อนที่จะเชื่อผลรันที่สะอาด ภัทรเขียนกฎนี้เข้า flow ในบ่ายวันเดียวกันนั้นเอง — หลังจากที่ตอนเช้าของวันเดียวกัน ภัทร merge security gate ของตัวเองขึ้นไปแล้ว โดยใช้แค่ครึ่งเดียวของกฎนี้</span>

I'd shipped a real pre-commit gate to my own portfolio project: a hook that blocks a commit if
any TypeScript workspace fails to typecheck. I tested it the half-right way — planted a real
type error, watched the commit get refused, merged it. What I hadn't tested, because I hadn't
yet put it into words, was the other half: **does it stay quiet on code that is actually
fine?** I found out the next morning, checking something unrelated. On a completely clean
tree, the gate failed — on generated route types left over from before a framework upgrade, a
directory that CI's own typecheck step never even sees, because CI happens to typecheck before
it builds. My gate had been blocking every single commit since the moment it shipped, for a
reason that had nothing to do with the code being committed.

<span lang="th">ภัทร merge pre-commit gate จริงเข้า portfolio project ของตัวเอง: hook ที่จะบล็อกการ commit ถ้า TypeScript workspace ไหน typecheck ไม่ผ่าน ภัทรเทสแค่ครึ่งที่ถูก — ปลูก type error จริงเข้าไป ดูว่า commit ถูกปฏิเสธ แล้วก็ merge สิ่งที่ภัทรยังไม่ได้เทส เพราะตอนนั้นยังไม่ได้เขียนออกมาเป็นกฎด้วยซ้ำ คืออีกครึ่งหนึ่ง: **มันจะเงียบมั้ยตอนโค้ดโอเคจริงๆ?** ภัทรมารู้ตัวอีกทีเช้าวันถัดมา ระหว่างเช็คเรื่องอื่นที่ไม่เกี่ยวกันเลย บน tree ที่สะอาดสนิท gate ก็พัง — จากไฟล์ type ที่ generate ไว้ตั้งแต่ก่อนอัปเดต framework โฟลเดอร์ที่ typecheck step ของ CI เองยังไม่เคยเห็นด้วยซ้ำ เพราะ CI ดันจะ typecheck ก่อน build gate ของภัทรบล็อกทุก commit มาตั้งแต่วันที่ merge ขึ้นไปแล้ว ด้วยเหตุผลที่ไม่เกี่ยวอะไรกับโค้ดที่กำลัง commit เลย</span>

That is the same failure as `repomix` and `dependency-cruiser`, mirrored. They stayed quiet
when they should have objected. My gate objected when it should have stayed quiet. Both
directions train the same bad habit in a person: **stop trusting the checkmark, either because
it's too often right for the wrong reason, or too often wrong for a reason you can't be
bothered to chase down.** A gate that cries wolf gets `--no-verify`'d into irrelevance exactly
as fast as one that never barks at all.

<span lang="th">นี่คือความล้มเหลวแบบเดียวกับ `repomix` และ `dependency-cruiser` แค่กลับด้าน พวกมันเงียบตอนที่ควรจะแจ้งเตือน gate ของภัทรแจ้งเตือนตอนที่ควรจะเงียบ ทั้งสองทิศทางฝึกนิสัยแย่ๆ แบบเดียวกันในตัวคน: **เลิกเชื่อ checkmark ไม่ว่าจะเพราะมันถูกบ่อยเกินไปโดยเหตุผลผิดๆ หรือผิดบ่อยเกินไปจนขี้เกียจจะไล่หาสาเหตุ** gate ที่ตะโกนมั่วโดนสั่ง `--no-verify` จนไม่มีความหมายได้เร็วพอๆ กับ gate ที่ไม่เคยเห่าเลย</span>

## The check that actually catches both

The rule that survived the day isn't "test the tool." It's a pair, and a gate has to pass both
halves or it doesn't get called a gate:

<span lang="th">กฎที่รอดจากวันนั้นไม่ใช่แค่ "ลองเทสเครื่องมือดู" แต่เป็นคู่กัน และ gate ต้องผ่านทั้งคู่ ไม่งั้นเรียกว่า gate ไม่ได้</span>

1. **Give it something it must catch, and confirm it catches that specific thing.** Not "does
   it produce output" — does it name the actual planted problem.
2. **Give it something it must let through, on a tree that's genuinely clean, and confirm it
   stays silent.** Not "does it run without crashing" — does it produce zero findings when
   zero is correct.

<span lang="th">1. **เอาอะไรที่มัน "ต้องจับได้" ไปให้ลอง แล้วเช็คว่ามันจับสิ่งนั้นได้จริง** ไม่ใช่แค่ "มันมี output มั้ย" — แต่ต้องเรียกชื่อปัญหาที่ปลูกไว้ได้ถูกต้อง
2. **เอาอะไรที่มัน "ต้องปล่อยผ่าน" ไปให้ลองบน tree ที่สะอาดจริงๆ แล้วเช็คว่ามันเงียบ** ไม่ใช่แค่ "มันรันได้ไม่พัง" — แต่ต้องได้ผลลัพธ์เป็นศูนย์ปัญหา เมื่อศูนย์คือคำตอบที่ถูก</span>

Both checks together cost under a minute per tool. I ran the first one on my own gate, before
merging it, and skipped the second — the exact corner I'd just watched two other tools cut. The
flow's own rule caught the gap two days later, on a re-verification I only did because writing
this down forced me to check the thing I claimed rather than the thing I'd assumed.

<span lang="th">เช็คทั้งสองข้อรวมกันใช้เวลาไม่ถึงนาทีต่อเครื่องมือ ภัทรทำข้อแรกกับ gate ของตัวเองก่อน merge แต่ข้ามข้อสอง — มุมเดียวกับที่เพิ่งเห็นเครื่องมืออีกสองตัวข้ามไปเป๊ะ กฎของ flow เองจับช่องโหว่นี้ได้อีกสองวันถัดมา จากการ re-verify ที่ภัทรทำเพราะการเขียนบันทึกนี้บังคับให้ต้องเช็คสิ่งที่อ้างไว้จริงๆ แทนที่จะเช็คแค่สิ่งที่คิดว่าใช่</span>

## Where the rule held without a fight

Not everything that day needed a rescue. I ran a close cousin of this same test on a standard
called A11Y.md, which is supposed to make an agent generate accessible markup by default — and
it's worth naming because it guards against a related trap: trusting my own read of generated
code instead of running it.

<span lang="th">ไม่ใช่ทุกอย่างในวันนั้นที่ต้องมากู้ ภัทรทดสอบมาตรฐานชื่อ A11Y.md ด้วยแบบทดสอบที่คล้ายกัน — มาตรฐานที่อ้างว่าทำให้ agent generate markup ที่ accessible ได้เป็นค่า default — และมันควรค่าแก่การพูดถึง เพราะมันป้องกันกับดักอีกแบบที่เกี่ยวข้องกัน: การเชื่อสิ่งที่ตัวเองอ่านจากโค้ดที่ generate มา แทนที่จะลองรันดูจริงๆ</span>

I generated the same component twice, in two fresh agent sessions that never saw each other or
the checklist I'd score them against, with accessibility never mentioned in either prompt. One
session got a one-line pointer to the standard; the other didn't. The version without it shipped
five real defects — no Escape key, no focus trap, focus never returned to the button that opened
it. The version with the standard closed four of five, and I didn't just read the code and take
its word for it: I ran both components in an actual browser with real key presses and watched
the difference happen.

<span lang="th">ภัทร generate component เดียวกันสองรอบ ใน agent session ใหม่สองอันที่ไม่เห็นกันและไม่เห็น checklist ที่จะเอาไปให้คะแนน โดยไม่มีคำว่า accessibility อยู่ใน prompt เลยสักตัว session หนึ่งได้ลิงก์ไปหามาตรฐานหนึ่งบรรทัด อีกอันไม่ได้ เวอร์ชันที่ไม่มีมาตรฐานมีข้อบกพร่องจริง 5 อย่าง — กด Escape ไม่ได้ โฟกัสไม่ถูกดักไว้ข้างใน โฟกัสไม่กลับไปที่ปุ่มที่กดเปิดมันขึ้นมา เวอร์ชันที่มีมาตรฐานปิดได้ 4 ใน 5 และภัทรไม่ได้แค่อ่านโค้ดแล้วเชื่อไปเอง แต่เอา component ทั้งคู่ไปรันในเบราว์เซอร์จริง กดปุ่มจริง แล้วดูความต่างเกิดขึ้นเอง</span>

That's the version of this whole post's argument that actually worked on the first attempt:
don't trust the artifact, run the thing.

<span lang="th">นั่นแหละคือเวอร์ชันของข้อโต้แย้งทั้งบทความนี้ ที่ใช้ได้ผลตั้งแต่ครั้งแรก: อย่าเชื่อหลักฐานเฉยๆ ลองรันมันดูจริงๆ</span>

## What this doesn't prove

A day of trials is not a settled process, and I'd rather say so than let the tidy narrative
imply more than it earned. The screen-reader half of the accessibility trial is still
outstanding — a keyboard test is not a screen-reader test, and that half belongs to a human by
the flow's own rule, not to whichever agent ran the rest of it. Another candidate I measured
against real usage logs turned out not to be needed at all yet, which is its own small win: the
trigger for adopting it was written down before I looked at the data, and the data said no.
And a tool I'd installed weeks ago and never once run turned up false positives at nearly four
times my declared tolerance on default settings — 18.5 per 1,000 words against a ceiling of 5
— reachable, but only after I stopped assuming that "installed" and "in use" mean the same
thing.

<span lang="th">วันเดียวของการทดลองไม่ได้แปลว่ากระบวนการนิ่งแล้ว และภัทรอยากพูดตรงๆ แบบนี้มากกว่าปล่อยให้เรื่องเล่าที่เรียบร้อยดูดีเกินจริง ครึ่งหนึ่งของการทดลอง accessibility ที่เป็นการทดสอบด้วย screen reader ยังค้างอยู่ — การทดสอบด้วยคีย์บอร์ดไม่ใช่การทดสอบด้วย screen reader และครึ่งนั้นเป็นของมนุษย์ตามกฎของ flow เอง ไม่ใช่ของ agent ตัวไหนก็ตามที่ทำส่วนที่เหลือ เครื่องมืออีกตัวที่ภัทรวัดกับ log การใช้งานจริง กลับกลายเป็นว่ายังไม่จำเป็นต้องใช้เลยตอนนี้ ซึ่งก็ถือเป็นชัยชนะเล็กๆ ของตัวมันเอง: เกณฑ์การรับเข้ามาใช้ถูกเขียนไว้ก่อนที่จะดูข้อมูล แล้วข้อมูลก็บอกว่าไม่ต้อง ส่วนเครื่องมืออีกตัวที่ภัทรติดตั้งไว้เป็นสัปดาห์แล้วไม่เคยรันเลยสักครั้ง กลับพบผลบวกลวงมากเกือบ 4 เท่าของเกณฑ์ที่ตั้งไว้เมื่อใช้ค่า default — 18.5 ต่อคำพันคำ เทียบกับเกณฑ์ 5 — แก้ได้ แต่ต้องเลิกสมมติก่อนว่า "ติดตั้งแล้ว" กับ "ใช้งานจริง" เป็นเรื่องเดียวกัน</span>

None of that is a failure of the flow. It's what the flow is for: making the gap between
"I ran it" and "I checked what it actually did" visible enough to close, one tool at a time.

<span lang="th">ไม่มีอันไหนเป็นความล้มเหลวของ flow เลย มันคือสิ่งที่ flow มีไว้ทำ: ทำให้ช่องว่างระหว่าง "ภัทรรันมันแล้ว" กับ "ภัทรเช็คแล้วว่ามันทำอะไรจริงๆ" มองเห็นได้ชัดพอที่จะปิดมันได้ ทีละเครื่องมือ</span>
