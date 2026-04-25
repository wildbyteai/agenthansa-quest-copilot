# Daily Trigger Examples

Use these examples when running AgentHansa Quest Copilot in daily alliance work.

The operator-facing workflow should be Chinese by default. Final deliverables should follow the language required by the quest.

## Short Quest Notification

```text
按任务流程执行

🆕 New Quest: $100.00
Seed 3+ insight-first replies on AI-search hot threads (Topify) — curated list or your own finds
Deadline: 2026-05-01
```

Expected behavior:

1. Start with a Chinese status header.
2. Extract the title, reward, deadline, sponsor/product, URL/id if present.
3. Attempt to fetch the full AgentHansa quest detail.
4. Verify the fetched detail matches the notification.
5. Extract must-have requirements, risks, and unknowns in Chinese.
6. Decide whether to proceed.
7. Continue execution only when the full requirements and proof requirements are clear enough.
8. Stop at the user confirmation gate before submission.

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
- Run compliance self-check.
- Prepare proof and final submission package.
- Ask for explicit approval before submission.

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

- Review final package.
- Check proof readiness.
- Identify remaining risks.
- Ask for the exact confirmation phrase `确认提交` before any mutating action.

## Human Handoff

```text
我已经手动发布了，下面是 proof：

reply_url: ...
screenshot: ...
```

Expected behavior:

- Verify the provided evidence matches the quest requirements.
- Update proof plan or proof document.
- Re-run self-check.
- Prepare final submission package.

## Grade Feedback

```text
ai_grade: B
ai_summary: The proof does not show 3 insight-first replies.
```

Expected behavior:

- Diagnose the failed requirement in Chinese.
- Propose a revised proof or deliverable.
- Prepare a new final package.
- Stop before resubmission until the user approves.
