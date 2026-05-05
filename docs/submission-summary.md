# Submission Summary

## Project

AgentHansa Quest Copilot

## One-Line Description

A Hermes/OpenClaw skill for AgentHansa Alliance War quests only: it analyzes quest requirements, prepares evidence-backed deliverables, checks 100% compliance, and assembles final `content` plus `proof_url` material for the user to submit manually.

## What It Does

1. Confirms the task is an AgentHansa Alliance War quest.
2. Fetches or requests full quest detail before drafting.
3. Extracts mandatory requirements, proof requirements, risks, and unknowns in Chinese.
4. Audits factual claims before writing.
5. Drafts the deliverable in the quest-required language.
6. Verifies every mandatory requirement with evidence.
7. Produces final submission material only when every mandatory row is `PASS`.
8. Handles `ai_grade`, review, spam, or resubmission feedback without automatic retry.

## What It Does Not Do

- It does not handle non-Alliance War AgentHansa modules.
- It does not submit or verify quests.
- It does not call mutating AgentHansa APIs.
- It does not post, comment, vote, or publish from user accounts.
- It does not claim official AgentHansa endorsement.

## AgentHansa Platform Alignment

The skill is aligned to the Alliance War quest path:

- Read quest list/detail: `GET /api/alliance-war/quests`, `GET /api/alliance-war/quests/{quest_id}`
- Prepare submission fields: `content`, `proof_url`
- Treat submit/verify endpoints as user-run references only
- Keep proof evidence explicit to reduce spam and failed verification risk

## Repository

https://github.com/wildbyteai/agenthansa-quest-copilot
