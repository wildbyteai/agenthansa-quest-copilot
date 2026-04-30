# Telegram Chat Example

This file shows a realistic Telegram conversation between a Chinese-speaking operator and Hermes using the `agenthansa-quest-copilot` skill.

The example demonstrates two hard rules:

1. The agent never submits automatically.
2. A manual submission package is produced only after 100% mandatory requirement compliance.

---

**User → Hermes:**
```text
帮我分析一下这个任务

New Quest: $50.00
Find 5 feature requests related to AI product needs. Write a short English post explaining why they matter. Proof: published post URL plus screenshots showing the 5 completed manual actions.
Deadline: 2026-04-30
```

---

**Hermes → User:**
```markdown
状态：FETCHING_QUEST_DETAIL
任务：Find 5 AI product feature requests
阻塞：none
下一步：拉取完整任务详情并验证

## 任务详情拉取
- 状态：SUCCESS
- 来源：用户提供的完整任务描述
- 匹配校验：✓ 标题 ✓ 奖励 ✓ 截止日期
```

---

**Hermes → User:**
```markdown
状态：ANALYZING_REQUIREMENTS
任务：Find 5 AI product feature requests
阻塞：none
下一步：拆解任务要求并判断是否值得做

## 任务摘要
- 奖励：$50.00
- 截止：2026-04-30
- 目标：找 5 个 AI 产品需求相关 feature request，并写一条英文帖文说明原因
- Proof：已发布帖文 URL + 5 个手动操作截图

## 要求拆解
必须做：
- 找到 5 个与 AI 产品需求相关的 feature request
- 完成任务要求的 5 个手动动作
- 写一条英文帖文说明原因
- 帖文包含 5 个 request 的引用或链接
- 提供已发布帖文 URL
- 提供 5 个手动动作截图

最好做：
- 语气 practical，不要过度营销
- 说明每个 request 为什么对 AI 产品有价值

风险点：
- 截图必须能证明手动动作已完成
- 帖文必须自然，不能像 spam
- 所有链接和事实必须可验证

未知/缺失：
- 5 个 request 链接尚未提供
- 已发布帖文 URL 尚未提供
- 5 个截图尚未提供

## 执行判断
结论：有风险但可做
原因：任务清晰，但 proof 依赖用户本人完成外部平台动作并提供证据。
```

---

**Hermes → User:**
```markdown
状态：PLANNING
任务：Find 5 AI product feature requests
阻塞：等待用户提供手动动作证据
下一步：你完成外部平台动作后，把链接和截图发给我

## 执行计划
1. 你手动找到 5 个符合要求的 request
2. 你完成任务要求的 5 个手动动作
3. 你截图保存证据
4. 我起草英文帖文
5. 你发布帖文
6. 你提供已发布帖文 URL 和截图
7. 我做 100% 任务符合性检查
8. 若全部 PASS，我整理手动提交包

## 需要你操作
- 动作：完成外部平台手动动作、截图、发布帖文
- 原因：这些操作涉及你的账号和外部平台写操作，只能由你本人完成
- 完成后发给我：5 个 request 链接、5 张截图、已发布帖文 URL
```

---

**User → Hermes:**
```text
[用户手动完成外部动作，并发送 5 个 request 链接、5 张截图、已发布帖文 URL]
```

---

**Hermes → User:**
```markdown
状态：DELIVERABLE_REVIEW
任务：Find 5 AI product feature requests
阻塞：none
下一步：请审核交付物草稿和 100% 检查

## 交付物草稿（任务要求：英文）

I reviewed five feature requests that matter for AI product builders:

1. Request A — improves long-context workflows.
2. Request B — makes structured outputs easier to validate.
3. Request C — supports switching between model providers.
4. Request D — helps teams version and reuse prompts.
5. Request E — gives builders clearer usage and cost visibility.

These are practical infrastructure needs that reduce friction for teams building with AI.

## 100% 任务符合性检查

| Requirement | Evidence | Status |
|---|---|---|
| 找到 5 个 AI 产品需求相关 request | 用户提供了 5 个 request 链接 | PASS |
| 完成 5 个手动动作 | 用户提供了 5 张截图 | PASS |
| 英文帖文说明原因 | 草稿为英文并解释价值 | PASS |
| 帖文包含 5 个 request 引用 | 草稿逐条引用 5 个 request | PASS |
| 提供已发布帖文 URL | 用户提供了已发布 URL | PASS |
| 提供截图 proof | 用户提供了截图 | PASS |
| 外部事实可验证 | 链接和截图可验证 | PASS |

Gate result: PASS
Decision: READY_FOR_MANUAL_SUBMISSION

> 以上为英文交付物，请审核内容是否正确。agent 不会发布、操作外部平台或提交任务。
```

---

**Hermes → User:**
```markdown
状态：READY_FOR_MANUAL_SUBMISSION
任务：Find 5 AI product feature requests
阻塞：需要用户本人手动提交
下一步：请复制下方 submission_content 和 proof_url 到 AgentHansa 页面，由你本人手动提交

## 手动提交包

submission_content:
I reviewed five feature requests that matter for AI product builders:

1. Request A — improves long-context workflows.
2. Request B — makes structured outputs easier to validate.
3. Request C — supports switching between model providers.
4. Request D — helps teams version and reuse prompts.
5. Request E — gives builders clearer usage and cost visibility.

These are practical infrastructure needs that reduce friction for teams building with AI.

proof_url:
<已发布帖文 URL>

evidence:
- 5 个 request 链接
- 5 张手动动作截图
- 已发布帖文 URL

checks:
- 任务要求：PASS（100% mandatory requirements satisfied）
- 内容要求：PASS（English post, 5 request references, practical tone）
- Proof：PASS（published URL + screenshots available）
- 外部事实：PASS（links/screenshots provided）

remaining_risks:
- none

## 手动提交步骤
1. 打开 AgentHansa 对应 quest 页面
2. 粘贴 submission_content
3. 填入 proof_url
4. 附上或引用 5 张截图
5. 由你本人点击提交

注意：agent 不会自动提交。
```

---

**User → Hermes:**
```text
确认提交
```

---

**Hermes → User:**
```markdown
状态：MANUAL_SUBMISSION_GUIDE
任务：Find 5 AI product feature requests
阻塞：需要用户本人手动提交
下一步：请复制提交包到 AgentHansa 页面，由你本人点击提交

我不会自动提交。`确认提交` 只表示刷新手动提交指引。

## 手动提交步骤
1. 打开 AgentHansa 对应 quest 页面
2. 粘贴上面的 submission_content
3. 填入 proof_url
4. 附上或引用 5 张截图
5. 最后由你本人点击提交
```

---

## Notes on This Example

- The skill never auto-submits, even after `确认提交`
- The status header is always first and mobile-readable
- Human actions are explicitly separated from agent work
- A manual submission package is only produced after every mandatory requirement is PASS
- `SUBMITTING` and `SUBMITTED` are intentionally absent
