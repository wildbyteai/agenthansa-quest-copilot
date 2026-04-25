# Hackathon Submission Summary

*(Copy this text directly into the hackathon submission form)*

---

## Project Name

AgentHansa Quest Copilot

---

## One-Line Description

A lightweight Telegram-first Hermes skill that helps Chinese-speaking operators understand, plan, quality-check, and prepare submissions for AgentHansa alliance tasks — with explicit human confirmation at every submission decision.

---

## What It Does

`agenthansa-quest-copilot` is a Hermes/OpenClaw skill that transforms a general-purpose AI agent into a disciplined AgentHansa alliance task copilot. When the operator sends a task notification via Telegram, Hermes activates the skill which:

1. **Fetches full quest details** — never drafts from a short notification alone
2. **Extracts requirements in Chinese** — classifies must-do, nice-to-do, risk points, and unknowns
3. **Assesses feasibility** — decides whether the task is worth doing before any work starts
4. **Creates a bilingual execution plan** — Chinese workflow guidance + quest-required language for the deliverable
5. **Runs a compliance self-check** — PASS/FAIL on task requirements, content rules, proof readiness, and external facts
6. **Prepares proof documentation** — proof URL, evidence, and post-submission proof guidance
7. **Stops at an explicit human confirmation gate** — only submits after the operator types `确认提交`
8. **Handles grading without blind retry loops** — non-A grades are diagnosed and proposed fixes are presented for human approval

---

## Why It Matters

Most AI agents for task platforms act as black-box automations: they claim tasks, generate content, and submit without the operator understanding what happened or why. This leads to:

- Low-quality, spammy submissions that hurt alliance reputation
- Broken proof chains (no evidence of what was actually done)
- Automatic retry loops that waste effort on fundamentally flawed approaches
- Operators who can't explain or verify what the agent did

`agenthansa-quest-copilot` takes a different approach: it keeps the human in the loop at every meaningful decision, communicates in the operator's native language, generates verifiable proof, and stops before submission to let the human verify. It is a **copilot**, not an **autopilot**.

---

## How It Uses AgentHansa

The skill is designed specifically for the AgentHansa alliance task workflow:

- Triggered by AgentHansa quest notifications (`New Quest`, `🆕 New Quest`, `做任务`, `按任务流程执行`)
- Understands AgentHansa's proof requirements (`proof_url`, `comment_url`, `proof_image_urls`)
- Respects AgentHansa's spam policy and submission guidelines
- Aligns with AgentHansa's grading system (A/B/C/D/Spam) and handles feedback without blind resubmission
- Designed for the claim → execute → submit → verify → settle lifecycle

---

## How It Works with Hermes and Telegram

**Daily workflow (Chinese):**

1. Operator receives AgentHansa alliance task notification
2. Operator forwards or pastes it to Hermes via Telegram
3. Hermes activates `agenthansa-quest-copilot` skill
4. Skill responds in Chinese with status headers, requirement analysis, and execution plan
5. Operator executes manual steps (e.g., upvoting on ProductFeatHub, posting to LinkedIn)
6. Operator sends `确认提交` to confirm
7. Hermes submits and returns the proof URL

**Key design principle:** Telegram is the primary interface. All operator communication is Chinese by default. Final deliverables follow the quest's required language.

---

## Repository

https://github.com/wildbyteai/agenthansa-quest-copilot

---

## Demo Video

https://youtube.com/shorts/zWK2gd2SE1o

---

## What This Is NOT

- NOT an automatic task claimer or submitter
- NOT a spam or bulk-commenting tool
- NOT affiliated with or endorsed by AgentHansa
- NOT a replacement for the AgentHansa platform or documentation
- NOT a fully autonomous AI agent — it requires human confirmation before every submission

---

## Technical Stack

- Skill file: `SKILL.md` (plain Markdown, loadable into Hermes/OpenClaw)
- No external dependencies required
- No database, backend, or frontend
- Works with any agent that can read Markdown skill files
- Telegram is the user interface (via Hermes)

---

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Main skill file for Hermes/OpenClaw |
| `README.md` | Project overview and usage guide |
| `examples/telegram-chat-example.md` | Full Telegram chat walkthrough |
| `examples/sample-quest.md` | Demo quest for testing |
| `examples/sample-hermes-run.md` | Expected Hermes output |
| `examples/final-submission.md` | Submission package example |
| `examples/daily-trigger.md` | Daily trigger phrase patterns |
| `docs/screen-recording-plan.md` | Demo video shot-by-shot plan |
| `docs/submission-summary.md` | This file (hackathon submission text) |
