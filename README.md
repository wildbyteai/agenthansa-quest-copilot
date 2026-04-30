# AgentHansa Quest Copilot

A lightweight Telegram-first Hermes/OpenClaw skill for preparing AgentHansa alliance task deliverables with discipline — not automation.

> This is a copilot, not an autopilot. It never submits, resubmits, posts, votes, comments, or mutates external platforms. It only prepares a 100% compliant manual submission package.

## Core Safety Rules

### 1. Never auto-submit

The agent must never:

- submit or resubmit AgentHansa quests
- publish posts
- send comments or replies
- vote or upvote
- upload final proof
- click final submit buttons
- call submission APIs
- run shell commands that submit payloads
- use browser automation to complete a submission

If the user says `确认提交`, `提交`, `approved, submit`, or `resubmit this version`, the agent treats it as: **generate or refresh the manual submission package**.

### 2. Require 100% task compliance

The agent must not prepare a manual submission package unless every mandatory requirement is PASS.

If any mandatory requirement is missing, uncertain, partially satisfied, unverifiable, ambiguous, or marked UNKNOWN, the agent must output `BLOCKED` instead of a submission package.

---

## What Problem It Solves

When an operator receives an AgentHansa alliance task notification, they often face:

- Unclear requirements hidden in a short notification
- No structured way to assess feasibility before starting work
- Deliverables in a foreign language while the operator works in Chinese
- No strict compliance check before submission
- Agents that auto-submit and cause spam flags
- No proof documentation when submissions fail grading

This skill gives the operator a repeatable, mobile-friendly workflow that handles four core tasks:

1. **任务理解** — Understand what the task requires, what the deliverable is, and what proof is needed
2. **执行计划** — Create a practical execution plan with clear human/agent separation
3. **100% 质量检查** — Verify every mandatory requirement before a manual package is produced
4. **手动提交包整理** — Assemble `submission_content`, `proof_url`, evidence, checks, and manual submission steps

---

## How It Works with Hermes/OpenClaw

Load `SKILL.md` into your Hermes or OpenClaw agent. When you send a task notification or trigger phrase, the agent activates the copilot skill.

**Telegram-first usage flow:**

```text
You (Telegram) → Hermes/OpenClaw → agenthansa-quest-copilot skill
→ Chinese analysis + plan → deliverable draft → 100% compliance check
→ manual submission package → you submit manually
```

**Trigger phrases:**

| Trigger | Meaning |
|---------|---------|
| `做任务` | Start the full preparation workflow |
| `按任务流程执行` | Same as above |
| `New Quest` / `🆕 New Quest` | A new task notification arrived |
| `帮我分析一下这个任务` | Paste a task and analyze first |
| `准备提交` | Prepare or refresh a manual submission package |
| `确认提交` | Generate manual submission guidance, not auto-submit |
| `resubmit` / `重新提交` | Diagnose grade feedback and prepare a revised manual package |

---

## AgentHansa Alliance Task Workflow

```text
任务通知 → 拉取详情 → 拆解要求 → 判断可行性 → 执行计划
    → 生成交付物 → 人工操作 → 100% 合规检查 → Proof 准备
    → 手动提交包 → 用户本人提交 → Grade 处理
```

Every major response outputs a mobile-friendly status header:

```markdown
状态：<STATE>
任务：<short quest title>
阻塞：<none or blocker>
下一步：<next human/agent action>
```

**States:** `FETCHING_QUEST_DETAIL` | `ANALYZING_REQUIREMENTS` | `WAITING_FOR_INFO` | `PLANNING` | `CREATING_DELIVERABLE` | `DELIVERABLE_REVIEW` | `READY_FOR_REVIEW` | `READY_FOR_MANUAL_SUBMISSION` | `MANUAL_SUBMISSION_GUIDE` | `GRADE_HANDLING` | `BLOCKED`

Forbidden states: `SUBMITTING`, `SUBMITTED`.

---

## Language Strategy

| Context | Language |
|---------|----------|
| Status, analysis, risk, execution plan, handoff instructions | 中文 |
| Grade diagnosis, manual submission guidance | 中文 |
| Final deliverable | Quest-required language |
| Proof document | Quest-required language |

The operator workflow is always Chinese. Final deliverables follow the quest requirements.

---

## Installation

1. Clone this repository
2. Copy `SKILL.md` to your Hermes skill directory or load it directly
3. No additional dependencies required

---

## Configuration

No configuration file needed. The skill reads quest details from your Telegram messages to Hermes/OpenClaw.

---

## Quick Start

**Step 1:** Send a task notification to Hermes via Telegram

```text
按任务流程执行

🆕 New Quest: $50.00
Find and vote on 5 ProductFeatHub feature requests related to AI product needs. Post your reasoning on LinkedIn.
```

**Step 2:** Hermes fetches full quest details and responds in Chinese with:

- 任务摘要：reward, deadline, goal, proof
- 要求拆解：must-do / nice-to-do / risk points / unknowns
- 执行判断：可以做 / 有风险但可做 / 暂停，先补信息 / 不建议做

**Step 3:** Review the plan and perform human-only actions yourself, such as upvoting, posting, commenting, uploading proof, or submitting.

**Step 4:** Hermes shows the deliverable draft and 100% compliance check.

**Step 5:** If every mandatory requirement is PASS, Hermes prepares a manual submission package.

**Step 6:** You copy the package into AgentHansa and submit manually.

---

## Manual Submission Package

The skill only prepares a package like this:

```markdown
状态：READY_FOR_MANUAL_SUBMISSION
任务：<quest title>
阻塞：需要用户本人手动提交
下一步：请复制下方 submission_content 和 proof_url 到 AgentHansa 页面/API，由你本人手动提交

## 手动提交包

submission_content:
<exact content to submit>

proof_url:
<proof URL>

evidence:
- <key evidence URLs/files>

checks:
- 任务要求：PASS（100% mandatory requirements satisfied）
- 内容要求：PASS（language/platform/format/tone/length/links/tags/mentions/labels satisfied）
- Proof：PASS（required proof exists and is accessible）
- 外部事实：PASS（all factual claims verified or removed）

remaining_risks:
- none

## 手动提交步骤
1. 打开 AgentHansa 对应 quest 页面
2. 粘贴 submission_content
3. 填入 proof_url
4. 检查 evidence 是否完整
5. 由你本人点击提交

注意：agent 不会自动提交。
```

If any mandatory check is `FAIL` or `UNKNOWN`, the skill outputs `BLOCKED` instead.

---

## 100% Compliance Check

Before a manual package is produced:

```markdown
## 100% 任务符合性检查

| Requirement | Evidence | Status |
|---|---|---|
| <mandatory requirement 1> | <where it is satisfied> | PASS/FAIL/UNKNOWN |
| <mandatory requirement 2> | <where it is satisfied> | PASS/FAIL/UNKNOWN |

Gate result:
- PASS only if every mandatory requirement is PASS.
- BLOCKED if any mandatory requirement is FAIL or UNKNOWN.
```

The agent must never treat partial compliance as acceptable.

---

## Usage Examples

See `examples/` for:

- `telegram-chat-example.md` — Full Telegram chat from trigger to manual package
- `daily-trigger.md` — Common trigger patterns for everyday use
- `sample-quest.md` — A safe demo quest for recording
- `sample-hermes-run.md` — Expected Hermes output
- `final-submission.md` — Manual submission package example

---

## What This Is NOT

- NOT an automatic task claimer or submitter
- NOT a posting, voting, commenting, or upvoting bot
- NOT a spam or bulk-commenting tool
- NOT affiliated with or endorsed by AgentHansa
- NOT a replacement for the AgentHansa platform or documentation
- NOT a fully autonomous AI agent

---

## Safety Notes

- Always fetch full quest details before executing from a notification
- Never prepare a manual package unless all mandatory requirements are PASS
- Never invent proof URLs or claim unverified facts
- Treat live AgentHansa docs and quest pages as authoritative
- The user performs all external mutations manually

---

## 中文使用说明

本 skill 面向 **Telegram + Hermes/OpenClaw** 日常工作流设计：

**使用流程：**

1. 在 Telegram 向 Hermes 发送任务通知或 `做任务`
2. Hermes 调用 skill，用中文返回任务分析
3. 你执行人工步骤（如 LinkedIn 发帖、ProductFeatHub upvote、提交任务）
4. Hermes 出交付物草稿并做 100% 任务符合性检查
5. 所有 mandatory requirements 都 PASS 后，Hermes 生成手动提交包
6. 你复制内容到 AgentHansa，由你本人手动提交

**核心四件事：**
- 任务理解 — 拆解要求，判断风险
- 执行计划 — 明确步骤，分离人工/AI 操作
- 质量检查 — 100% mandatory requirements PASS
- 提交材料整理 — `submission_content` + `proof_url` + evidence + 手动步骤

**不做什么：**
- 不自动提交
- 不自动 resubmit
- 不自动发帖/评论/upvote
- 不伪造 proof
- 不批量刷任务
- 不替用户做任何外部平台写操作

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
| `examples/final-submission.md` | Manual submission package example |
| `examples/daily-trigger.md` | Common trigger patterns |
| `examples/telegram-chat-example.md` | Full Telegram chat example |
| `demo/demo-script.md` | One-minute demo script |
| `docs/research-report.md` | Research and gap analysis |
| `docs/implementation-plan.md` | Implementation plan |
| `docs/screen-recording-plan.md` | 2-3 min demo video plan |
| `docs/submission-summary.md` | Hackathon submission text |
