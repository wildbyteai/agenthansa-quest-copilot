# Daily Trigger Examples

Use these examples when running AgentHansa Quest Copilot in daily alliance work.

The operator-facing workflow should be Chinese by default. Final deliverables should follow the language required by the quest.

Hard rules:

1. The agent never submits, resubmits, posts, comments, votes, uploads final proof, clicks final buttons, or calls submission APIs.
2. The agent only prepares a manual submission package when every mandatory requirement is PASS.
3. Any mandatory `FAIL` or `UNKNOWN` means `BLOCKED`.

## Short Quest Notification

```text
按任务流程执行

New Quest: $100.00
Seed 3+ insight-first replies on AI-search hot threads — curated list or your own finds
Deadline: 2026-05-01
```

Expected behavior:

1. Start with a Chinese status header.
2. Extract the title, reward, deadline, sponsor/product, URL/id if present.
3. Attempt to fetch the full AgentHansa quest detail.
4. Verify the fetched detail matches the notification.
5. Extract must-have requirements, risks, and unknowns in Chinese.
6. Decide whether to proceed.
7. Continue drafting only when full requirements and proof requirements are clear enough.
8. Run the 100% compliance check.
9. Stop at a manual submission package if every mandatory requirement is PASS.
10. Output `BLOCKED` if any mandatory requirement is `FAIL` or `UNKNOWN`.

## Full Quest Detail

```text
做任务

[paste full AgentHansa quest detail here]
```

Expected behavior:

- Skip external lookup if the pasted detail is complete.
- Extract requirements in Chinese.
- Create an execution plan.
- Produce the deliverable in the quest-required language.
- Run the 100% compliance check.
- Prepare proof plan.
- Prepare a manual submission package only if every mandatory requirement is PASS.
- Never execute submission.

## Submission Preparation

```text
准备提交

Quest:
[paste quest detail]

Final content:
[paste final content]

Proof URL:
[paste proof URL]
```

Expected behavior:

- Review the final content against every mandatory requirement.
- Check proof readiness and accessibility.
- Identify remaining risks.
- Output a manual submission package only if every mandatory requirement is PASS.
- If the user says `确认提交`, refresh manual submission guidance only.
- Never perform any mutating action.

## Human Handoff

```text
我已经手动发布了，下面是 proof：

reply_url: ...
screenshot: ...
```

Expected behavior:

- Verify the provided evidence matches the quest requirements.
- Update proof plan.
- Re-run the 100% compliance check.
- Prepare a manual submission package only if every mandatory requirement is PASS.
- Do not publish, upload, submit, or resubmit anything.

## Grade Feedback

```text
ai_grade: B
ai_summary: The proof does not show 3 insight-first replies.
```

Expected behavior:

- Diagnose the failed requirement in Chinese.
- Propose a revised proof or deliverable.
- Prepare a revised manual package only if every mandatory requirement becomes PASS.
- Explain manual resubmission steps.
- Never resubmit automatically.
