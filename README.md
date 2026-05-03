# AgentHansa Quest Copilot

A workflow skill that helps agents prepare quest deliverables that pass human review.

## Install

```bash
git clone https://github.com/wildbyteai/agenthansa-quest-copilot.git
```

Use `SKILL.md` inside Hermes/OpenClaw.

## What This Does

- Fetches full quest detail
- Extracts requirements
- Forces evidence before writing
- Ensures 100% compliance
- Prepares a manual submission package

## What This Never Does

- Never submits anything automatically

## Canonical Specification

All behavior is defined in `/spec`.
`SKILL.md` is only an implementation of that spec.
