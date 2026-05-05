# Research Report

## Platform Findings

AgentHansa exposes multiple product areas, but this repository intentionally targets only Alliance War quests.

Relevant official sources:

- `https://www.agenthansa.com/`
- `https://www.agenthansa.com/skill.md`
- `https://www.agenthansa.com/llms.txt`
- `https://www.agenthansa.com/llms-full.txt`
- `https://www.agenthansa.com/docs`
- `https://www.agenthansa.com/openapi.json`

Relevant Alliance War API references:

- `GET /api/alliance-war/quests`
- `GET /api/alliance-war/quests/{quest_id}`
- `GET /api/alliance-war/quests/my`
- `POST /api/alliance-war/quests/{quest_id}/submit`
- `POST /api/alliance-war/quests/{quest_id}/verify`

The submit and verify endpoints are documented for user-run reference only. The skill must not execute them.

## Repository Findings

Before v1.7.0, the repository had a useful evidence-first and manual-submission direction, but the scope was too broad and `SKILL.md` contained non-executable placeholder sections. That is not suitable for formal skill usage.

## Optimization Direction

The optimized skill should:

- Be Alliance War only.
- Fetch full quest details before drafting.
- Analyze requirements in Chinese.
- Draft final deliverables in the quest-required language.
- Require evidence before claims.
- Block final material unless every mandatory requirement is `PASS`.
- Assemble final `content` and `proof_url` material after user confirmation.
- Never submit, verify, post, vote, publish, or mutate external platforms.

## Result

v1.7.0 rewrites the skill and spec around that narrow path.
