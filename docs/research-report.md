# Research Report

## 1. Executive Summary

The repository already has a solid v1.3.0 AgentHansa quest copilot skill for Hermes/OpenClaw with Chinese operator workflow, compliance self-check, and explicit human confirmation gates. The main gaps for hackathon + daily use are: (1) README lacks Telegram/Hermes-specific usage visuals and bilingual structure, (2) demo/screen-recording materials are thin, (3) the skill could better surface bilingual deliverable outputs, (4) no post-submission proof documentation guidance.

This report recommends lightweight improvements to README, SKILL.md, and docs — no new architecture.

## 2. Hackathon Requirements

**What the event asks of contestants** (from Google Doc):
- Build an agent/agentic system that uses AgentHansa as an LLM evaluation platform
- Submit a working agent that completes at least one AgentHansa alliance task
- Provide a video demo (English preferred)
- Repository must demonstrate the agent is real, repeatable, and not a one-shot demo

**What to submit:**
- Video demo (2-3 minutes, English narration preferred)
- Repository with working code/prompts
- Clear README explaining what, why, and how

**Language:** English for public-facing materials (repo docs, video narration); Chinese for internal operator workflow. The user confirmed this in the brief.

## 3. AgentHansa Platform Notes

Key mechanism learned from agenthansa.com/llms.txt:

- **Alliance tasks**: Three alliances compete on business quests; merchants publish and select winners
- **Claim → Execute → Submit flow**: Browse → Claim → Execute locally → Submit with proof_url → Verify → Settle
- **Proof requirements**: `proof_url` is mandatory to avoid spam flags. Engagement tasks need `comment_url`, `notes`, `proof_image_urls`
- **Grading**: Engagement tasks = 1-5 stars (each star = 20% pay); Competitive = top 10 win (1st: 25%, 2nd: 10%, 3rd: 5%, 4th-10th: 1% each)
- **AgentRank tiers**: Elite (121+, 100% payout), Reliable (61-120, 80%), Active/Newcomer (0-60, 50%)
- **Spam policy**: 50%+ spam rate blocks submission rights; duplicate comments blocked; XP diminishes after 10 comments/day
- **Reward range**: $10-200+ for competitive quests; engagement tasks pay 1-5 stars × 20%

**Implication for copilot design**: The skill must emphasize proof_url generation, prevent spam-like behavior, and ensure human-controlled submission.

## 4. User Scenario: Telegram + Hermes + Chinese IM Workflow

**Daily usage:**
1. User receives AgentHansa alliance task notification (Telegram or forwarded)
2. User sends task to Hermes (Chinese: "帮我分析一下这个任务" / "按任务流程执行")
3. Hermes uses agenthansa-quest-copilot skill, responds in Chinese
4. Hermes extracts requirements, creates deliverable draft, runs self-check
5. Hermes presents final package and waits for `确认提交`
6. User confirms; Hermes executes (e.g., posts to LinkedIn, creates proof doc)
7. User verifies submission and proof

**Key design points:**
- Telegram = mobile-first, short messages, Chinese by default
- Hermes = intermediary that invokes the skill
- Human-in-the-loop at every submission decision
- Final deliverables in quest-required language; workflow in Chinese

## 5. Current Repository Assessment

| Component | Status | Notes |
|-----------|--------|-------|
| README.md | Good foundation | Needs: Telegram usage flow, bilingual structure, screenshots, safer "what this is not" |
| SKILL.md | Strong core | Well-structured 10-phase workflow; needs better bilingual output surfacing and post-submission proof doc guidance |
| examples/ | Adequate | sample-quest + sample-hermes-run are good; needs Telegram chat example showing trigger → output |
| demo/demo-script.md | Thin | Only 1 minute; needs 2-3 min structure with shot-by-shot plan |
| docs/ | Missing | No research-report, implementation-plan, or submission-summary yet |

**Already done well:**
- Mobile-first status headers (`状态：... 阻塞：... 下一步：...`)
- Explicit confirmation gate with `确认口令：确认提交`
- Anti-spam / compliance self-check with PASS/FAIL
- Grade handling without blind retry loops
- No invented metrics or fake proof

## 6. Screenshot-Based Findings

### Screenshot 1 (0d5b79ed...): Task Analysis + Draft Creation

**What it shows:**
- User: "45.ai产品需求的alliance task，帮我分析一下这个任务"
- Hermes correctly extracted task: "Find and vote on 5 ProductFeatHub feature requests related to AI product needs"
- LinkedIn post draft created (English, ~100 words, practical tone)
- Self-check all PASS
- Proof plan: LinkedIn post + ProductFeatHub upvote evidence
- Human handoff asking for publication confirmation

**Strengths:**
- Status header always visible
- Requirement breakdown clear (must-do, risk points, unknowns)
- Feasibility judgment explicit
- Deliverable draft shown before asking for approval
- Clear separation of agent work vs human action

**Gaps observed:**
- The deliverable draft could be more visually separated as a "deliverable review" state before the confirmation gate
- No explicit mention of the bilingual output (Chinese workflow → English deliverable) in the output itself
- Post-draft review state (`READY_FOR_REVIEW`) is present but the transition from draft review to submission package could be tighter

### Screenshot 2 (e30c3e94...): Submission Execution

**What it shows:**
- User said `确认提交`
- Hermes executed LinkedIn post with status updates
- Success message with proof_url
- Proof document showing: LinkedIn post URL, 5x upvote confirmation, requirement checklist
- `remaining_risks: none`

**Strengths:**
- Clean execution flow
- Proof document well-structured
- Post-submission summary complete

**Gaps observed:**
- No explicit post-submission proof documentation guidance in the skill (should tell user to save/record the proof)

## 7. Gaps to Fix

1. **README**: English-first structure with Chinese usage section, Telegram-specific flow, screenshot placeholders
2. **SKILL.md**: Better bilingual output surfacing, clearer "deliverable review" state, post-submission proof doc guidance
3. **Examples**: Add Telegram chat example file showing realistic trigger → analysis → draft → confirm → submit flow
4. **Demo materials**: Expand to 2-3 min script with screen recording plan, add submission summary
5. **No automation**: Confirm the skill does NOT auto-submit (it correctly doesn't — this is already right)

## 8. Recommended Lightweight Direction

Keep the existing 10-phase workflow. Make targeted improvements:

- **README**: Reorganize English-first, add Chinese quickstart, add Telegram flow diagram (text-based), add "What this is NOT"
- **SKILL.md**: Add a "Deliverable Review" explicit state, add post-submission proof documentation reminder, clarify bilingual output in headers
- **New files**: `examples/telegram-chat-example.md`, `docs/screen-recording-plan.md`, `docs/submission-summary.md`, `docs/implementation-plan.md`, this research report
- **Do NOT add**: New backend, database, automation features, auto-submit logic

## 9. Open Questions Requiring Human Confirmation

1. Should the demo video be hosted on YouTube/Vimeo, or just submitted as a file?
2. Is the 2-3 minute video duration a hard requirement or guideline?
3. Should I SSH to the Hermes server to check the live skill configuration, or is reviewing the local repo sufficient?
4. The screenshots contain the 45.ai task — should I reference this specific task in the demo script, or use the generic sample quest?
