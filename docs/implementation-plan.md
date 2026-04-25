# Implementation Plan

## 1. Product Positioning

**English (for repo, hackathon, public-facing):**
> A lightweight Telegram-first Hermes skill that helps a Chinese-speaking operator understand, plan, quality-check, and prepare submissions for AgentHansa alliance tasks. Not a task-automation bot; a disciplined human-in-the-loop copilot.

**中文 (日常使用):**
> 一个面向 Telegram + Hermes 的轻量 AgentHansa 联盟任务辅助 skill，帮中文用户理解任务、规划执行、做质量检查、整理 proof 和提交说明。核心原则：人主导，AI 辅助。

## 2. Target User

- Primary: Kyle (Chinese-speaking, Telegram + Hermes daily workflow, participates in AgentHansa alliance tasks)
- Secondary: Hermes/OpenClaw builders who want a repeatable quest execution workflow

## 3. Core Workflow

```
用户发送任务通知/链接/截图
    ↓
Hermes 触发 skill（触发词：做任务 / 按任务流程执行 / New Quest 等）
    ↓
【Phase 0】拉取完整任务详情（never draft from notification alone）
    ↓
【Phase 1】拆解任务要求（中文输出）
    ↓
【Phase 2】判断可行性
    ↓
【Phase 3】制定执行计划
    ↓
【Phase 4】生成交付物草稿（按任务要求语言，如英文）
    ↓
【Phase 5】需要人工操作的部分（人工 handoff）
    ↓
【Phase 6】合规自检
    ↓
【Phase 7】Proof 准备
    ↓
【Phase 8】输出最终提交包（bilingual：中文说明 + 任务语言内容）
    ↓
【Phase 9】等待用户确认「确认提交」
    ↓
【Phase 10】执行提交（人工或 API），返回结果
    ↓
【Phase 11】（如有）Grade 处理
```

**Human-in-the-loop at:** Phase 5 (manual actions), Phase 9 (explicit submission gate)

## 4. Language Strategy

| Context | Language |
|---------|----------|
| Telegram status/analysis/risk/execution plan | 中文 |
| Quest requirement extraction | 中文 |
| Feasibility judgment | 中文 |
| Human handoff instructions | 中文 |
| Final confirmation prompts | 中文 |
| Grade diagnosis | 中文 |
| Deliverable content | 按任务要求（通常英文） |
| Proof document content | 按任务要求 |
| Submission payload | 按任务要求 |
| README / hackathon docs | 英文为主 |

## 5. Skill Behavior Design

### Status Header (always first)
```
状态：<STATE>
任务：<short quest title>
阻塞：<none or blocker>
下一步：<next human/agent action>
```

### Supported States
`FETCHING_QUEST_DETAIL` | `ANALYZING_REQUIREMENTS` | `WAITING_FOR_INFO` | `PLANNING` | `CREATING_DELIVERABLE` | `READY_FOR_REVIEW` | `WAITING_FOR_SUBMIT_APPROVAL` | `SUBMITTING` | `SUBMITTED` | `GRADE_HANDLING` | `BLOCKED`

### Trigger Phrases (Chinese + English)
- `做任务`
- `按任务流程执行`
- `New Quest` / `🆕 New Quest`
- `帮我分析一下这个任务`
- `评估这个任务`
- `准备提交`
- `确认提交`
- `resubmit` / `重新提交`

### Four Core Capabilities (must remain explicit in skill)

1. **任务理解** — Extract requirements, classify must-do / nice-to-do / risk / unknown
2. **执行计划** — Short actionable plan with human/agent separation
3. **质量检查** — Self-check with PASS/FAIL on task requirements, content, proof, external facts
4. **提交材料整理** — Final package with submission_content, proof_url, checks, risks

### Anti-Spam Rules
- Never invent metrics, endorsements, rankings, or usage claims
- Never generate fake proof URLs
- Never auto-submit without explicit `确认提交`
- Never treat `ok` / `继续` / `看起来可以` as submission approval
- Mark unknown risks explicitly
- Stop on non-A grades; do not blind retry

## 6. Quality and Anti-Spam Checklist

Before every submission package:

```
## 自检
- 任务要求：PASS/FAIL
- 内容要求：PASS/FAIL
- Proof 准备：PASS/FAIL/UNKNOWN
- 外部事实：PASS/FAIL/UNKNOWN
- 剩余风险：none / <list>
```

## 7. Minimal Repository Changes

### File list to add/edit:

| File | Action | Purpose |
|------|--------|---------|
| README.md | Rewrite | English-first, bilingual quickstart, Telegram flow, clearer positioning |
| SKILL.md | Enhance | Explicit "Deliverable Review" state, post-submission proof doc reminder, bilingual surfacing |
| examples/telegram-chat-example.md | New | Realistic Telegram chat showing full flow from trigger to submission |
| docs/implementation-plan.md | New | This file |
| docs/screen-recording-plan.md | New | Shot-by-shot 2-3 min demo plan |
| docs/submission-summary.md | New | English hackathon submission text |

### Files to keep unchanged:
- examples/sample-quest.md (already good)
- examples/sample-hermes-run.md (already good)
- examples/final-submission.md (already good)
- examples/daily-trigger.md (already good)
- demo/demo-script.md (will expand into screen-recording-plan)
- CHANGELOG.md (append new entry)
- VERSION (increment to 1.4.0)

## 8. Demo Video Plan

**Duration:** 2-3 minutes
**Language:** English narration, Chinese workflow shown in screen
**Flow:**

1. **0-20s**: Show GitHub repo, state the problem (Chinese-speaking operator needs help with AgentHansa alliance tasks)
2. **20-50s**: Show SKILL.md structure — triggers, Chinese workflow, compliance check, confirmation gate
3. **50-90s**: Show Telegram chat — paste a real task trigger, show Hermes analyzing it in Chinese
4. **90-130s**: Show deliverable draft (English) + self-check + proof plan
5. **130-170s**: Show `确认提交` → execution → success → proof document
6. **170-180s**: Close with value prop — lightweight copilot, human-in-the-loop, not automation

## 9. Acceptance Criteria

- [ ] README has English-first structure + Chinese quickstart section
- [ ] README explains Telegram + Hermes usage clearly
- [ ] README has "What this is NOT" section
- [ ] SKILL.md has explicit bilingual output surfacing
- [ ] SKILL.md has post-submission proof documentation reminder
- [ ] examples/telegram-chat-example.md exists with realistic flow
- [ ] docs/screen-recording-plan.md has 2-3 min shot-by-shot plan
- [ ] docs/submission-summary.md exists with English hackathon text
- [ ] All four core capabilities visible in skill: 任务理解, 执行计划, 质量检查, 提交材料整理
- [ ] No auto-submit logic added
- [ ] No fake proof URL generation
- [ ] No large new architecture (backend, database, etc.)
- [ ] VERSION bumped to 1.4.0
- [ ] CHANGELOG entry added
