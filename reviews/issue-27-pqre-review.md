# PQRE Risk Review — Issue #27

**Issue:** [AI Risk Review] Test Reliability Issue — JNC2 Platform CPU Power Increase 650 W → 900 W
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/27
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-14
**Requestor:** ShouChin Lee (DCAI Q&R — Boards & Systems)

---

<!-- ═══════════════════════════════════════════════════════════════════════
     ENGLISH REVIEW
     ═══════════════════════════════════════════════════════════════════════ -->

## 1. Executive Summary

This PQRE review was triggered by Issue #27, submitted by ShouChin Lee
(DCAI Q&R — Boards & Systems). The request concerns platform **JNC2** where the
**CPU TDP has been increased from 650 W to 900 W** — a 38% power increase.
The requestor explicitly notes the absence of a derating report, SI report,
thermal validation report, and qualification evidence; no supporting data of any
kind was submitted with the intake.

The power increase places at least five engineering domains in scope: Thermal,
Derating, SI/PI/PDN, Mechanical, and Reliability. With no supporting data for
any domain and Data Confidence rated at 1 (No data) across all in-scope areas,
the preliminary risk posture is **High Risk — HOLD**. Engineering review cannot
be signed off until the blocking evidence items listed in Section 7 are submitted
and evaluated.

---

## 2. Request Classification

- **Platform:** JNC2
- **Change Description:** CPU TDP increase from 650 W to 900 W (+250 W / +38%)
- **Domains in scope:** Thermal, Derating, SI/PI/PDN, Mechanical, Reliability
- **Domains out of scope:** Manufacturing (no process change noted), Supplier
  Readiness (no component substitution noted), Regulatory (no material or
  certification change noted)
- **Risk Tier:** **High Risk** (Data Confidence ≤ 2 across all in-scope domains;
  aggregate of ≥ 2 Medium Risk domains escalates to High Risk per
  `KnowledgeBase/risk_scoring_criteria.md`)
- **Action Required:** Yes

---

## 3. Action Required

**Yes.**

A 38% CPU TDP increase on platform JNC2 (650 W → 900 W) without any supporting
engineering evidence constitutes a high-risk change. All five in-scope PQRE
domains lack required evidence. This review is **HOLD** until all five blocking
evidence items (Actions 1–5 in Section 8) are submitted and evaluated.

---

## 4. Known Issues

1. **No Thermal Validation Report** — The requestor explicitly confirms that no
   thermal validation has been performed at 900 W. Cooling solution adequacy at
   the new TDP is unknown. Overtemperature operation risks component damage,
   system instability, and reduced MTBF.

2. **No Derating Report** — All power delivery components, voltage regulators,
   and board-level power components must be re-derated at 900 W. Without a
   derating analysis, the risk of operating outside derated margins is
   unquantified.

3. **No SI/PDN Report** — Higher current draw at 900 W requires PDN
   re-analysis. VR load line, decoupling capacitor adequacy, and PDN target
   impedance compliance at 900 W are unverified.

4. **No Qualification Evidence** — No component, board, or system-level
   qualification data at 900 W has been provided. Historical qualification at
   650 W does not cover the new operating point.

5. **KnowledgeBase Precedent Confirms High Risk** — `KnowledgeBase/
   risk_scoring_criteria.md` includes an explicit example RPN calculation for the
   identical scenario (650 W → 900 W CPU TDP increase), classifying the Thermal
   domain alone at RPN = 48 with Data Confidence = 1. This precedent confirms the
   High Risk classification for the current request.

---

## 5. Unknown Risks

- **Thermal Margin Erosion** — Without thermal characterisation at 900 W, the
  actual junction temperature (Tj) relative to Tj_max is unknown. Margin erosion
  may exist but remain undetected until a field failure occurs.

- **PDN Transient Instability** — CPU power transients at 900 W may cause
  voltage droop events exceeding the VR load line specification. Risk of system
  instability under load-step conditions is uncharacterised without transient PDN
  simulation.

- **Solder Joint Fatigue** — Increased thermal cycling amplitude at 900 W
  accelerates solder joint fatigue. The delta-T and the associated reduction in
  thermal cycle life have not been estimated.

- **Socket / Connector Retention** — Higher thermal load may increase board
  warpage, affecting CPU socket and adjacent connector retention forces. No
  board-flex analysis at 900 W has been submitted.

- **MTBF Reduction** — Component failure rates (FIT) increase with operating
  temperature. The magnitude of MTBF reduction at 900 W versus the 650 W
  qualification baseline is unknown.

- **Adjacent Component Thermal Stress** — Nearby components (VRs, memory,
  PCIe devices) may experience increased thermal stress from the higher-TDP CPU.
  Cross-component thermal impact has not been assessed.

- **Power Sequencing Compliance** — If VR configuration was tuned for 650 W,
  power sequencing margins at 900 W may be affected. This risk is uncharacterised.

---

## 6. Impact Assessment

### Qualitative Impact Summary

| Category | Impact Description | Severity |
|----------|--------------------|----------|
| Thermal | System overtemperature failure possible if cooling solution is not re-validated at 900 W | Critical |
| Derating | Components may exceed derated voltage/current/power limits; risk of early failure or damage | Significant |
| SI / PI / PDN | PDN droop events may cause CPU errors, system hangs, or data corruption | Significant |
| Mechanical | Increased board flex and solder joint fatigue under higher thermal cycling amplitude | Moderate |
| Reliability | Reduced component MTBF due to elevated operating temperature; qualification gap at 900 W | Significant |

### RPN Risk Assessment

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|--------|-------------|----------------|---------------|-----|-----------------|-----------|
| Thermal | 4 | 4 | 3 | **48** | 1 — No thermal validation data ¹ | **High Risk** |
| Derating | 4 | 4 | 3 | **48** | 1 — No derating report ¹ | **High Risk** |
| SI / PI / PDN | 4 | 3 | 3 | **36** | 1 — No SI/PDN report ¹ | **Medium + Low Conf → High Risk** |
| Mechanical | 3 | 3 | 3 | **27** | 1 — No mechanical analysis ¹ | **Medium + Low Conf → High Risk** |
| Reliability | 4 | 3 | 3 | **36** | 1 — No qualification evidence ¹ | **Medium + Low Conf → High Risk** |

**Scoring Rationale:**

- **Thermal S=4**: Thermal failure possible if cooling solution is not validated
  at 900 W — consistent with KnowledgeBase reference example for identical scenario.
- **Thermal O=4**: 38% TDP increase with no new thermal data — identical to
  KnowledgeBase reference (S×O×D = 4×4×3 = RPN 48).
- **Thermal D=3**: Thermal monitoring exists but may not detect margin erosion
  before damage occurs.

- **Derating S=4**: Exceeding component derating limits can cause immediate or
  accelerated failure.
- **Derating O=4**: No derating analysis performed; risk of limit exceedance is
  uncharacterised.
- **Derating D=3**: Functional testing may not catch derating exceedances.

- **SI/PDN S=4**: PDN insufficiency at 900 W can cause CPU errors and data
  corruption.
- **SI/PDN O=3**: PDN may or may not be adequate; new analysis required to
  determine margin.
- **SI/PDN D=3**: PDN simulation and measurement can detect issues but have not
  been performed.

- **Mechanical S=3**: Board flex and solder joint issues are moderate severity
  with recoverable impact.
- **Mechanical O=3**: Significant thermal load change creates moderate probability
  of mechanical issues.
- **Mechanical D=3**: Simulation is possible but has not been performed.

- **Reliability S=4**: Reduced MTBF and uncharacterised qualification gap
  represent significant long-term risk.
- **Reliability O=3**: Elevated temperatures increase FIT rate; magnitude depends
  on Tj delta.
- **Reliability D=3**: Long-term reliability impacts may not manifest in
  short-term testing.

¹ **Low Confidence flag triggered** — Data Confidence = 1 (No data) for all five
  in-scope domains. Escalation to PQRE Manager required per
  `KnowledgeBase/risk_scoring_criteria.md`.

**Aggregate Risk:** Two or more domains at Medium Risk → Aggregate treated as
**High Risk** per escalation rules. Labels `high-risk` and `low-confidence` must
be applied to this issue.

---

## 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | Thermal validation report at 900 W (simulation or test data; Tj_max vs. measured/simulated Tj; cooling solution specification) | Thermal | **Yes** |
| 2 | Derating report: all component derating calculations re-validated at 900 W operating conditions | Derating | **Yes** |
| 3 | SI/PDN report: PDN target impedance analysis, VR load line specification, PDN simulation or measurement at 900 W | SI/PI/PDN | **Yes** |
| 4 | Component qualification evidence at 900 W: FIT/MTBF data, HTOL results, or supplier qualification certificate | Reliability | **Yes** |
| 5 | Board flex / mechanical stress simulation at new thermal load (900 W) | Mechanical | **Yes** |
| 6 | System-level thermal qualification test results or plan with projected completion timeline | Thermal | **Yes** |
| 7 | VR and PDN component datasheet maximum ratings vs. applied conditions at 900 W | Derating | No |
| 8 | Cooling solution thermal resistance data (heatsink, TIM, airflow specification) | Thermal | No |
| 9 | Solder joint reliability assessment under increased thermal cycling amplitude | Mechanical | No |
| 10 | System inlet temperature specification and altitude derating (if applicable) | Thermal | No |

---

## 8. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Submit thermal validation report: thermal simulation or test data at 900 W, Tj analysis, cooling solution specification | [TBD — assign before closure] | [TBD] | **Yes** |
| 2 | Submit derating report: re-validate all component derating margins at 900 W operating conditions | [TBD — assign before closure] | [TBD] | **Yes** |
| 3 | Submit SI/PDN report: PDN target impedance analysis, VR load line specification, simulation or measurement at 900 W | [TBD — assign before closure] | [TBD] | **Yes** |
| 4 | Submit component qualification evidence: FIT/MTBF data or supplier qualification certificate at 900 W | [TBD — assign before closure] | [TBD] | **Yes** |
| 5 | Submit mechanical analysis: board flex / stress simulation at new thermal load | [TBD — assign before closure] | [TBD] | **Yes** |
| 6 | Schedule PQRE engineering review meeting after Actions 1–5 are submitted to evaluate all evidence | [TBD — assign before closure] | [TBD] | Yes |
| 7 | Obtain PQRE Manager acknowledgement of HOLD status and confirm escalation path | [TBD] | [TBD] | No |
| 8 | Apply `high-risk` and `low-confidence` labels to this issue and notify the designated reviewers | [TBD] | [TBD] | No |

---

## 9. PQRE Recommendation

> **HOLD**
>
> Platform JNC2 CPU TDP increase from 650 W to 900 W cannot be approved in its
> current state. All five in-scope engineering domains (Thermal, Derating,
> SI/PI/PDN, Mechanical, Reliability) lack supporting evidence, and Data
> Confidence is rated at 1 (No data) for every domain. This triggers both the
> **High Risk** threshold (aggregate of multiple Medium Risk domains) and the
> **Low Confidence** flag across all in-scope domains, requiring escalation to
> the PQRE Manager.
>
> Per `KnowledgeBase/pqre_signoff_criteria.md`, the following five blocking
> evidence items must be submitted and reviewed before this issue can be
> advanced:
>
> - **Action 1** — Thermal validation report at 900 W.
> - **Action 2** — Derating report at 900 W.
> - **Action 3** — SI/PDN report at 900 W.
> - **Action 4** — Component qualification evidence at 900 W.
> - **Action 5** — Mechanical analysis (board flex/stress) at 900 W thermal load.
>
> Do not proceed with JNC2 deployment at 900 W until all blocking actions are
> resolved and a PQRE review upgrade (HOLD → CONDITIONAL APPROVE or APPROVE) is
> issued by the PQRE Manager.

---
---

<!-- ═══════════════════════════════════════════════════════════════════════
     繁體中文版 TRADITIONAL CHINESE REVIEW
     ═══════════════════════════════════════════════════════════════════════ -->

## 1. 執行摘要

本次 PQRE 審查由 Issue #27 觸發，請求人為 ShouChin Lee（DCAI Q&R — 主板與系統部門）。
本次請求涉及平台 **JNC2**，其 **CPU TDP 由 650 W 提升至 900 W**，增幅達 38%。
請求人明確指出缺乏降額報告、SI 報告、熱驗證報告及資格認證文件，亦未附上任何支持數據。

此次功耗提升影響至少五個工程領域：熱設計、降額、SI/PI/PDN、機械及可靠性。
由於所有在審領域均無支持數據（資料可信度評定為 1，即無數據），初步風險評估為
**高風險 — 暫停（HOLD）**。在第 7 節所列封鎖性文件齊備並完成評審前，
工程審查不得簽核。

---

## 2. 請求分類

- **平台：** JNC2
- **變更描述：** CPU TDP 由 650 W 提升至 900 W（+250 W / +38%）
- **在審領域：** 熱設計、降額、SI/PI/PDN、機械、可靠性
- **排除領域：** 製造（無製程變更）、供應商就緒（無元件替換）、
  法規（無材料或認證變更）
- **風險等級：** **高風險**（所有在審領域資料可信度 ≤ 2；依
  `KnowledgeBase/risk_scoring_criteria.md`，兩個以上中風險領域合計升級為高風險）
- **需要行動：** 是

---

## 3. 需要採取行動

**是。**

JNC2 平台 CPU TDP 增加 38%（650 W → 900 W）且無任何工程支持文件，屬於高風險變更。
五個在審 PQRE 領域均缺乏所需證據。本審查維持**暫停（HOLD）**狀態，
直至第 8 節行動項目 1–5 完成提交並通過評審。

---

## 4. 已知問題

1. **無熱驗證報告** — 請求人明確確認尚未對 900 W 進行熱驗證。
   新 TDP 下散熱方案的充足性未知。超溫運行可能導致元件損壞、系統不穩定及 MTBF 降低。

2. **無降額報告** — 所有電源傳遞元件、穩壓器及板級電源元件須在 900 W 下重新降額驗算。
   缺乏降額分析，元件超出降額限值的風險無法量化。

3. **無 SI/PDN 報告** — 900 W 下電流需求增加，需重新分析 PDN。
   VR 負載線、去耦電容充足性及 PDN 目標阻抗合規性尚未驗證。

4. **無資格認證文件** — 未提供 900 W 工作條件下的元件、電路板或系統層級認證數據。
   650 W 的歷史認證數據不適用於新工作點。

5. **知識庫先例確認高風險** — `KnowledgeBase/risk_scoring_criteria.md`
   收錄了完全相同情境（650 W → 900 W CPU TDP 提升）的 RPN 計算範例，
   單一熱設計領域即評定為 RPN = 48、資料可信度 = 1。
   此先例確認本請求之高風險分類。

---

## 5. 未知風險

- **熱裕量侵蝕** — 未在 900 W 下進行熱表徵，實際接面溫度（Tj）與 Tj_max 的差距未知。
  裕量侵蝕可能存在但在現場故障發生前無法被察覺。

- **PDN 暫態不穩定** — 900 W 下 CPU 功耗暫態可能導致電壓跌落超出 VR 負載線規格。
  未進行暫態 PDN 模擬，負載階躍條件下系統不穩定的風險尚未表徵。

- **焊點疲勞** — 900 W 下熱循環振幅增大，加速焊點疲勞。
  溫差（delta-T）及熱循環壽命縮短幅度尚未估算。

- **插槽 / 接連器保持力** — 較高熱負載可能增大電路板翹曲，
  影響 CPU 插槽及相鄰連接器保持力。尚未提交 900 W 下的板彎分析。

- **MTBF 降低** — 元件失效率（FIT）隨工作溫度升高而增加。
  900 W 相較 650 W 認證基準的 MTBF 降幅未知。

- **相鄰元件熱應力** — 鄰近元件（VR、記憶體、PCIe 裝置）可能因高 TDP CPU 而承受更高熱應力，
  跨元件熱影響尚未評估。

- **電源序列合規性** — 若 VR 配置依 650 W 調整，900 W 下電源序列裕量可能受影響，
  此風險尚未表徵。

---

## 6. 影響評估

### 定性影響摘要

| 類別 | 影響描述 | 嚴重度 |
|------|----------|--------|
| 熱設計 | 若未在 900 W 下重新驗證散熱方案，可能發生系統超溫故障 | 嚴重 |
| 降額 | 元件可能超出降額電壓/電流/功率限值，導致提前故障或損壞 | 顯著 |
| SI / PI / PDN | PDN 電壓跌落事件可能導致 CPU 錯誤、系統宕機或資料損毀 | 顯著 |
| 機械 | 熱循環振幅增大導致板彎及焊點疲勞加速 | 中等 |
| 可靠性 | 工作溫度升高導致元件 MTBF 降低；900 W 下存在認證缺口 | 顯著 |

### RPN 風險評估表

| 領域 | 嚴重度 (S) | 發生率 (O) | 探測度 (D) | RPN | 資料可信度 | 風險等級 |
|------|-----------|-----------|-----------|-----|-----------|--------|
| 熱設計 | 4 | 4 | 3 | **48** | 1 — 無熱驗證數據 ¹ | **高風險** |
| 降額 | 4 | 4 | 3 | **48** | 1 — 無降額報告 ¹ | **高風險** |
| SI / PI / PDN | 4 | 3 | 3 | **36** | 1 — 無 SI/PDN 報告 ¹ | **中風險 + 低可信度 → 高風險** |
| 機械 | 3 | 3 | 3 | **27** | 1 — 無機械分析 ¹ | **中風險 + 低可信度 → 高風險** |
| 可靠性 | 4 | 3 | 3 | **36** | 1 — 無資格認證文件 ¹ | **中風險 + 低可信度 → 高風險** |

**評分依據：**

- **熱設計 S=4**：若未在 900 W 下驗證散熱方案，可能發生熱故障；與知識庫相同情境範例一致。
- **熱設計 O=4**：TDP 增加 38% 且無新熱數據；與知識庫參考範例相同（4×4×3 = RPN 48）。
- **熱設計 D=3**：熱監控機制存在，但可能無法在損壞發生前檢測到裕量侵蝕。
- **降額 S=4**：超出降額限值可能導致即時或加速失效。
- **降額 O=4**：無降額分析，超限風險尚未表徵。
- **SI/PDN S=4**：900 W 下 PDN 不足可能導致 CPU 錯誤及資料損毀。
- **SI/PDN O=3**：PDN 是否充足尚不確定，需新分析確認裕量。
- **機械 S=3**：板彎及焊點問題屬中等嚴重度，有補救可能。
- **可靠性 S=4**：MTBF 降低及認證缺口構成顯著長期風險。

¹ **觸發低可信度旗標** — 所有五個在審領域資料可信度均為 1（無數據）。
  依 `KnowledgeBase/risk_scoring_criteria.md` 須升級至 PQRE 主管審查。

**合計風險：** 兩個以上領域達到中風險 → 依升級規則合計升級為**高風險**。
本 Issue 須套用 `high-risk` 及 `low-confidence` 標籤。

---

## 7. 資訊缺口

| # | 缺失項目 | 領域 | 是否封鎖 |
|---|---------|------|---------|
| 1 | 900 W 熱驗證報告（模擬或測試數據；Tj_max vs. 模擬/測量 Tj；散熱方案規格） | 熱設計 | **是** |
| 2 | 降額報告：所有元件在 900 W 工作條件下重新進行降額計算 | 降額 | **是** |
| 3 | SI/PDN 報告：PDN 目標阻抗分析、VR 負載線規格、900 W 下 PDN 模擬或量測 | SI/PI/PDN | **是** |
| 4 | 900 W 工作條件下元件資格認證文件：FIT/MTBF 數據、HTOL 結果或供應商認證書 | 可靠性 | **是** |
| 5 | 新熱負載（900 W）下板彎 / 機械應力模擬 | 機械 | **是** |
| 6 | 系統層級熱資格認證測試結果，或附預計完成時程之計劃書 | 熱設計 | **是** |
| 7 | VR 及 PDN 元件規格書最大額定值 vs. 900 W 工作條件下實際施加條件 | 降額 | 否 |
| 8 | 散熱方案熱阻數據（散熱器、TIM、風量規格） | 熱設計 | 否 |
| 9 | 熱循環振幅增大條件下焊點可靠性評估 | 機械 | 否 |
| 10 | 系統進氣溫度規格及高度降額（如適用） | 熱設計 | 否 |

---

## 8. 必要行動

| # | 行動項目 | 負責人 | 截止日期 | 是否封鎖 |
|---|---------|-------|---------|---------|
| 1 | 提交熱驗證報告：900 W 熱模擬或測試數據、Tj 分析、散熱方案規格 | [待指定 — 關閉前必須填寫] | [待定] | **是** |
| 2 | 提交降額報告：在 900 W 工作條件下重新驗算所有元件降額裕量 | [待指定 — 關閉前必須填寫] | [待定] | **是** |
| 3 | 提交 SI/PDN 報告：PDN 目標阻抗分析、VR 負載線規格、900 W 下模擬或量測 | [待指定 — 關閉前必須填寫] | [待定] | **是** |
| 4 | 提交元件資格認證文件：900 W 下 FIT/MTBF 數據或供應商認證書 | [待指定 — 關閉前必須填寫] | [待定] | **是** |
| 5 | 提交機械分析：新熱負載下板彎 / 應力模擬 | [待指定 — 關閉前必須填寫] | [待定] | **是** |
| 6 | 行動 1–5 完成提交後，安排 PQRE 工程審查會議評估所有文件 | [待指定 — 關閉前必須填寫] | [待定] | 是 |
| 7 | 取得 PQRE 主管對暫停狀態之確認，並確認升級路徑 | [待定] | [待定] | 否 |
| 8 | 為本 Issue 套用 `high-risk` 及 `low-confidence` 標籤，並通知指定審查人員 | [待定] | [待定] | 否 |

---

## 9. PQRE 建議

> **暫停（HOLD）**
>
> JNC2 平台 CPU TDP 由 650 W 提升至 900 W，目前狀態下無法核准。
> 所有五個在審工程領域（熱設計、降額、SI/PI/PDN、機械、可靠性）均缺乏支持文件，
> 且所有領域資料可信度均為 1（無數據）。此情況同時觸發**高風險**門檻
> （兩個以上中風險領域合計升級）及所有在審領域的**低可信度**旗標，
> 須升級至 PQRE 主管審查。
>
> 依 `KnowledgeBase/pqre_signoff_criteria.md`，下列五項封鎖性文件必須提交並通過評審，
> 本 Issue 方可進展：
>
> - **行動 1** — 900 W 熱驗證報告。
> - **行動 2** — 900 W 降額報告。
> - **行動 3** — 900 W SI/PDN 報告。
> - **行動 4** — 900 W 元件資格認證文件。
> - **行動 5** — 900 W 熱負載下機械分析（板彎/應力）。
>
> 在所有封鎖性行動完成並由 PQRE 主管發出審查升級通知
> （HOLD → CONDITIONAL APPROVE 或 APPROVE）之前，
> 請勿對 JNC2 平台在 900 W 下進行部署。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication based on this review.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-14.
This review is an advisory output. Final engineering decisions require human sign-off.*
