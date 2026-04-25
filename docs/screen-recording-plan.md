# Screen Recording Plan

**1分钟 hackathon 演示视频**（活动规则：最长1分钟，2026年4月25日 20:00 PST 前提交）

**总时长：约60秒**
**旁白语言：英文**（你说，让AI读）
**屏幕语言：中文（Telegram对话）+ 英文（交付物）**

---

## 镜头 1：开场 (0:00 – 0:10)

**屏幕上做什么：**
打开 GitHub 仓库，`agenthansa-quest-copilot` 的 README 页面

**英文口播：**
> "I built agenthansa-quest-copilot — a Hermes skill that helps me complete AgentHansa alliance tasks with discipline, not automation."

---

## 镜头 2：展示 Skill (0:10 – 0:20)

**屏幕上做什么：**
打开 `SKILL.md`，展示以下内容：
- 触发词区域（`做任务`、`New Quest`、`按任务流程执行`）
- 状态 Header 格式
- 确认口令 `确认提交`

**英文口播：**
> "It extracts requirements in Chinese, drafts deliverables in the quest language, runs a compliance self-check, and stops here — waiting for my explicit '确认提交' before anything goes out."

---

## 镜头 3：Telegram — 任务触发与分析 (0:20 – 0:35)

**屏幕上做什么：**
在 Telegram 对话中粘贴任务通知

**用户输入：**
```
按任务流程执行

🆕 New Quest: $50.00
Find and vote on 5 ProductFeatHub feature requests...
```

Hermes 响应：
- 状态切换：`FETCHING_QUEST_DETAIL` → `ANALYZING_REQUIREMENTS`
- 输出：`任务摘要`、`要求拆解`（必须做/最好做/风险点）、`执行判断`

**英文口播：**
> "I paste a task notification. Hermes fetches the details, analyzes requirements, and creates a plan — all in Chinese."

---

## 镜头 4：交付物草稿 + 自检 (0:35 – 0:50)

**屏幕上做什么：**
Telegram 对话继续滚动，展示：
- 英文 LinkedIn post 草稿
- `自检`：4项全部 PASS
- `Proof 计划`

**英文口播：**
> "The deliverable is drafted in English — because the quest requires it. A self-check runs. Then the confirmation gate."

---

## 镜头 5：确认提交 + 执行 (0:50 – 1:00)

**屏幕上做什么：**
用户在 Telegram 输入：`确认提交`

Hermes 响应：
- 状态：`SUBMITTING`
- 执行操作
- 返回 `proof_url`
- 状态：`SUBMITTED`

**英文口播：**
> "Only after I type '确认提交' does Hermes execute. Every submission is traceable, every proof is real."

---

## 录制注意事项

- 推荐工具：OBS 或 Loom，1080p 或以上
- Telegram 文字要足够大，确保在视频里能看清
- 全程控制在60秒以内
- 旁白：单独录音后合成，或用自动降噪
- 导出格式：MP4（H.264, AAC）

## 录制后

1. 上传到 YouTube/Vimeo（先私密审看，再公开提交）
2. 把视频链接填入 `docs/submission-summary.md`
3. 在截止时间前（2026年4月25日 20:00 PST）提交
