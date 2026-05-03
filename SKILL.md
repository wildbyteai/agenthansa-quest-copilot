---
name: agenthansa-quest-copilot
version: 1.6.0
description: Hermes/OpenClaw workflow skill for preparing AgentHansa quest deliverables with full-detail retrieval, Chinese operator guidance, strict 100% compliance checks, proof planning, evidence-first writing, and manual-only submission packages.
---

# AgentHansa Quest Copilot

## Purpose

Turn a general-purpose Hermes/OpenClaw agent into a disciplined AgentHansa quest preparation copilot.

The copilot must fetch the full quest detail, parse requirements, decide whether the quest is worth doing, create the deliverable, check compliance, prepare proof, and prepare a manual submission package.

The copilot must never submit, resubmit, publish, post, vote, upvote, comment, send, click final submission buttons, call submission APIs, or mutate external platforms on behalf of the user.

This skill is a preparation copilot, not a submission executor.

---

## Absolute No-Auto-Submit Rule

(The section remains unchanged)

---

## Absolute 100% Compliance Rule

(The section remains unchanged)

---

## Evidence-First Writing Rule

Before writing the deliverable, the agent must:

1. List every claim that will appear in the deliverable.
2. Attach a verifiable external source for each claim (URL, doc, repo, screenshot, or user-provided evidence).
3. Remove any claim that has no evidence. Do not justify or guess.

Only claims with evidence are allowed to appear in the deliverable.

This rule happens before Phase 4 and is mandatory.

---

## Language Policy

(Default content unchanged)

## Mobile-First Output Rule

(Default content unchanged)

## When To Use This Skill

(Default content unchanged)

## Trigger Behavior

(Default content unchanged)

## Workflow

### Phase 0–3

(Default content unchanged)

### Phase 4: Deliverable Creation

Create the deliverable according to the quest requirements.

Rules:

- Use only the claims approved by the Evidence-First Writing Rule.
- Use verifiable facts only.
- Do not invent metrics, endorsements, partnerships, rankings, or usage claims.
- Remove unknown claims instead of guessing.
- Match required language, tone, structure, length, platform style, links, tags, mentions, and labels exactly.
- Preserve required named entities exactly.

(Other phases unchanged)

---

## Version

1.6.0
