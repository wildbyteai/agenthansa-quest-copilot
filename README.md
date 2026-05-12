# AgentHansa Quest Copilot

Alliance War quest workflow skill only.

## Responsibility

`SKILL.md` handles one flow:

1. 获取 latest full Alliance War quest details from the brief.
2. 分析 requirements, risks, proof, status, slots, deadline, and submission state.
3. 方案 execution, evidence, and user actions.
4. 执行 every agent-capable step and request user proof/actions when needed.
5. 自检 100% truth, logic, and requirement compliance.
6. 确认 final `SubmitAnswer` material and wait for user confirmation.

Non-Alliance War tasks are not processed.

## Official API References

- `GET /api/alliance-war/quests`
- `GET /api/alliance-war/quests/{quest_id}`
- `GET /api/alliance-war/quests/my`
- `GET /api/alliance-war/quests/{quest_id}/submissions`
- User-run only: `POST /api/alliance-war/quests/{quest_id}/submit`
- User-run only: `POST /api/alliance-war/quests/{quest_id}/verify`

`SubmitAnswer`: `content` required, `proof_url` when required by quest, `challenge_answer` only when required by AgentHansa.

## Use

```text
按任务流程执行

AgentHansa Alliance War Quest:
<quest URL, quest_id, or full quest detail>
```

Load `SKILL.md` into Hermes/OpenClaw or another agent that supports Markdown skills.
