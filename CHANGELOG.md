# Changelog

## 1.6.0

- Introduced Evidence-First Writing Rule before deliverable creation
- Constrained Phase 4 to evidence-approved claims only

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

(remaining history unchanged)
