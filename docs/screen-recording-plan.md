# Screen Recording Plan

A 2-3 minute hackathon demo video showing how the AgentHansa Quest Copilot works through Telegram + Hermes.

**Total duration:** ~2 minutes 30 seconds
**Narration language:** English
**Screen language:** Chinese (Telegram workflow) + English (deliverables)

---

## Shot 1: Title & Problem Statement (0:00 – 0:20)

**Screen:** GitHub repository homepage (agenthansa-quest-copilot)

**Show:**
- README.md open
- Brief shot of the project description

**Narration:**
> "Every agent economy needs reliable task execution. I built `agenthansa-quest-copilot`, a Hermes skill that helps a Chinese-speaking operator complete AgentHansa alliance tasks with discipline — not automation."

**Cut to:** SKILL.md briefly open

**Narration (continued):**
> "It handles task understanding, planning, quality checking, and submission preparation. It never submits without me."

---

## Shot 2: Show The Skill Structure (0:20 – 0:50)

**Screen:** SKILL.md open, scroll through key sections

**Show:**
- Trigger phrases section (`做任务`, `New Quest`, `按任务流程执行`)
- Mobile-first status header
- 10-phase workflow overview
- Self-check PASS/FAIL format
- Confirmation gate with `确认口令：确认提交`

**Narration:**
> "The skill has natural Chinese and English triggers. When activated, it runs a 10-phase workflow — always in Chinese for me, always with a human confirmation gate before submission."

**Key text to flash:**
```
状态：WAITING_FOR_SUBMIT_APPROVAL
任务：Find and vote on 5 ProductFeatHub...
阻塞：等待用户确认
下一步：确认无误后回复「确认提交」
```

---

## Shot 3: Telegram — Task Trigger & Analysis (0:50 – 1:30)

**Screen:** Telegram chat with Hermes (simulated or real)

**Action 1 — User sends:**
```
帮我分析一下这个任务

🆕 New Quest: $50.00
Find and vote on 5 ProductFeatHub feature requests...
```

**Show Hermes responding with:**
- Status header (FETCHING_QUEST_DETAIL → ANALYZING_REQUIREMENTS)
- 任务摘要 (reward, deadline, goal)
- 要求拆解 (必须做 / 最好做 / 风险点)
- 执行判断 (可以做)

**Narration:**
> "I paste the task notification into Telegram. Hermes immediately activates the copilot skill, fetches the details, and analyzes the requirements — in Chinese, because that's how I work."

---

## Shot 4: Telegram — Execution Plan & Human Handoff (1:30 – 1:50)

**Screen:** Same Telegram thread, Hermes output continues

**Show:**
- 执行计划 (step-by-step)
- 需要你操作 section (Hermes clearly separates human actions)

**Narration:**
> "Hermes creates an execution plan and explicitly separates what I need to do manually — in this case, upvoting on ProductFeatHub — from what it handles."

---

## Shot 5: Telegram — Deliverable Draft + Self-Check (1:50 – 2:10)

**Screen:** Telegram thread, Hermes output shows LinkedIn post draft

**Show:**
- 交付物草稿 (English LinkedIn post, ~100 words)
- 自检 (all PASS)
- Proof 计划

**Narration:**
> "The deliverable is drafted in English — because that's what the quest requires — while the analysis stays in Chinese. A strict self-check runs before anything moves forward."

---

## Shot 6: Telegram — Confirmation Gate + Execution (2:10 – 2:25)

**Screen:** Telegram thread

**Show user types:**
```
确认提交
```

**Show Hermes responds:**
- SUBMITTING status
- ✅ Task submitted successfully!
- proof_url

**Narration:**
> "Submission only happens after I explicitly type '确认提交'. Hermes shows me the proof URL and stops to let me verify."

---

## Shot 7: GitHub Repo — Final Summary (2:25 – 2:30)

**Screen:** GitHub repository, examples/ folder open

**Show:**
- telegram-chat-example.md
- sample-hermes-run.md
- final-submission.md

**Narration:**
> "Everything is documented in the repo — including a full Telegram chat example, so this workflow is repeatable every day, not a one-shot demo."

---

## Recording Tips

- Use OBS or Loom for screen recording
- Record at 1080p minimum
- Use a phone-style Telegram window if possible (mobile-first demo)
- Keep Telegram text large enough to read on video
- Add a subtle cursor highlight for visibility
- Record narration separately and sync in post if needed (or use auto-ducking)
- Keep total under 3 minutes — hackathon judges prefer concise

## Post-Recording

1. Export video as MP4 (H.264, AAC)
2. Upload to YouTube/Vimeo (unlisted for review, public for submission)
3. Add link to repo README
4. Use the submission-summary.md for the hackathon form
