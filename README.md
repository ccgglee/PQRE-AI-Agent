# PQRE-AI-Agent

**Purpose:** Automate the PQRE engineering review workflow using AI agents
triggered by GitHub issues created from Outlook email intake.

**Author:** Shou-Chin Lee (DCAI Q&R — Boards & Systems)

---

## Repository Structure

```
.github/
  agents/
    pqre-risk-review-agent.agent.md   ← Agent definition
  prompts/
    pqre-risk-review.prompt.md        ← Structured review prompt
    ai-risk-review.prompt.md
    design-review.prompt.md
    email-analysis.prompt.md
  copilot-instructions.md             ← Global Copilot guardrails
KnowledgeBase/
  pqre_signoff_criteria.md            ← Minimum evidence requirements per domain
  risk_scoring_criteria.md            ← RPN calculation rules and tier definitions
reviews/
  issue-5-pqre-review.md             ← PQRE review output for Issue #5 (PR #2 agent intro)
README.md
```

---

## Agents

### pqre-risk-review-agent

Reads a GitHub issue created by the Power Automate email intake flow and
generates a full PQRE risk review covering eight engineering domains:
Thermal, Derating, SI/PI/PDN, Mechanical, Reliability, Manufacturing,
Supplier Readiness, and Regulatory.

**How to invoke:**

```
@pqre-risk-review-agent review issue #<N>
```

Or apply the label `ai-risk-review` to any issue to trigger automatic analysis.

If an intake issue includes a `Required PQRE Analysis` section, the agent uses
that exact section list in the same order. If the issue also requests `Output
in English and Traditional Chinese`, the agent returns the requested section
set in both languages.

If the intake explicitly asks for questionnaire or form-completion guidance,
the agent appends draft questionnaire responses. Questionnaire answers remain
draft-only, use `[TBD]` placeholders for missing identity fields, and reject
items that are not related to platform hardware or validation hardware.

---

## Example — Issue #1

**Issue:** [AI Risk Review] PQRE GitHub Test (COR CPU)
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/1

**Input (from issue body):**
> COR CPU TDP increase from 650 W to 900 W. Need derating assessment.

**Command:**
```
@pqre-risk-review-agent review issue #1
```

---

### Example Output

---

#### 1. Executive Summary

A request was received from Shou-Chin Lee (DCAI Q&R — Boards & Systems) to
evaluate a COR CPU TDP increase from 650 W to 900 W (a 38% increase) and
provide a derating assessment. The issue was created via the Power Automate
email intake flow on 2026-07-09. No thermal simulation data, cooling solution
specifications, or derating calculations were provided with the request.
Given the magnitude of the TDP delta and the absence of supporting evidence,
the preliminary risk posture is **High Risk — HOLD**.

---

#### 2. Request Classification

- **Domains in scope:** Thermal, Derating, SI/PI/PDN, Reliability
- **Domains out of scope:** Mechanical, Manufacturing, Supplier Readiness, Regulatory *(pending further information)*
- **Risk Tier:** High Risk
- **Action Required:** Yes

---

#### 3. Available Evidence

- `[CONFIRMED]` Current TDP: 650 W
- `[CONFIRMED]` Proposed TDP: 900 W
- `[CONFIRMED]` Component family: COR CPU

---

#### 4. Missing Evidence

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | Tj_max and θja from component datasheet | Thermal | Yes |
| 2 | Thermal simulation or test data at 900 W | Thermal | Yes |
| 3 | Cooling solution specification (heatsink, airflow, TIM) | Thermal | Yes |
| 4 | System inlet temperature specification | Thermal | No |
| 5 | Component max voltage/current/power ratings | Derating | Yes |
| 6 | Derating calculation workbook at 900 W | Derating | Yes |
| 7 | VR load line specification and PDN simulation at 900 W | SI/PI/PDN | Yes |
| 8 | FIT rate / MTBF at new operating conditions | Reliability | Yes |

---

#### 5. Known Issues

No documented field escapes or open engineering change notices were found in
the current issue log for this component at 900 W. Assessment cannot be
completed without the evidence listed in Section 4.

---

#### 6. Unknown Risks

- Thermal margin erosion at 900 W if existing cooling solution was sized for 650 W
- VR (Voltage Regulator) output capability and transient response at increased load
- Solder joint fatigue acceleration due to higher thermal cycling amplitude
- Reliability derating at elevated junction temperature

---

#### 7. Qualification Gaps

| Domain | Current Qualification Basis | Required for 900 W |
|--------|----------------------------|-------------------|
| Thermal | Qualified at 650 W TDP | Re-qualification at 900 W required |
| Derating | Not confirmed | Derating table at 900 W required |
| SI/PI/PDN | Not confirmed | PDN re-simulation at 900 W required |
| Reliability | Not confirmed | HTOL extrapolation at new Tj required |

---

#### 8. Risk Assessment

| Domain | S | O | D | RPN | Data Confidence | Risk Tier |
|--------|---|---|---|-----|-----------------|-----------|
| Thermal | 4 | 4 | 3 | 48 | 1 — No test data | **High** ¹ |
| Derating | 4 | 4 | 3 | 48 | 1 — No derating calc | **High** ¹ |
| SI/PI/PDN | 3 | 3 | 3 | 27 | 1 — No PDN sim | **High** ¹ |
| Reliability | 4 | 3 | 3 | 36 | 1 — No HTOL data | **High** ¹ |

¹ Data Confidence ≤ 2 triggers **Low Confidence** flag → domain treated as High Risk
regardless of RPN per `KnowledgeBase/risk_scoring_criteria.md`.

---

#### 9. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Provide COR CPU 900 W datasheet (Tj_max, θja, ratings) | [TBD] | [TBD] | Yes |
| 2 | Submit thermal simulation or test report at 900 W | [TBD] | [TBD] | Yes |
| 3 | Provide cooling solution specification for 900 W scenario | [TBD] | [TBD] | Yes |
| 4 | Submit derating calculation workbook at 900 W | [TBD] | [TBD] | Yes |
| 5 | Provide PDN simulation results at 900 W load | [TBD] | [TBD] | Yes |
| 6 | Submit HTOL data or Reliability prediction at new Tj | [TBD] | [TBD] | Yes |

---

#### 10. PQRE Recommendation

> **HOLD**
>
> All four in-scope domains lack the minimum evidence required for sign-off
> per `KnowledgeBase/pqre_signoff_criteria.md`. Six blocking action items
> (Actions 1–6) must be resolved before this review can proceed. Do not
> implement the TDP change until a CONDITIONAL APPROVE or APPROVE is issued.

---

#### 11. Bilingual Summary (繁體中文摘要)

**執行摘要**

本次審查收到 Shou-Chin Lee（DCAI Q&R — 主板與系統）透過 Power Automate
電子郵件流程建立的 GitHub Issue，請求評估 COR CPU 熱設計功耗（TDP）從
650 W 增加至 900 W（增幅 38%）的降額可行性。本次請求未提供任何熱模擬數據、
散熱解決方案規格或降額計算資料。鑑於 TDP 變化幅度及缺乏佐證文件，
初步風險評估為**高風險 — 暫緩（HOLD）**。

**PQRE 建議**

> **暫緩（HOLD）**
>
> 四個範圍內的工程領域（熱設計、降額、SI/PI/PDN、可靠性）均缺乏
> `KnowledgeBase/pqre_signoff_criteria.md` 所要求的最低佐證文件。
> 必須完成六項封鎖性行動項目（行動 1–6）後，本審查方可繼續進行。
> 在發出「有條件核准」或「核准」通知之前，請勿實施此 TDP 變更。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication based on this review.

---

## Functions

- **AI Risk Review** — `pqre-risk-review-agent` (see above)
- **Design Review Analysis** — `.github/prompts/design-review.prompt.md`
- **Email Analysis** — `.github/prompts/email-analysis.prompt.md`

## Guardrails

- Do not approve if required evidence is missing.
- Use draft-never-send for any email response.
- Human review is required before any external communication.
- Decision review is required when RPN ≥ 51.
- Low confidence is defined as Data Confidence ≤ 2.
- Do not invent evidence.
- Clearly separate confirmed facts from assumptions.
- GitHub issues are the first queryable decision log / memory store.
