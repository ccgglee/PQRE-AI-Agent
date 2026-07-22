# PQRE Risk Review — Issue #146

**Issue:** [AI Risk Review] MTBF for RP boards
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/146
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-22
**Requestor:** ccgglee
**Platform:** Reference Platform (RP) boards — ANC, Sabre, Dunlow, Johnson City (JNC1/JNC2), Basin City (BNC)
**Scope:** MTBF (Mean Time Between Failures) analysis and qualification readiness for RP boards

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #146, which requests an AI risk review focused on **MTBF (Mean Time Between Failures) for RP (Reference Platform) boards**. The intake body contains no supporting engineering data, design delta documents, or MTBF prediction workbooks.

RP boards in scope (per `KnowledgeBase/platform/platform_alias.yaml`) include:

| Platform | Aliases | CPU |
|---|---|---|
| ANC (Anderson City) | Pine Stream | COR AP 20CH |
| Sabre (Sabre City) | — | COR AP 20CH |
| Dunlow | — | Xeon E |
| Johnson City | JNC1, JNC2, Oak Stream AP | DMR AP |
| Basin City | BNC, COR 8CH | COR SP |

MTBF is a **blocking reliability evidence item** per `KnowledgeBase/Rules/pqre_signoff_criteria.md` (Section 5 — Reliability: *"Component FIT rate or MTBF at new operating conditions — Blocking: Yes"*). Without a submitted MTBF prediction report, component FIT rate data, or system-level reliability block diagram (RBD), a formal APPROVE or CONDITIONAL APPROVE cannot be issued for any RP board release tied to this request.

> **Current PQRE Posture: HOLD — Insufficient data; reliability evidence package required before disposition can be upgraded.**

The key risk is not that MTBF is inherently poor on RP boards, but that **no quantified evidence has been submitted** to confirm MTBF meets the customer or program requirement. This creates an evidence gap, not necessarily a design deficiency.

---

### 2. Request Classification

- **Request type:** Reliability metric review — MTBF qualification readiness inquiry
- **Platform scope:** All active RP boards (ANC, Sabre, Dunlow, JNC1/JNC2, BNC)
- **Primary domain:** Reliability
- **Secondary domains:** Thermal (operating temperature affects MTBF), Material (component FIT rates), DFT (field return data availability)
- **Out-of-scope domains:** SI, PDN, Mechanical, DFM, Regulatory *(unless a specific RP board design change is associated with this request)*
- **Current evidence level:** None provided in issue body
- **Risk Tier:** High (Low Confidence — no MTBF data submitted; Data Confidence = 1)
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.**

MTBF evidence is a **blocking sign-off item** under PQRE sign-off criteria. The following actions are required before disposition can be upgraded from HOLD:

1. Submit an MTBF prediction report for each RP board in scope (MIL-HDBK-217, Telcordia SR-332, or FIDES methodology accepted).
2. Confirm the MTBF target requirement per program specification or customer contractual requirement.
3. Confirm operating conditions (Tj_max, ambient temperature, duty cycle, altitude) used for prediction.
4. Provide component FIT rate data (supplier-sourced or standard parts database) for critical BOM items.

---

### 4. Known Issues

1. **No MTBF data submitted** — The intake body is empty. No prediction workbook, FIT rate summary, or reliability qualification report has been provided. This is the primary blocking gap.

2. **Multiple RP boards in scope without differentiation** — The request covers five distinct RP platforms (ANC, Sabre, Dunlow, JNC1/JNC2, BNC) with different CPUs and configurations. A single MTBF number cannot be assumed to apply across all platforms without platform-specific evidence.

3. **MTBF target requirement not stated** — No MTBF target (e.g., 100,000 hours, 200,000 hours) or reference standard has been cited. Without a target, pass/fail determination is impossible.

4. **Operating condition assumptions unknown** — MTBF predictions are sensitive to junction temperature, ambient temperature, and duty cycle. If these inputs differ between platforms or between development and production configurations, predictions may not be valid for field conditions.

5. **Component FIT rate source not identified** — FIT rates may be derived from MIL-HDBK-217, Telcordia SR-332, FIDES, or supplier datasheets. If the methodology is mixed or undocumented, prediction traceability is lost.

6. **Field return data availability unclear** — For platforms with prior-generation equivalents (e.g., JNC1/JNC2 DMR AP), field return or early-life failure data may exist but has not been submitted to substantiate or anchor the prediction.

---

### 5. Unknown Risks

- **Thermal exceedance impact on MTBF** — If any RP board operates at or near Tj_max under production workloads, the Arrhenius temperature acceleration factor can reduce effective MTBF by 30–50% compared to rated conditions. This risk cannot be quantified without thermal characterization data.

- **Connector and socket wear-out** — RP boards used in high-cycle lab and validation environments accumulate connector insertion cycles beyond field equivalent. Mechanical wear-out failure modes are typically not captured in electronic MTBF predictions; if lab-use MTBF is being used to make field-reliability claims, this creates an unconservative estimate.

- **BOM change impact on FIT rate** — If any component substitution (CCN/PCN) was applied during RP board production, FIT rates from the original prediction may no longer be valid. No BOM change review was included in the intake.

- **Accelerated life test (ALT) data gap** — If no HTOL (High Temperature Operating Life) or ALT data exists at the system level, the MTBF prediction relies entirely on part-count methods, which can carry ±50% uncertainty bands.

- **Cross-platform data re-use risk** — If a prior-generation RP (e.g., JNC1 DMR AP) MTBF report is being proposed as evidence for a new-generation platform (e.g., ANC COR 20CH), the design delta between platforms must be formally assessed before data re-use is accepted. CPU and chipset changes directly affect dominant FIT contributors.

---

### 6. Impact Assessment

| Category | Impact | Severity |
|---|---|---|
| Reliability — field MTBF risk | RP boards shipped without validated MTBF may not meet customer SLA requirements | Significant |
| Reliability — prediction accuracy | Part-count predictions without ALT data carry high uncertainty; field MTBF may differ significantly | Moderate |
| Program — sign-off gate | MTBF is a blocking item; missing evidence will delay PQRE sign-off and platform release | Significant |
| Thermal — MTBF sensitivity | Operating temperature deviation from prediction assumption reduces effective MTBF; risk is unquantified without thermal data | Moderate |
| Material — FIT rate validity | BOM changes or component substitutions may invalidate existing FIT rate inputs | Moderate |
| DFT — field return feedback | Without field return analysis, early-life failure rate and infant mortality risk remain uncharacterized | Moderate |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|---|---|---|
| 1 | MTBF prediction report (MIL-HDBK-217 / Telcordia SR-332 / FIDES) for each RP board in scope | Reliability | **Yes** |
| 2 | MTBF target requirement per program specification or customer contract | Reliability | **Yes** |
| 3 | Operating condition assumptions used in prediction (Tj, Ta, duty cycle, altitude) | Reliability | **Yes** |
| 4 | Component FIT rate source and methodology (supplier data, standard parts DB, or empirical) | Reliability | **Yes** |
| 5 | HTOL or ALT data at system or critical subsystem level (if available) | Reliability | No |
| 6 | Field return / early-life failure data from predecessor RP platforms (JNC1, JNC2, BNC) | Reliability | No |
| 7 | BOM change log (CCN/PCN) for any RP board since last reliability qualification | Material | No |
| 8 | Thermal characterization data (Tj_max at production workload) for each RP platform | Thermal | No |
| 9 | Connector insertion cycle count for lab/validation unit versus field unit | Mechanical | No |
| 10 | Design delta assessment if prior-generation RP MTBF data is proposed for re-use | Reliability | **Yes** (if re-use is proposed) |

---

### 8. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|---|---|---|---|
| 1 | Submit MTBF prediction report for each RP board in scope (ANC, Sabre, Dunlow, JNC1/JNC2, BNC); include methodology, operating condition assumptions, and FIT rate sources | [TBD — Reliability Engineering] | [TBD] | **Yes** |
| 2 | Confirm and document MTBF target requirement per program specification or customer contractual requirement for each RP platform | [TBD — Program/Systems Engineering] | [TBD] | **Yes** |
| 3 | Verify operating conditions used in MTBF prediction match actual production/field thermal and environmental profile; reconcile with thermal characterization data | [TBD — Thermal + Reliability Engineering] | [TBD] | **Yes** |
| 4 | Review BOM change log (CCN/PCN) since last reliability qualification; reassess FIT rates for any changed components | [TBD — Component Engineering] | [TBD] | No |
| 5 | If prior-generation RP MTBF data (JNC1/JNC2 or BNC) is proposed for re-use on a new platform, submit formal design delta assessment demonstrating equivalence or documenting delta impact on FIT | [TBD — Reliability Engineering] | [TBD] | **Yes** (if re-use is proposed) |
| 6 | Provide HTOL or ALT data at system or critical subsystem level if available; if not available, document rationale for relying on part-count method only | [TBD — Reliability Engineering] | [TBD] | No |
| 7 | Collect and review field return data from predecessor platforms (JNC1, JNC2, BNC); assess ELFR and infant mortality trend | [TBD — Quality Engineering] | [TBD] | No |

---

### 9. Risk Assessment

#### MTBF Evidence Gap Risk Scoring

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|---|---:|---:|---:|---:|---|---|
| Reliability — MTBF evidence completeness | 4 | 3 | 3 | 36 | 1 — No data submitted | **Medium → High** ¹ |
| Reliability — thermal impact on MTBF | 3 | 3 | 3 | 27 | 1 — No thermal data submitted | **Medium → High** ¹ |
| Material — BOM change FIT validity | 3 | 2 | 3 | 18 | 2 — No BOM change review | **Low → Medium** ¹ |

**Scoring rationale:**

- **Reliability MTBF evidence S=4**: Missing MTBF validation is a direct blocking sign-off item; if unresolved, RP boards may be shipped without confirmed reliability compliance, creating potential field quality excursion.
- **Reliability MTBF evidence O=3**: Moderate likelihood that prediction work has been initiated but not formally submitted; new platforms without full characterisation data are common at PRD or early design stages.
- **Reliability MTBF evidence D=3**: Human PQRE review at sign-off would catch a missing report, but earlier milestone reviews may pass without formal check if evidence is assumed to exist.

- **Thermal MTBF S=3**: Temperature deviation from prediction assumption degrades MTBF; functional workaround available (de-rate to lower operating temperature) but may impact performance SLA.
- **Thermal MTBF O=3**: Temperature exceedance is possible without validated thermal characterisation; new CPU configurations (COR AP 20CH) may have higher thermal density.

¹ **Low Confidence flag triggered** — Data Confidence = 1 for all in-scope domains. All domains are treated as requiring elevated Engineering Manager review per `KnowledgeBase/Rules/risk_scoring_criteria.md`.

**Aggregate Risk Assessment:**

> Two domains at Medium Risk (RPN ≥ 21) with Data Confidence ≤ 2 triggers aggregate escalation to **High Risk** per risk escalation rules (Two or more domains at Medium Risk → treated as High Risk).

**Risk Band:** **High Risk** (aggregate escalation from two Medium domains with Low Confidence)
**Disposition:** **HOLD** — Blocking evidence items (Actions 1–3, 5) must be completed and reviewed before disposition can be upgraded.

---

### PQRE Recommendation

> **HOLD**
>
> This review cannot be upgraded to APPROVE or CONDITIONAL APPROVE until the four
> blocking information gaps are resolved (Information Gaps #1–4, and #10 if prior-
> generation data re-use is proposed):
>
> - **Action 1** — MTBF prediction report required for each RP board in scope.
> - **Action 2** — MTBF target requirement must be documented and confirmed.
> - **Action 3** — Operating condition assumptions must be validated against actual thermal/environmental profile.
> - **Action 5** — Design delta assessment required if prior-generation RP data re-use is proposed.
>
> Once blocking items are resolved:
> - If predicted MTBF ≥ target requirement with adequate margin (≥ 10%) at worst-case operating conditions → eligible for **APPROVE**.
> - If predicted MTBF meets target only at nominal conditions, or margin is < 10%, or confidence data is incomplete → eligible for **CONDITIONAL APPROVE** with defined closure plan.
> - If predicted MTBF does not meet target, or thermal exceedance is confirmed to reduce MTBF below target → remain **HOLD** pending corrective action.

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次 PQRE 審查由 Issue #146 觸發，主題為 **RP（Reference Platform，參考平台）板卡的 MTBF（平均故障間隔時間）** 風險審查。本次 intake 主體為空，未附任何工程數據、設計差異文件或 MTBF 預測計算書。

依 `KnowledgeBase/platform/platform_alias.yaml`，涵蓋範圍內的 RP 板卡包含：

| 平台 | 別稱 | CPU |
|---|---|---|
| ANC（Anderson City） | Pine Stream | COR AP 20CH |
| Sabre（Sabre City） | — | COR AP 20CH |
| Dunlow | — | Xeon E |
| Johnson City | JNC1、JNC2、Oak Stream AP | DMR AP |
| Basin City | BNC、COR 8CH | COR SP |

MTBF 為 **阻擋性可靠性證據項目**，依 `KnowledgeBase/Rules/pqre_signoff_criteria.md`（第 5 節 — 可靠性：「新操作條件下元件 FIT rate 或 MTBF — 阻擋：是」）規定。未提交 MTBF 預測報告、元件 FIT rate 資料或系統級可靠度方塊圖（RBD）前，無法對任何 RP 板卡放行請求正式核發 APPROVE 或 CONDITIONAL APPROVE。

> **目前 PQRE 狀態：HOLD — 資料不足；需提交可靠性證據包後方可升級處置意見。**

主要風險並非 RP 板卡 MTBF 本身一定存在問題，而是**尚未提交量化證據**以確認 MTBF 符合客戶或計畫要求。這是證據缺口問題，未必是設計缺陷。

---

### 2. 請求分類

- **請求類型：** 可靠性指標審查 — MTBF 資格準備度查詢
- **平台範圍：** 所有現行 RP 板卡（ANC、Sabre、Dunlow、JNC1/JNC2、BNC）
- **主要領域：** 可靠性（Reliability）
- **次要領域：** 熱（Thermal，操作溫度影響 MTBF）、物料（Material，元件 FIT rate）、DFT（現場回流資料可用性）
- **不在範圍：** SI、PDN、Mechanical、DFM、Regulatory（除非本次請求關聯特定 RP 設計變更）
- **目前證據等級：** 無（intake 本體為空）
- **風險等級：** 高風險（低可信度 — 未提交 MTBF 資料；Data Confidence = 1）
- **需採取行動：** 是

---

### 3. 是否需採取行動（是/否）

**是。**

MTBF 證據為 PQRE 簽核標準下的**阻擋性簽核項目**。在處置意見從 HOLD 升級前，需完成下列行動：

1. 針對範圍內每塊 RP 板卡提交 MTBF 預測報告（接受 MIL-HDBK-217、Telcordia SR-332 或 FIDES 方法論）。
2. 確認計畫規格或客戶合約要求中的 MTBF 目標值。
3. 確認預測所用操作條件（Tj_max、環境溫度、Duty Cycle、海拔）。
4. 提供關鍵 BOM 元件的 FIT rate 資料（供應商或標準零件資料庫）。

---

### 4. 已知問題

1. **未提交 MTBF 資料** — Intake 本體為空；未提供預測計算書、FIT rate 摘要或可靠性認證報告，為主要阻擋缺口。

2. **多個 RP 板卡涵蓋範圍未區分** — 請求涵蓋五個不同 RP 平台（ANC、Sabre、Dunlow、JNC1/JNC2、BNC），CPU 與配置各不相同，無法以單一 MTBF 數值代表所有平台。

3. **未說明 MTBF 目標要求** — 未引用 MTBF 目標（如 100,000 小時、200,000 小時）或參考標準，無法進行合格/不合格判定。

4. **操作條件假設未知** — MTBF 預測對 Tj、環境溫度及 Duty Cycle 高度敏感；若各平台或開發與生產配置間存在差異，預測可能不適用於現場條件。

5. **元件 FIT rate 來源未確認** — FIT rate 可能來自 MIL-HDBK-217、Telcordia SR-332、FIDES 或供應商資料表；若方法論混用或未文件化，將失去預測可追溯性。

6. **現場回流資料可用性不明** — 對有前代等效平台的板卡（如 JNC1/JNC2 DMR AP），可能存在現場回流或早期失效資料，但尚未提交以支撐或校正預測。

---

### 5. 未知風險

- **熱超限對 MTBF 的影響** — 若任何 RP 板卡在生產工作負載下操作溫度接近 Tj_max，Arrhenius 溫度加速因子可使有效 MTBF 比額定條件降低 30–50%。未提交熱特性數據前，此風險無法量化。

- **連接器與插座磨耗失效** — 用於高頻率實驗室與驗證環境的 RP 板卡，其連接器插拔次數超過現場等效值。機械磨耗失效模式通常未納入電子 MTBF 預測；若以實驗室用 MTBF 作為現場可靠性聲明，將產生過於樂觀的估計。

- **BOM 變更對 FIT rate 的影響** — 若 RP 板卡生產過程中存在元件替換（CCN/PCN），原始預測中的 FIT rate 可能已不再有效；本次 intake 未含 BOM 變更審查。

- **加速壽命測試（ALT）資料缺口** — 若系統層級無 HTOL 或 ALT 資料，MTBF 預測完全依賴零件計數法，不確定性可達 ±50%。

- **跨平台資料重用風險** — 若提議使用前代 RP（如 JNC1 DMR AP）的 MTBF 報告作為新世代平台（如 ANC COR 20CH）的證據，必須在資料重用前正式評估平台間設計差異。CPU 與晶片組變更直接影響 FIT 率主要貢獻者。

---

### 6. 影響評估

| 類別 | 影響 | 嚴重程度 |
|---|---|---|
| 可靠性 — 現場 MTBF 風險 | RP 板卡在未驗證 MTBF 情況下出貨，可能無法滿足客戶 SLA 要求 | 重大 |
| 可靠性 — 預測準確性 | 缺乏 ALT 資料的零件計數法預測不確定性高；現場 MTBF 可能與預測差異顯著 | 中等 |
| 計畫 — 簽核關卡 | MTBF 為阻擋性項目；缺失證據將延誤 PQRE 簽核與平台放行 | 重大 |
| 熱 — MTBF 敏感性 | 操作溫度偏離預測假設將降低有效 MTBF；未提交熱數據前風險無法量化 | 中等 |
| 物料 — FIT rate 有效性 | BOM 變更或元件替換可能使現有 FIT rate 輸入失效 | 中等 |
| DFT — 現場回流反饋 | 缺乏現場回流分析，早期失效率與嬰兒期死亡率風險未被描述 | 中等 |

---

### 7. 資訊缺口

| # | 缺失項目 | 領域 | 是否阻擋 |
|---|---|---|---|
| 1 | 範圍內各 RP 板卡的 MTBF 預測報告（MIL-HDBK-217 / Telcordia SR-332 / FIDES） | 可靠性 | **是** |
| 2 | 計畫規格或客戶合約中的 MTBF 目標要求 | 可靠性 | **是** |
| 3 | 預測所用操作條件假設（Tj、Ta、Duty Cycle、海拔） | 可靠性 | **是** |
| 4 | 元件 FIT rate 來源與方法論（供應商資料、標準零件資料庫或實測） | 可靠性 | **是** |
| 5 | 系統或關鍵次系統層級的 HTOL 或 ALT 資料（如有） | 可靠性 | 否 |
| 6 | 前代 RP 平台（JNC1、JNC2、BNC）現場回流 / 早期失效資料 | 可靠性 | 否 |
| 7 | 任何 RP 板卡自上次可靠性認證以來的 BOM 變更紀錄（CCN/PCN） | 物料 | 否 |
| 8 | 各 RP 平台在生產工作負載下的熱特性數據（Tj_max） | 熱 | 否 |
| 9 | 實驗室/驗證單元與現場單元的連接器插拔次數 | 機械 | 否 |
| 10 | 若提議重用前代 RP MTBF 資料，需提交設計差異評估 | 可靠性 | **是**（如提議重用） |

---

### 8. 必要行動

| # | 行動 | Owner | 截止日期 | 是否阻擋 |
|---|---|---|---|---|
| 1 | 針對範圍內各 RP 板卡（ANC、Sabre、Dunlow、JNC1/JNC2、BNC）提交 MTBF 預測報告；包含方法論、操作條件假設與 FIT rate 來源 | [待定 — 可靠性工程] | [待定] | **是** |
| 2 | 確認並文件化各 RP 平台計畫規格或客戶合約中的 MTBF 目標要求 | [待定 — 計畫/系統工程] | [待定] | **是** |
| 3 | 核實 MTBF 預測所用操作條件與實際生產/現場熱與環境條件一致；與熱特性數據比對 | [待定 — 熱工程 + 可靠性工程] | [待定] | **是** |
| 4 | 審查自上次可靠性認證以來的 BOM 變更紀錄（CCN/PCN）；重新評估已變更元件的 FIT rate | [待定 — 元件工程] | [待定] | 否 |
| 5 | 若提議將前代 RP MTBF 資料（JNC1/JNC2 或 BNC）重用於新平台，提交正式設計差異評估，說明等效性或記錄差異對 FIT 的影響 | [待定 — 可靠性工程] | [待定] | **是**（如提議重用） |
| 6 | 若有系統或關鍵次系統層級 HTOL 或 ALT 資料，請提供；若無，文件化僅依賴零件計數法的理由 | [待定 — 可靠性工程] | [待定] | 否 |
| 7 | 收集並審查前代平台（JNC1、JNC2、BNC）現場回流資料；評估 ELFR 與嬰兒期死亡率趨勢 | [待定 — 品質工程] | [待定] | 否 |

---

### 9. 風險評估

#### MTBF 證據缺口風險評分

| 領域 | Severity (S) | Occurrence (O) | Detection (D) | RPN | 資料可信度 | 風險等級 |
|---|---:|---:|---:|---:|---|---|
| 可靠性 — MTBF 證據完整性 | 4 | 3 | 3 | 36 | 1 — 未提交資料 | **中→高** ¹ |
| 可靠性 — 熱對 MTBF 的影響 | 3 | 3 | 3 | 27 | 1 — 未提交熱數據 | **中→高** ¹ |
| 物料 — BOM 變更 FIT rate 有效性 | 3 | 2 | 3 | 18 | 2 — 無 BOM 變更審查 | **低→中** ¹ |

**評分說明：**

- **可靠性 MTBF 證據 S=4**：缺少 MTBF 驗證為直接阻擋性簽核項目；若未解決，RP 板卡可能在未確認可靠性合規的情況下出貨，導致潛在現場品質逸失。
- **可靠性 MTBF 證據 O=3**：預測工作可能已啟動但尚未正式提交，屬於 PRD 或早期設計階段的常見情況。
- **可靠性 MTBF 證據 D=3**：簽核時的人工 PQRE 審查可發現缺失報告，但若假設證據存在，較早里程碑審查可能未正式核查。

¹ **觸發低可信度標誌** — 所有範圍內領域的資料可信度 = 1 或 2。依 `KnowledgeBase/Rules/risk_scoring_criteria.md` 規定，所有領域均需提升至工程主管層級審查。

**整體風險評估：**

> 兩個領域達中等風險（RPN ≥ 21）且資料可信度 ≤ 2，依風險升級規則觸發整體**高風險**升級（兩個以上中風險領域 → 視為高風險）。

**Risk Band：** **高風險**（由兩個中等風險低可信度領域整體升級）
**Disposition：** **HOLD** — 阻擋性證據項目（行動 1–3、5）須完成並通過審查後，方可升級處置意見。

---

### PQRE 建議

> **HOLD（暫停放行）**
>
> 在以下四項阻擋性資訊缺口解決前，本次審查無法升級至 APPROVE 或 CONDITIONAL APPROVE
>（資訊缺口 #1–4，以及若提議重用前代資料則加上 #10）：
>
> - **行動 1** — 需提供範圍內各 RP 板卡的 MTBF 預測報告。
> - **行動 2** — 需文件化並確認 MTBF 目標要求。
> - **行動 3** — 需核實操作條件假設與實際熱/環境條件一致。
> - **行動 5** — 若提議重用前代 RP 資料，需提交設計差異評估。
>
> 阻擋項解決後的升級路徑：
> - 若在最差操作條件下預測 MTBF ≥ 目標值且餘裕 ≥ 10% → 可核發 **APPROVE**。
> - 若預測 MTBF 僅在標稱條件下符合目標，或餘裕 < 10%，或可信度資料不完整 → 可核發 **CONDITIONAL APPROVE**（含明確完成計畫）。
> - 若預測 MTBF 未達目標，或確認熱超限導致 MTBF 低於目標 → 維持 **HOLD** 直至完成矯正行動。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-22.
Closes #146.*
