# PQRE Risk Review — Issue #38

**Issue:** [AI Risk Review] Basin City DR0.3 Review Placeholder
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/38
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-15
**Requestor:** ccgglee (DCAI Q&R — Boards & Systems)

---

## 1. Executive Summary

This PQRE review was triggered by Issue #38, which captures a DR0.3 (Design Review stage 0.3)
milestone email for the **Basin City** platform. The intake content indicates that three
engineering open items are currently outstanding and will be resolved in subsequent work weeks:

- **HCC (High Core Count) power numbers** — expected WW29.5
- **DDR CAC (Command/Address/Clock) pinout optimizations** — in progress
- **64 GT/s Signal Integrity (SI) validation data** — expected WW30

The next formal design review milestone, **DR0.6**, is on track for **WW40**.

The intake body was submitted as a placeholder and contains **no quantitative engineering
data, no test results, and no formal design specifications**. As a result, it is not possible
to perform a full PQRE sign-off assessment at this stage. The preliminary risk posture is
**HOLD — INSUFFICIENT DATA**, pending resubmission of the intake after WW30 when all three
blocking data sets are expected to be available.

Three engineering domains are directly affected: **PDN/Power Delivery**, **Signal Integrity
(SI)**, and **DFM/Board Layout** (DDR pinout). Each carries at least one open item that
blocks PQRE sign-off per `KnowledgeBase/pqre_signoff_criteria.md`.

---

## 2. Request Classification

- **Platform:** Basin City
- **Design Review Stage:** DR0.3 (early design; DR0.6 target WW40)
- **Domains in scope:**
  - PDN / Power Delivery (HCC power numbers outstanding)
  - Signal Integrity (64 GT/s SI validation pending)
  - DFM / Board Layout (DDR CAC pinout optimizations in progress)
- **Domains out of scope:** Thermal (no thermal data provided), Mechanical (no data provided),
  Reliability (no HTOL / FIT data provided), Supplier Readiness (no BOM / EOL data provided),
  Regulatory (no compliance declarations provided)
- **Risk Tier:** Medium Risk — escalated to High Risk treatment due to Low Confidence across
  all in-scope domains (Data Confidence = 1 for all three domains)
- **Action Required:** Yes

---

## 3. Action Required

**Yes.** All three in-scope domains have Data Confidence = 1 (no measurement or simulation
data provided). Per `KnowledgeBase/risk_scoring_criteria.md`, this triggers the
**Low Confidence flag** for all domains, requiring elevated review to Engineering Manager
level. Formal PQRE intake must be resubmitted after WW30 with complete engineering data.

---

## 4. Known Issues

1. **HCC power numbers not yet available** — The exact TDP, peak power transient, and
   per-rail current targets for the High Core Count (HCC) configuration of Basin City are
   pending (expected WW29.5). PDN design, decoupling strategy, and Voltage Regulator (VR)
   load line specification cannot be validated until these numbers are confirmed.

2. **DDR CAC pinout under active optimization** — The Command/Address/Clock pinout for DDR
   memory is subject to ongoing design changes. Any pinout alteration affects board routing
   rules (trace length, topology, termination), signal integrity budgets, and manufacturing
   DFM checks. The scope and direction of these changes are not yet documented in this intake.

3. **64 GT/s SI validation data not yet available** — Simulation or measurement data for the
   high-speed 64 GT/s interface (PCIe Gen 5 or equivalent) has not been submitted. SI
   validation is a blocking evidence requirement for the SI domain per
   `KnowledgeBase/pqre_signoff_criteria.md`. Data is expected WW30.

4. **Intake body is a placeholder** — The original issue body lists open items without
   engineering specifications, simulation results, or test data. The PQRE review framework
   cannot issue an APPROVE or CONDITIONAL APPROVE recommendation on a placeholder intake.

---

## 5. Unknown Risks

- **HCC power overshoot / undershoot** — Until HCC power numbers are confirmed, it is
  unknown whether the existing PDN design (VR topology, decoupling capacitor placement,
  trace impedance) can support the final power target. A significant increase may require
  PDN re-spin.

- **DDR pinout impact on other interfaces** — Changes to DDR CAC pinout may affect
  adjacent signal routing and crosstalk budgets for other high-speed interfaces on the
  board. The cascading impact on SI and EMI is unknown until the final pinout is frozen.

- **64 GT/s SI margin risk** — At 64 GT/s, SI margins are extremely sensitive to via
  stubs, connector launches, and package parasitics. Pre-layout simulations may not
  capture all real-board effects; post-layout validation results could reveal margin
  issues requiring board or package re-design.

- **Schedule compression risk** — With HCC power data expected WW29.5 and SI data
  expected WW30, and DR0.6 targeted for WW40, the available window for design iteration
  and PQRE sign-off is narrow (~10 weeks). Any slip in data delivery could compress
  or jeopardise the DR0.6 milestone.

- **Out-of-scope domain risks** — Thermal, Mechanical, and Reliability impacts of the
  final HCC power configuration are unknown. A significant TDP increase may trigger
  separate reviews in those domains.

---

## 6. Impact Assessment

| Category | Impact | Severity |
|----------|--------|----------|
| PDN — HCC power | VR selection, decoupling network, and board power planes may require redesign if power targets exceed current PDN specification | Significant |
| SI — 64 GT/s interface | Channel loss, crosstalk, and timing margin violations could require board layer stack-up or routing changes | Significant |
| DFM — DDR CAC pinout | Pinout changes drive routing rule updates, potentially affecting board area, via usage, and PCB layer count | Moderate |
| Schedule — DR0.6 WW40 | Approximately 10-week window for data delivery, analysis, iteration, and PQRE sign-off is tight; any slip in data availability directly threatens DR0.6 readiness | Significant |
| Thermal / Mechanical | Cannot be assessed until HCC power numbers are confirmed; potential impact unknown | Unknown |
| Reliability | Cannot be assessed without operating power and temperature data; potential impact unknown | Unknown |

---

## 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | HCC TDP (W) — current design target and worst-case maximum | PDN | **Yes** |
| 2 | Per-rail current targets for HCC configuration (VCCIN, VCCSA, VDDQ, etc.) | PDN | **Yes** |
| 3 | VR load line specification for HCC power mode | PDN | **Yes** |
| 4 | PDN simulation or measurement at HCC power levels | PDN | **Yes** |
| 5 | DDR CAC pinout delta — current vs. proposed; full net list or schematic markup | DFM / SI | **Yes** |
| 6 | DDR routing rule update driven by pinout change (trace length, topology, termination) | DFM | **Yes** |
| 7 | 64 GT/s SI channel simulation results (insertion loss, return loss, crosstalk) | SI | **Yes** |
| 8 | 64 GT/s SI validation test data (eye diagram, bathtub BER) | SI | **Yes** |
| 9 | Thermal impact assessment for final HCC TDP (junction temperature, cooling re-validation) | Thermal | No |
| 10 | Reliability impact (FIT rate, HTOL data) at final HCC operating conditions | Reliability | No |
| 11 | Updated board layer stack-up if DDR or SI changes require additional routing layers | DFM | No |

---

## 8. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Submit HCC power numbers (TDP, per-rail current targets, VR load line) when confirmed | [TBD — assign before closure] | WW29.5 | **Yes** |
| 2 | Submit DDR CAC pinout delta document (current vs. proposed net list or schematic markup) with routing rule impact assessment | [TBD — assign before closure] | [TBD — before DR0.6] | **Yes** |
| 3 | Submit 64 GT/s SI simulation and validation data (channel analysis, eye diagram, BER) | [TBD — assign before closure] | WW30 | **Yes** |
| 4 | Resubmit formal PQRE intake (Issue #38 or new issue) after WW30 with all three blocking data sets attached for full PQRE sign-off assessment | [TBD — assign before closure] | WW30 + | **Yes** |
| 5 | Initiate Thermal domain review once HCC TDP is confirmed; determine whether cooling solution re-validation is required before DR0.6 | [TBD] | WW29.5 + | No |
| 6 | Confirm Reliability domain impact of final HCC TDP; assess whether operating conditions change requires FIT rate re-calculation or new HTOL data | [TBD] | [TBD] | No |
| 7 | Confirm no Regulatory impact from DDR pinout change (RoHS / REACH compliance not affected by board layout changes) | [TBD] | [TBD] | No |

---

## 9. PQRE Recommendation

> **HOLD — INSUFFICIENT DATA**
>
> The Basin City DR0.3 intake is a placeholder with no quantitative engineering data,
> simulation results, or test measurements. All three in-scope domains (PDN, SI, DFM)
> have Data Confidence = 1, triggering the **Low Confidence flag** for each domain.
> Formal PQRE sign-off assessment cannot be completed at this stage.
>
> **Required steps before PQRE sign-off can be issued:**
>
> - **Action 1** — HCC power numbers required (TDP, per-rail currents, VR load line) — expected WW29.5.
> - **Action 2** — DDR CAC pinout delta documentation required — needed before DR0.6.
> - **Action 3** — 64 GT/s SI validation data required (simulation + test) — expected WW30.
> - **Action 4** — Formal PQRE intake resubmission required after WW30 for full assessment.
>
> The recommendation will be revisited and upgraded to **CONDITIONAL APPROVE** or
> **APPROVE** once Actions 1–4 are completed and submitted for review. The
> **DR0.6 (WW40) milestone** provides approximately 10 weeks of schedule margin from
> WW30 for data submission, PQRE assessment, and any required design iteration.
>
> Do not use this placeholder review as a PQRE sign-off decision basis.

---

## 10. Bilingual Summary (繁體中文摘要)

### 執行摘要

本次 PQRE 審查由 Issue #38 觸發，該 Issue 為 **Basin City** 平台 DR0.3（設計審查第 0.3 階段）
里程碑的電子郵件通知。本次審查涵蓋以下三項工程待完成項目：

- **HCC（高核心數）功耗數據** — 預計 WW29.5 提供
- **DDR CAC（命令 / 位址 / 時脈）接腳排列優化** — 設計進行中
- **64 GT/s 訊號完整性（SI）驗證數據** — 預計 WW30 提供

下一個正式設計審查里程碑 **DR0.6** 目標為 **WW40**。

本次受理資料為佔位符格式，**不包含量化工程規格、模擬結果或測試數據**。
因此，目前階段無法進行完整的 PQRE 簽核評估。

三個工程領域受到直接影響：**PDN / 電源完整性**、**訊號完整性（SI）** 及
**DFM / 電路板佈線**（DDR 接腳配置）。每個領域均存在至少一項封鎖性待確認項目，
阻礙 PQRE 依照 `KnowledgeBase/pqre_signoff_criteria.md` 規定完成簽核。

---

### 已知問題

1. **HCC 功耗數據尚未確定** — DDR PDN 設計、去耦策略及 VR 負載線規格無法在確認前驗證。
2. **DDR CAC 接腳排列尚在優化中** — 任何接腳改變均影響電路板佈線規則與 SI 預算。
3. **64 GT/s SI 驗證數據尚未提供** — 為 SI 領域封鎖性簽核依據，預計 WW30 提供。
4. **受理資料為佔位符** — 無量化工程規格；PQRE 無法依此出具核准建議。

---

### PQRE 建議

> **暫緩（HOLD）— 資料不足**
>
> Basin City DR0.3 受理資料為佔位符，三個相關工程領域（PDN、SI、DFM）之
> 資料可信度均為 1，觸發**低可信度標記**。目前階段無法完成正式 PQRE 簽核評估。
>
> **PQRE 簽核評估所需步驟：**
>
> - **行動 1** — 需提供 HCC 功耗數據（TDP、各電源軌電流目標、VR 負載線） — 預計 WW29.5。
> - **行動 2** — 需提供 DDR CAC 接腳排列差異文件 — DR0.6 前需完成。
> - **行動 3** — 需提供 64 GT/s SI 驗證數據（模擬 + 測試） — 預計 WW30。
> - **行動 4** — WW30 後需重新提交正式 PQRE 受理單以進行完整評估。
>
> 建議將於行動 1–4 完成並提交後重新審查，並視情況升級為**有條件核准**或**核准**。
>
> 請勿將本佔位符審查作為 PQRE 簽核決策依據。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication based on this review.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-15.
This review is an advisory output. Final engineering decisions require human sign-off.*
