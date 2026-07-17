# PQRE Risk Review — Issue #80

**Issue:** [AI Risk Review] PRD for Anderson City 1/2 (Pine Stream COR 20CH) is now open
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/80
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-17
**Requestor:** ccgglee
**Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20 CH
**Agent Instruction:** Do we need to redo reliability stress? Could we reference JNC1 JNC2 (DMR AP) RP reliability stress data?

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #80, which records the opening of the **Product Requirements Document (PRD)** for **Anderson City (ANC) 1S / 2S** — the baseline Reference Platform (RP) for **Pine Stream COR 20 CH**. Per the platform context established in Issue #59, Anderson City is the primary Pine Stream RP supporting both single-socket (1S) and dual-socket (2S) configurations; it is the main reference platform planned for Pine Stream development and validation activities.

The intake body contains no engineering data beyond the subject line. A specific engineering question has been received via agent instruction:

> **"Do we need to redo reliability stress? Could we reference JNC1 JNC2 (DMR AP) RP reliability stress data?"**

This question is addressed in detail in Sections 4, 5, 7, and 8 below.

Because the PRD has just been opened and no quantified engineering data, design delta document, or qualification plan has been submitted with the intake, the current PQRE posture is:

> **HOLD — Insufficient data; PRD-stage guidance issued pending formal intake package.**

The reliability data re-use question (JNC1/JNC2 DMR AP RP → ANC Pine Stream COR 20CH) cannot be answered definitively without a formal design delta analysis. General PQRE guidance for this class of question is provided in Section 8 (Required Actions).

---

### 2. Request Classification

- **Request type:** PRD opening notification — early-stage PQRE intake
- **Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20 CH
- **Predecessor RP referenced in agent instruction:** JNC1 / JNC2 (DMR AP RP)
- **Domains potentially impacted:** Thermal, SI, PDN, Mechanical, DFM, DFT, Material, Regulatory, Reliability
- **Current evidence level:** None provided in issue body
- **Risk tier:** High (Low Confidence — no design data submitted)
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.**

Two parallel tracks are required:

1. **PRD intake track** — A complete engineering intake package must be submitted before PQRE can perform domain-level risk evaluation and provide a sign-off-capable recommendation for ANC Pine Stream COR 20CH.

2. **Reliability data re-use track** — A formal design delta analysis between JNC1/JNC2 (DMR AP RP) and ANC (Pine Stream COR 20CH RP) must be completed to determine whether the existing JNC1/JNC2 reliability stress data can be referenced (with or without additional stress) for ANC qualification.

Both tracks must be completed before PQRE sign-off.

---

### 4. Known Issues

1. **PRD just opened — no engineering data provided.** The intake body contains no design baseline, delta specifications, power/thermal targets, interface definitions, or validation plan for Anderson City Pine Stream COR 20CH.

2. **Platform transition from DMR AP RP to Pine Stream RP is a generation change.** Anderson City (ANC) is a new RP generation. Qualification data from JNC1/JNC2 (DMR AP RP) is from a preceding platform generation and cannot be directly applied without a formal delta analysis and gap closure plan.

3. **Reliability stress re-use requires explicit justification.** Per `KnowledgeBase/srf_cwf_pqre_comparison.md`, qualification and sign-off reuse across platforms requires an explicit gap list and closure plan. The same principle applies to RP-to-RP transitions (DMR AP → Pine Stream). Simply citing JNC1/JNC2 data without a formal comparability assessment is insufficient for PQRE sign-off.

4. **Design scope for ANC 1S vs. 2S configurations not defined.** The PRD covers both 1S and 2S variants. Each configuration may have different power delivery, thermal, and mechanical stress profiles that affect the applicability of single-platform predecessor data.

---

### 5. Unknown Risks

- **Architectural delta between DMR AP RP and Pine Stream COR 20CH RP is unknown.** Changes in CPU TDP, memory channel count (20CH vs. predecessor), interconnect interfaces (PCIe gen, UPI revision), and board form factor may invalidate the comparability of JNC1/JNC2 stress conditions to ANC operating conditions.

- **Thermal envelope delta is unknown.** If the Pine Stream COR TDP or junction temperature specification differs from DMR AP, the thermal stress conditions applied in JNC1/JNC2 HTOL runs may not bound the ANC use case.

- **Solder joint reliability (thermal cycling stress) applicability is unknown.** Board-level thermal cycling stress from DMR AP RP may not cover ANC's material stack, component mass distribution, or PCB layer count changes.

- **Memory channel increase impact on PDN and SI stress coverage is unknown.** Going from a predecessor channel count to 20 CH may introduce new impedance, crosstalk, and power delivery conditions not covered by JNC1/JNC2 test configurations.

- **2S configuration reliability coverage from JNC1/JNC2 is unknown.** If JNC1/JNC2 was primarily qualified for 1S, the 2S UPI interface stress and associated package-board interaction data may be absent.

- **ELFR (Early Life Failure Rate) data for new component steppings is unknown.** If ANC uses new silicon steppings or board revision relative to DMR AP RP, ELFR data from JNC1/JNC2 may not be representative.

---

### 6. Impact Assessment

| Category | Current Impact Assessment |
|----------|---------------------------|
| Schedule | PQRE sign-off blocked until PRD intake data and reliability delta analysis are submitted |
| Quality | Cannot determine — no design data, test plan, or qualification baseline provided |
| Compliance | Cannot determine — no material declaration or regulatory evidence provided |
| Manufacturing | Cannot determine — no DFM/DFT data or manufacturing constraints provided |
| Reliability | Potential for incomplete coverage if JNC1/JNC2 DMR AP RP data is applied without formal comparability analysis; redo risk to be determined by delta review |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | PRD technical scope — full design baseline, proposed architecture, and key parameters for ANC Pine Stream COR 20CH | All | **Yes** |
| 2 | ANC vs. JNC1/JNC2 (DMR AP RP) design delta document — CPU TDP, memory channel count, interfaces, PCB layer stack, form factor | Reliability / All | **Yes** |
| 3 | JNC1/JNC2 DMR AP RP reliability stress test report — scope, test conditions (HTOL temp/voltage, ELFR, thermal cycling), sample size, pass/fail criteria | Reliability | **Yes** |
| 4 | ANC-specific thermal specification (TDP, Tj_max, cooling solution) | Thermal / Reliability | **Yes** |
| 5 | ANC PDN specification and SI channel definition for 20CH configuration | PDN / SI | **Yes** |
| 6 | ANC qualification plan — test vehicle definition, stress conditions, acceptance criteria, and schedule | Reliability | **Yes** |
| 7 | Formal comparability assessment (or its absence): whether JNC1/JNC2 stress conditions bound ANC operating envelope | Reliability | **Yes** |
| 8 | DFM/DFT readiness data for ANC 1S and 2S board variants | DFM / DFT | **Yes** |
| 9 | Material declaration and RoHS/REACH compliance evidence for ANC | Material / Regulatory | **Yes** |
| 10 | Owner assignments and target dates for all required actions | Program management | No |

---

### 8. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Submit complete PRD intake for ANC Pine Stream COR 20CH: architecture baseline, key parameters, 1S/2S configuration scope, and qualification objectives | [TBD] | [TBD] | **Yes** |
| 2 | Complete design delta analysis: ANC Pine Stream COR 20CH vs. JNC1/JNC2 (DMR AP RP) — document all changes in TDP, memory channels, interfaces, PCB stack, and form factor | Reliability / PQRE team | [TBD] | **Yes** |
| 3 | Submit JNC1/JNC2 DMR AP RP reliability stress test reports for PQRE review: HTOL conditions, ELFR data, thermal cycling scope, sample sizes, pass/fail summary | [TBD] | [TBD] | **Yes** |
| 4 | Based on Actions 2 and 3: issue formal PQRE determination on whether JNC1/JNC2 data fully covers ANC, partially covers ANC (with supplemental stress required), or does not cover ANC (full redo required) | PQRE team | After Actions 2–3 | **Yes** |
| 5 | If supplemental or full reliability stress redo is determined in Action 4: define test plan with test conditions, sample size, duration, acceptance criteria, and schedule | [TBD] | After Action 4 | Conditional |
| 6 | Submit ANC thermal specification and PDN specification for domain review | [TBD] | [TBD] | **Yes** |
| 7 | Submit DFM/DFT, Material, and Regulatory evidence packages | [TBD] | [TBD] | **Yes** |
| 8 | Re-submit for full PQRE review after Actions 1–7 are complete | [TBD] | [TBD] | **Yes** |

---

### 9. PQRE Recommendation

> **HOLD — PRD Stage; Reliability Data Re-Use Determination Pending**
>
> The Anderson City (ANC) Pine Stream COR 20CH RP PRD has opened but the intake package contains no engineering data. PQRE sign-off cannot be issued at this stage.
>
> **Specific guidance on the reliability stress re-use question (JNC1/JNC2 DMR AP RP data):**
>
> Whether JNC1/JNC2 (DMR AP RP) reliability stress data can be referenced for ANC (Pine Stream COR 20CH RP) depends on the degree of design commonality between the two platforms. PQRE cannot approve data re-use without a formal comparability assessment. The outcome of that assessment will fall into one of three categories:
>
> - **Full re-use approved** — if the ANC design is within the stress envelope demonstrated by JNC1/JNC2 (same or lower TDP, same or fewer memory channels, same or lower-frequency interfaces, no new mechanical features outside the qualified envelope).
> - **Partial re-use with supplemental stress** — if ANC introduces specific changes (e.g., new interface speeds, higher TDP, 2S UPI stress not covered by JNC1/JNC2) that create gaps in the existing stress coverage. Targeted supplemental stress runs would be required to close those gaps.
> - **Full redo required** — if the ANC design envelope substantially exceeds the JNC1/JNC2 test conditions (e.g., significantly higher TDP, new package type, new board material system, or architectural changes that invalidate prior stress comparability).
>
> **Required steps before PQRE reliability sign-off:**
>
> 1. Submit JNC1/JNC2 DMR AP RP reliability stress reports (Action 3).
> 2. Complete ANC vs. JNC1/JNC2 design delta analysis (Action 2).
> 3. PQRE team issues formal determination (Action 4) — full re-use, partial re-use, or full redo.
> 4. If a redo or supplement is required, submit and execute the test plan (Action 5).
>
> Do not proceed to ANC Pine Stream COR 20CH PQRE reliability sign-off until the above steps are completed and reviewed.

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次 PQRE 審查由 Issue #80 觸發，記錄 **Anderson City (ANC) 1S / 2S**（**Pine Stream COR 20 CH** 基準參考平台 RP）之**產品需求文件（PRD）**正式開啟一事。依 Issue #59 所建立之平台背景，Anderson City 為 Pine Stream 主要 RP，同時支援單插槽（1S）與雙插槽（2S）配置，為 Pine Stream 開發與驗證活動的主要參考平台。

本次受理內文除主旨外不含任何工程資料。代理人指令中提出一項特定工程問題：

> **「是否需要重做可靠度壓力測試？是否可引用 JNC1/JNC2（DMR AP）RP 可靠度壓力測試資料？」**

此問題於下文第 4、5、7 及 8 節中詳細說明。

由於 PRD 剛開啟，且受理單未附上量化工程資料、設計差異文件或資格驗證計畫，當前 PQRE 結論為：

> **暫緩（HOLD）— 資料不足；PRD 階段指引已提供，待正式受理資料包提交。**

可靠度資料複用問題（JNC1/JNC2 DMR AP RP → ANC Pine Stream COR 20CH）在未完成正式設計差異分析前無法定論。本文第 8 節就此類問題提供一般性 PQRE 指引。

---

### 2. 請求分類（Request Classification）

- **請求型態：** PRD 開啟通知 — 前期 PQRE 受理
- **平台：** Anderson City (ANC) 1S / 2S — Pine Stream COR 20 CH
- **代理人指令所參照之前代 RP：** JNC1 / JNC2（DMR AP RP）
- **可能受影響領域：** Thermal、SI、PDN、Mechanical、DFM、DFT、Material、Regulatory、Reliability
- **目前證據完整度：** 受理內文未提供有效佐證
- **風險層級：** 高風險（低可信度 — 未提供設計資料）
- **是否需要行動：** 是

---

### 3. 是否需要行動（Action Required: Yes/No）

**是（Yes）。**

需同步推進兩條工作線：

1. **PRD 受理線** — 必須提交完整工程受理資料包，PQRE 方能進行各領域風險評估並提出可簽核建議。

2. **可靠度資料複用評估線** — 必須完成 JNC1/JNC2（DMR AP RP）與 ANC（Pine Stream COR 20CH RP）之間的正式設計差異分析，以確定現有可靠度壓力測試資料是否可引用（全部引用或部分引用）用於 ANC 資格驗證。

兩條工作線均須完成，方可進行 PQRE 簽核。

---

### 4. 已知問題（Known Issues）

1. **PRD 剛開啟 — 未提供工程資料。** 受理內文未包含 Anderson City Pine Stream COR 20CH 的設計基線、差異規格、功耗 / 熱設計目標、介面定義或驗證計畫。

2. **DMR AP RP 至 Pine Stream RP 為跨世代平台轉換。** Anderson City (ANC) 為新一代 RP。JNC1/JNC2（DMR AP RP）的資格驗證資料來自前代平台，未完成正式差異分析與缺口補足計畫前，不得直接套用。

3. **可靠度壓力測試資料複用需有明確依據。** 依 `KnowledgeBase/srf_cwf_pqre_comparison.md`，跨平台資格驗證資料複用須附有明確缺口清單與補足計畫。此原則同樣適用於 RP 世代間轉換（DMR AP → Pine Stream）。單純引用 JNC1/JNC2 資料而未進行可比性評估，不符合 PQRE 簽核要求。

4. **ANC 1S 與 2S 配置之設計範疇尚未定義。** PRD 涵蓋兩種配置，各自的電源完整性、熱設計及機構壓力特性可能不同，影響前代單一平台資料之適用性。

---

### 5. 未知風險（Unknown Risks）

- **DMR AP RP 與 Pine Stream COR 20CH RP 之架構差異未知。** CPU TDP、記憶體通道數（20CH 與前代差異）、互連介面（PCIe 世代、UPI 版本）及電路板板形的變更，可能使 JNC1/JNC2 壓力條件與 ANC 作業包絡不具可比性。

- **熱設計包絡差異未知。** 若 Pine Stream COR TDP 或接面溫度規格與 DMR AP 不同，JNC1/JNC2 HTOL 測試所採用的熱應力條件可能無法涵蓋 ANC 使用情境。

- **焊點可靠度（熱循環壓力）適用性未知。** DMR AP RP 的板級熱循環壓力測試，可能未能涵蓋 ANC 材料疊層、零件重量分佈或 PCB 層數變更。

- **20CH 記憶體通道增加對 PDN 與 SI 壓力覆蓋的影響未知。** 通道數增加可能引入 JNC1/JNC2 測試配置未覆蓋的新阻抗、串擾及電源完整性條件。

- **2S 配置之可靠度覆蓋範圍未知。** 若 JNC1/JNC2 主要針對 1S 進行資格驗證，2S UPI 介面壓力及相關封裝 — 電路板交互作用資料可能缺失。

- **新零件步階 ELFR（早期生命失效率）資料未知。** 若 ANC 使用相對於 DMR AP RP 的新矽片步階或新板版本，JNC1/JNC2 的 ELFR 資料可能不具代表性。

---

### 6. 影響評估（Impact Assessment）

| 類別 | 目前影響評估 |
|------|--------------|
| 時程 | 在提交 PRD 受理資料及可靠度差異分析之前，PQRE 簽核受阻 |
| 品質 | 無法判定 — 未提供設計資料、測試計畫或資格驗證基線 |
| 合規 | 無法判定 — 未提供材料宣告或法規符合證據 |
| 製造 | 無法判定 — 未提供 DFM/DFT 資料或製造限制 |
| 可靠度 | 若未完成正式可比性分析即直接引用 JNC1/JNC2 DMR AP RP 資料，可能造成覆蓋缺口；是否需重做測試待差異審查後決定 |

---

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | 阻擋性 |
|---|---------|------|--------|
| 1 | PRD 技術範疇 — ANC Pine Stream COR 20CH 完整設計基線、架構及關鍵參數 | 全域 | **是** |
| 2 | ANC 與 JNC1/JNC2（DMR AP RP）設計差異文件 — CPU TDP、記憶體通道數、介面、PCB 疊層、板形 | Reliability / 全域 | **是** |
| 3 | JNC1/JNC2 DMR AP RP 可靠度壓力測試報告 — 測試範疇、條件（HTOL 溫度 / 電壓、ELFR、熱循環）、樣本數、通過 / 失敗標準 | Reliability | **是** |
| 4 | ANC 熱設計規格（TDP、Tj_max、散熱解決方案） | Thermal / Reliability | **是** |
| 5 | ANC 20CH 配置之 PDN 規格與 SI 通道定義 | PDN / SI | **是** |
| 6 | ANC 資格驗證計畫 — 測試載具定義、壓力條件、驗收標準及時程 | Reliability | **是** |
| 7 | 正式可比性評估：JNC1/JNC2 壓力條件是否涵蓋 ANC 作業包絡 | Reliability | **是** |
| 8 | ANC 1S 與 2S 板型之 DFM/DFT 就緒資料 | DFM / DFT | **是** |
| 9 | ANC 材料宣告與 RoHS/REACH 符合證據 | Material / Regulatory | **是** |
| 10 | 所有行動項目之負責人與目標完成日期 | 專案管理 | 否 |

---

### 8. 必要行動（Required Actions）

| # | 行動 | 責任人 | 到期日 | 阻擋性 |
|---|------|--------|--------|--------|
| 1 | 提交 ANC Pine Stream COR 20CH 完整 PRD 受理資料：架構基線、關鍵參數、1S/2S 配置範疇及資格驗證目標 | [TBD] | [TBD] | **是** |
| 2 | 完成設計差異分析：ANC Pine Stream COR 20CH vs. JNC1/JNC2（DMR AP RP） — 記錄 TDP、記憶體通道數、介面、PCB 疊層及板形之所有變更 | 可靠度 / PQRE 團隊 | [TBD] | **是** |
| 3 | 提交 JNC1/JNC2 DMR AP RP 可靠度壓力測試報告供 PQRE 審查：HTOL 條件、ELFR 資料、熱循環範疇、樣本數、通過 / 失敗摘要 | [TBD] | [TBD] | **是** |
| 4 | 依據行動 2 與 3 出具 PQRE 正式判定：JNC1/JNC2 資料是否完全涵蓋 ANC、部分涵蓋（需補充測試）或不涵蓋（需全部重做） | PQRE 團隊 | 行動 2–3 完成後 | **是** |
| 5 | 若行動 4 判定需補充或全部重做：定義測試計畫（測試條件、樣本數、持續時間、驗收標準及時程） | [TBD] | 行動 4 完成後 | 視情況 |
| 6 | 提交 ANC 熱設計規格與 PDN 規格供各領域審查 | [TBD] | [TBD] | **是** |
| 7 | 提交 DFM/DFT、Material 及 Regulatory 證據包 | [TBD] | [TBD] | **是** |
| 8 | 完成行動 1–7 後重新提交完整 PQRE 審查 | [TBD] | [TBD] | **是** |

---

### 9. PQRE 建議（PQRE Recommendation）

> **暫緩（HOLD）— PRD 階段；可靠度資料複用判定待決**
>
> Anderson City (ANC) Pine Stream COR 20CH RP PRD 已開啟，但受理資料包不含工程資料，當前階段無法進行 PQRE 簽核。
>
> **針對可靠度壓力測試複用問題（JNC1/JNC2 DMR AP RP 資料）之具體指引：**
>
> JNC1/JNC2（DMR AP RP）可靠度壓力測試資料是否可引用於 ANC（Pine Stream COR 20CH RP），取決於兩平台設計共通程度。PQRE 在未完成正式可比性評估前，無法核准資料複用。評估結果可能落入以下三種情形之一：
>
> - **可全部複用** — 若 ANC 設計落在 JNC1/JNC2 已驗證之壓力包絡範圍內（TDP 相同或更低、記憶體通道數相同或更少、介面頻率相同或更低、機構特性未超出已驗證包絡）。
> - **部分複用 + 補充測試** — 若 ANC 引入特定變更（例如：新介面速率、更高 TDP、JNC1/JNC2 未涵蓋之 2S UPI 壓力），造成現有壓力覆蓋缺口，需針對缺口執行補充壓力測試。
> - **需全部重做** — 若 ANC 設計包絡實質超出 JNC1/JNC2 測試條件（例如：TDP 顯著提高、新封裝型式、新板材系統，或使前代壓力可比性失效之架構變更）。
>
> **可靠度 PQRE 簽核所需步驟：**
>
> 1. 提交 JNC1/JNC2 DMR AP RP 可靠度壓力測試報告（行動 3）。
> 2. 完成 ANC vs. JNC1/JNC2 設計差異分析（行動 2）。
> 3. PQRE 團隊出具正式判定（行動 4） — 全部複用、部分複用或全部重做。
> 4. 若需重做或補充：提交並執行測試計畫（行動 5）。
>
> 在完成並審查上述步驟之前，請勿推進 ANC Pine Stream COR 20CH PQRE 可靠度簽核。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-17.
This review is an advisory output. Final engineering decisions require human sign-off.*
