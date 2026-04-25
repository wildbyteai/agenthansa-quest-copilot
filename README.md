# AgentHansa Quest Copilot

A lightweight Telegram-first Hermes skill for executing AgentHansa alliance tasks with discipline — not automation.

> This is a copilot, not an autopilot. Every submission goes through an explicit human confirmation gate.

## What Problem It Solves

When an operator receives an AgentHansa alliance task notification, they often face:

- Unclear requirements hidden in a short notification
- No structured way to assess feasibility before starting work
- Deliverables in a foreign language while the operator works in Chinese
- No compliance check before submission
- Agents that auto-submit and cause spam flags
- No proof documentation when submissions fail grading

This skill gives the operator a repeatable, mobile-friendly workflow that handles all four core tasks:

1. **任务理解** — Understand what the task requires, what the deliverable is, and what proof is needed
2. **执行计划** — Create a practical execution plan with clear human/agent separation
3. **质量检查** — Run a compliance self-check before any submission
4. **提交材料整理** — Assemble the final submission package with proof_url and confirmation

---

## How It Works with Hermes Agent

Load `SKILL.md` into your Hermes or OpenClaw agent. When you send a task notification or trigger phrase, the agent activates the copilot skill.

**Telegram-first usage flow:**

```
You (Telegram) → Hermes Agent → agenthansa-quest-copilot skill → Chinese analysis + plan → Your confirmation → Submission
```

**Trigger phrases:**

| Trigger | When to use |
|---------|-------------|
| `做任务` | Start the full task workflow |
| `按任务流程执行` | Same as above |
| `New Quest` / `🆕 New Quest` | A new task notification arrived |
| `帮我分析一下这个任务` | Paste a task and want analysis first |
| `准备提交` | Prepare submission package for an existing task |
| `确认提交` | Explicit submission approval |
| `resubmit` / `重新提交` | Handle grade feedback and resubmit |

---

## AgentHansa Alliance Task Workflow

```
任务通知 → 拉取详情 → 拆解要求 → 判断可行性 → 执行计划
    → 生成交付物 → 人工操作 → 合规自检 → Proof 准备
    → 最终提交包 → 确认「确认提交」→ 提交 → Grade 处理
```

**Every step outputs a mobile-friendly status header:**

```markdown
状态：<STATE>
任务：<short quest title>
阻塞：<none or blocker>
下一步：<next human/agent action>
```

**States:** `FETCHING_QUEST_DETAIL` | `ANALYZING_REQUIREMENTS` | `PLANNING` | `CREATING_DELIVERABLE` | `READY_FOR_REVIEW` | `WAITING_FOR_SUBMIT_APPROVAL` | `SUBMITTING` | `SUBMITTED` | `GRADE_HANDLING` | `BLOCKED`

---

## Language Strategy

| Context | Language |
|---------|----------|
| Status, analysis, risk, execution plan, handoff instructions | 中文 (Chinese) |
| Grade diagnosis, confirmation prompts | 中文 (Chinese) |
| Final deliverable (post, comment, article) | Quest-required language |
| Proof document | Quest-required language |

The operator workflow is always Chinese. Final deliverables follow the quest requirements.

---

## Installation

1. Clone this repository
2. Copy `SKILL.md` to your Hermes skill directory or load it directly
3. No additional dependencies required

---

## Configuration

No configuration file needed. The skill reads quest details from your Telegram messages to Hermes.

---

## Quick Start

**Step 1:** Send a task notification to Hermes via Telegram

```
按任务流程执行

🆕 New Quest: $50.00
Find and vote on 5 ProductFeatHub feature requests related to AI product needs. Post your reasoning on LinkedIn.
```

**Step 2:** Hermes fetches full quest details and responds in Chinese with:

- 任务摘要 (reward, deadline, goal)
- 要求拆解 (must-do / nice-to-do / risk points / unknowns)
- 执行判断 (可以做 / 有风险但可做 / 不建议做)

**Step 3:** Review the plan and execute manual steps (e.g., upvote, post)

**Step 4:** Hermes shows the deliverable draft and self-check

**Step 5:** If everything looks good, type `确认提交`

**Step 6:** Hermes submits and returns the proof URL

---

## Usage Examples

See `examples/` for:

- `telegram-chat-example.md` — Full Telegram chat from trigger to submission
- `daily-trigger.md` — Common trigger patterns for everyday use
- `sample-quest.md` — A safe demo quest for recording
- `sample-hermes-run.md` — Expected Hermes output
- `final-submission.md` — Final submission package example

---

## Proof Preparation Workflow

Every submission requires evidence. The skill helps you prepare:

```markdown
## 最终提交包
submission_content:
<exact content to submit>

proof_url:
<proof URL or pending>

evidence:
- <key evidence URLs/files>

checks:
- 任务要求：PASS/FAIL
- 内容要求：PASS/FAIL
- Proof：PASS/FAIL/UNKNOWN

remaining_risks:
- none / <list>
```

Proof must be real and accessible. Never use fake or private URLs.

---

## Quality / Anti-Spam Checklist

Before every submission:

```
## 自检
- 任务要求：PASS/FAIL
- 内容要求：PASS/FAIL
- Proof 准备：PASS/FAIL/UNKNOWN
- 外部事实：PASS/FAIL/UNKNOWN
- 剩余风险：none / <list>
```

**What this skill NEVER does:**

- Never auto-submits without `确认提交`
- Never invents metrics, partnerships, endorsements, or usage claims
- Never generates fake proof URLs
- Never treats `ok`, `继续`, or `看起来可以` as submission approval
- Never retries on non-A grades without human-approved fix
- Never performs bulk claiming or spamming

---

## Demo Video Plan

See `docs/screen-recording-plan.md` for a 2-3 minute shot-by-shot demo plan.

See `docs/submission-summary.md` for the English hackathon submission text.

---

## Limitations

- Requires Hermes or OpenClaw agent runtime
- Manual actions (posting, upvoting) require the operator's account access
- Cannot access AgentHansa directly — works as a guided workflow copilot
- Submission execution depends on available tools in your agent runtime

---

## Safety Notes

- Always fetch full quest details before executing from a notification
- Never submit without explicit `确认提交` confirmation
- Never invent proof URLs or claim unverified facts
- Treat live AgentHansa docs and quest pages as authoritative
- This skill formalizes local agent behavior — it does not replace platform rules

---

## 中文使用说明

本 skill 面向 **Telegram + Hermes** 日常工作流设计：

**使用流程：**

1. 在 Telegram 向 Hermes 发送任务通知或 `做任务`
2. Hermes 调用 skill，用中文返回任务分析
3. 执行人工步骤（如 LinkedIn 发帖、ProductFeatHub upvote）
4. Hermes 出配合交付物草稿并自检
5. 你确认后回复 `确认提交`
6. Hermes 执行提交并返回 proof URL

**核心四件事：**
- 任务理解 — 拆解要求，判断风险
- 执行计划 — 明确步骤，分离人工/AI 操作
- 质量检查 — 自检合规性
- 提交材料整理 — proof_url + submission_content

**不做什么：**
- 不自动提交
- 不伪造 proof
- 不批量刷任务
- 不替用户做无法验证的线上操作

---

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | Main skill file for Hermes/OpenClaw |
| `README.md` | This file |
| `VERSION` | Current version |
| `CHANGELOG.md` | Release history |
| `examples/sample-quest.md` | Demo quest |
| `examples/sample-hermes-run.md` | Expected Hermes output |
| `examples/final-submission.md` | Submission package example |
| `examples/daily-trigger.md` | Common trigger patterns |
| `examples/telegram-chat-example.md` | Full Telegram chat example |
| `demo/demo-script.md` | One-minute demo script |
| `docs/research-report.md` | Research and gap analysis |
| `docs/implementation-plan.md` | Implementation plan |
| `docs/screen-recording-plan.md` | 2-3 min demo video plan |
| `docs/submission-summary.md` | Hackathon submission text |
