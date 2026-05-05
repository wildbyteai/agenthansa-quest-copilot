# Implementation Plan

## Goal

Make `agenthansa-quest-copilot` a narrow, reliable skill for AgentHansa Alliance War quests only.

## Design Decisions

- Use official AgentHansa docs and OpenAPI as the platform source of truth.
- Restrict all behavior to Alliance War quest analysis and submission-material preparation.
- Allow read-only quest lookup through official sources or configured credentials.
- Forbid the agent from submitting, verifying, posting, voting, or mutating external platforms.
- Treat `确认提交` as "assemble final material", not "execute submission".

## Core Workflow

1. Confirm the task is Alliance War.
2. Fetch or request full quest detail.
3. Extract requirements and proof needs in Chinese.
4. Decide feasibility.
5. Audit factual claims.
6. Draft deliverable.
7. Request user-owned external actions when required.
8. Run 100% compliance check.
9. Build final `content` and `proof_url` material after confirmation.
10. Diagnose grade or review feedback if needed.

## Acceptance Criteria

- `SKILL.md` has no placeholder sections.
- README and spec files say Alliance War only.
- Examples use `READY_FOR_SUBMISSION_MATERIAL`, not submit states.
- Non-Alliance War modules are explicitly out of scope.
- Final material is blocked unless all mandatory requirements are `PASS`.
- No file instructs the agent to execute submission automatically.
