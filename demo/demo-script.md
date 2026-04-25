# One-Minute Demo Script

Use this script for a short hackathon-style screen recording.

## 0-10s: Show The Project

Open the GitHub repository.

Say:

> This is `agenthansa-quest-copilot`, a Hermes/OpenClaw skill that turns a general-purpose agent into a disciplined AgentHansa quest execution copilot.

## 10-20s: Show The Skill

Open `SKILL.md` and briefly show:

- natural triggers such as `New Quest`, `做任务`, and `按任务流程执行`
- Chinese operator workflow by default
- Phase 0: full quest detail retrieval
- mobile-friendly status header
- compliance self-check
- explicit user confirmation gate

Say:

> The skill keeps the operator workflow clear in Chinese, while generating the final deliverable in the language required by the quest.

## 20-35s: Give Hermes The Quest

Paste the sample quest from `examples/sample-quest.md` into Hermes.

Suggested prompt:

```text
Use agenthansa-quest-copilot demo mode.
Complete this AgentHansa-style quest and stop at the user confirmation gate:

[paste sample quest]
```

Show Hermes producing:

- 状态 header
- 任务详情拉取
- 要求拆解
- 执行判断

## 35-50s: Show The Output

Scroll to:

- English deliverable draft
- 中文自检
- Proof 计划
- 最终提交包

Say:

> The operator sees Chinese status, risks, and checks. The final content stays in English because the quest requires English.

## 50-60s: Close With The Value

Show `examples/final-submission.md` or the final package.

Say:

> This is a lightweight AgentOps workflow for AgentHansa builders. It reduces sloppy submissions, keeps proof handling explicit, and prevents blind resubmission loops.

## Optional Final Pitch

> Every agent economy needs agents that help other agents execute tasks reliably. This skill is a small step toward that: a quest execution workflow for Hermes and OpenClaw.
