# Changelog

## 1.5.0

- Repositioned the skill as a preparation copilot, not a submission executor.
- Added an absolute no-auto-submit rule that overrides all workflow instructions, examples, trigger phrases, user shorthand, tool availability, demo convenience, and model assumptions.
- Changed `确认提交`, `提交`, `approved, submit`, and resubmission phrases to mean: generate or refresh the final manual submission package only.
- Removed the automatic submit workflow from the core skill behavior.
- Forbid `SUBMITTING` and `SUBMITTED` states.
- Added `READY_FOR_MANUAL_SUBMISSION` and `MANUAL_SUBMISSION_GUIDE` states.
- Added an absolute 100% compliance rule: no manual submission package unless every mandatory requirement is PASS.
- Added a strict requirement/evidence/status compliance table.
- Changed any `FAIL` or `UNKNOWN` mandatory requirement into a `BLOCKED` state.
- Updated README to document manual-only submission and 100% mandatory compliance.
- Updated Telegram example so `确认提交` refreshes manual submission guidance instead of submitting.

## 1.4.0

- Added explicit bilingual output rule: deliverable in quest-required language + Chinese explanation in same response
- Added `DELIVERABLE_REVIEW` state between deliverable creation and human handoff for clearer review flow
- Added post-submission proof documentation reminder (save URL, screenshot, submission ID, timestamp)
- Added `examples/telegram-chat-example.md` with full Telegram chat from trigger to submission
- Added `docs/screen-recording-plan.md` with 2-3 min shot-by-shot demo plan
- Added `docs/submission-summary.md` with English hackathon submission text
- Added `docs/implementation-plan.md` and `docs/research-report.md`
- Rewrote README.md English-first with Chinese quickstart section and clearer Telegram/Hermes usage flow
- Clarified "What this is NOT" section in README

## 1.3.0

- Added Chinese-first operator workflow while preserving quest-required language for final deliverables.
- Added mobile-friendly status headers for every major response: state, quest, blocker, next action.
- Added compact output rules to reduce long free-form chat responses.
- Added explicit human handoff section for actions the user must complete manually.
- Strengthened final submission gate with a compact package and exact confirmation phrase `确认提交`.
- Clarified that vague replies such as `ok`, `继续`, or `看起来可以` are not submission approval.
- Updated README, sample run, daily trigger examples, and demo script to reflect the bilingual workflow.

## 1.2.3

- Renamed the skill metadata and headings to `agenthansa-quest-copilot` for consistency with the repository name.
- Updated README positioning, everyday usage guidance, and demo flow to emphasize full quest-detail retrieval before execution.
- Updated all examples and demo scripts to use the new repository name and URL.
- Added `examples/daily-trigger.md` with daily AgentHansa trigger patterns for quest notifications, full quest details, submission preparation, and grade feedback.

## 1.2.2

- Added Phase 0: full quest detail retrieval before execution.
- Changed short quest notifications into retrieval triggers instead of incomplete execution inputs.
- Added retrieval methods for quest URL, AgentHansa CLI/API/session tools, browser/session access, cached quest lists, and title-based lookup.
- Added match verification rules using title, reward, deadline, sponsor/product, and quest id/slug.
- Added explicit fetch failure output so the agent reports what it tried and asks only for the minimum missing input.

## 1.2.1

- Added natural trigger phrases for everyday use, including `New Quest`, `🆕 New Quest`, `做任务`, `按任务流程执行`, `准备提交`, and resubmission/grade feedback phrases.
- Added default behavior by trigger type: quest notification only, full task execution, submission preparation, and grade handling.
- Clarified that a quest notification should start intake and feasibility analysis first, not immediate drafting or submission.

## 1.2.0

- Reframed the skill as a Hermes/OpenClaw AgentHansa quest execution workflow.
- Added explicit trigger conditions for AgentHansa quests, bounties, proof tasks, and resubmissions.
- Added required output sections for reproducible demo runs.
- Expanded the workflow into clear phases: intake, extraction, feasibility, execution plan, drafting, self-check, proof, final package, confirmation, submission, and grade handling.
- Added strict PASS/FAIL compliance self-check format.
- Added demo mode for hackathon recordings and simulated quests.
- Refreshed README with positioning, demo flow, file list, and safety notes.
- Added sample quest, sample Hermes run, final submission example, and one-minute demo script.

## 1.1.5

- Reworked grade handling to support any non-A grade (B/C/D/F/Spam/unknown).
- Replaced automatic fix/retry behavior with diagnose → summarize → propose → stop.
- Prevented infinite resubmission loops.
- Enforced explicit user approval before any resubmit.

## 1.1.4

- Rewrote negative "do not" rules into positive action-oriented instructions.
- Simplified self-check wording to focus on required actions rather than prohibitions.
- Improved clarity for agent execution behavior.

## 1.1.3

- Clarified that A/B/C/D/Spam are post-submission ai_grade results.
- Explicitly forbids assigning A/B/C grades during self-check.
- Reinforced pass/fail only logic before submission.

## 1.1.2

- Restored critical execution details for real-world usage.
- Added task-type drafting strategies (competitive map, blog, email, localization).
- Reintroduced proof platform priority and trust considerations.
- Added content truncation prevention rule.
- Expanded B/C grade classification and resubmit decision logic.
- Improved quest scouting guidance.

## 1.1.1

- Fixed self-check wording to make it a mandatory pass/fail gate.
- Added two explicit pass standards:
  - 100% quest compliance.
  - 100% agent writing compliance.
- Clarified that partial compliance is failure.
- Blocked proof preparation, user confirmation, submission, and resubmission until both standards are green.

## 1.1.0

- Merged practical experience from local experiments into a single, coherent workflow.
- Added a compliance checklist covering proof platforms, screenshot requirements, structure, language, word count, sponsorship labels and named entities.
- Included competition assessment to decide whether to attempt a quest based on existing submissions and reward structure.
- Expanded self-check section to include goal coverage, source verification, framework conformance and rubric coverage.
- Detailed proof preparation steps for Google Docs and GitHub Gists, including network and authentication checks, and highlighted platforms that should be avoided.
- Emphasised user confirmation before initial submission and resubmits, with scripts for safe API calls via `terminal`.
- Added guidance on interpreting grades and deciding when to verify, resubmit or abandon a quest based on grader feedback.
- Provided optional quest scouting tips for prioritising tasks and handling API keys.
