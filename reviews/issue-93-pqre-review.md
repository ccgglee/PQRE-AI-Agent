# PQRE Risk Review — Issue #93

**Issue:** [AI Risk Review] FW: Pine Stream COR AP 20CH - Budgetary Demand Collection Kick off meeting
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/93
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-17
**Requestor:** ccgglee
**Platform:** Pine Stream COR AP 20CH
**Agent Instruction:** About H-TDP SKUs — is it a more severe config compared to the normal system?

---

## English

### 1. Executive Summary

This review was triggered by Issue #93, a forwarded email related to the
**Pine Stream COR AP 20CH Budgetary Demand Collection Kick-off Meeting**.
The agent instruction poses a specific technical question:

> **"About H-TDP SKUs — is it a more severe config compared to the normal system?"**

**Answer: Yes. H-TDP (High Thermal Design Power) SKUs represent a materially
more severe operating configuration than standard TDP SKUs across multiple PQRE
domains, and they constitute a distinct qualification scope.**

H-TDP SKUs are defined by a higher rated TDP compared to the base/nominal TDP
configuration for the same processor family. This elevated power envelope
increases thermal load, current demand, thermomechanical stress, and accelerated
wearout exposure across the following domains:

- **Thermal:** Higher TDP → higher junction temperature (Tj) → reduced thermal
  margin, increased risk of thermal runaway if the cooling solution is not
  re-validated at H-TDP conditions.
- **PDN:** Higher TDP → higher peak and sustained current → higher risk of PDN
  impedance overshoot, VR load-line violation, and voltage droop if the PDN was
  sized for the base TDP.
- **Reliability:** Higher Tj accelerates all major semiconductor wearout
  mechanisms (electromigration, TDDB, HCI, NBTi). HTOL and ELFR data obtained
  at base TDP are **not transferable** to H-TDP SKUs without re-qualification or
  formal comparability assessment.
- **Mechanical:** Higher thermal gradient between H-TDP and ambient generates
  greater CTE mismatch stress on solder joints, board flex, and socket retention
  forces.
- **Derating:** H-TDP SKUs may push rail currents, capacitor ESR loading, and
  connector current ratings beyond the derating limits established for standard
  TDP configurations.

**Overall risk posture for H-TDP SKU inclusion: HIGH RISK — distinct
qualification activities are required before H-TDP SKUs can be PQRE-approved.**

---

### 2. Request Classification

- **Request type:** Technical query during demand collection kick-off
- **Platform:** Pine Stream COR AP 20CH
- **SKU type in question:** H-TDP (High Thermal Design Power) variant vs. base/standard TDP SKU
- **Domains impacted by H-TDP:** Thermal, PDN, Reliability, Mechanical, Derating
- **Domains not directly changed by TDP increase:** DFT, Material, Regulatory
  *(assuming no PCB layout, material stack, or component changes beyond power delivery)*
- **Risk tier:** High Risk
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.** H-TDP SKUs require separate qualification evidence from standard TDP
SKUs. Existing qualification data from normal TDP systems cannot be directly
re-used for H-TDP SKUs without a formal comparability assessment and
gap-fill plan.

---

### 4. Known Issues

1. **H-TDP increases junction temperature (Tj) above the standard TDP
   baseline.** Higher Tj accelerates all thermally-activated wearout mechanisms.
   Any reliability stress data (HTOL, ELFR, thermal cycling) conducted at
   standard TDP conditions is not directly applicable to H-TDP SKUs.

2. **H-TDP imposes higher peak and sustained current on the PDN.** VR
   specifications, load-line settings, PDN impedance targets, and decoupling
   capacitor BOM may all need to be revisited for the H-TDP power envelope.

3. **Cooling solution adequacy is unconfirmed for H-TDP.** The thermal
   resistance budget (θja, θjb) and cooling solution specification (heatsink,
   TIM, airflow) that were validated for the standard TDP may be insufficient
   at H-TDP.

4. **Mechanical stress increases with higher thermal load.** The thermomechanical
   cycling amplitude (ΔT) is larger for H-TDP operation, increasing solder joint
   fatigue accumulation rate and CTE mismatch stress on the CPU package-to-board
   interface.

5. **Demand collection context — H-TDP SKU scope not yet defined.** The issue
   originates from a budgetary demand collection kick-off. It is not yet confirmed
   whether H-TDP SKUs are part of the Pine Stream COR AP 20CH RP scope, what the
   H-TDP wattage value is, or which cooling solutions are targeted.

---

### 5. Unknown Risks

- **Exact H-TDP wattage is unknown.** The severity of re-qualification impact
  depends on the delta between standard TDP and H-TDP. A 5% increase is a
  different risk profile from a 30%+ increase.
- **Whether H-TDP SKUs are in the current Pine Stream COR AP 20CH RP scope is
  unknown.** If H-TDP SKUs are out of scope for the RP, this question is
  informational only.
- **Whether Pine Stream COR AP 20CH will share a cooling solution with DMR-AP
  platforms is unknown.** If the cooling solution carries over, its H-TDP
  adequacy must still be re-validated.
- **H-TDP reliability stress test scope is unknown.** It is not confirmed whether
  Intel component qualification at H-TDP has been or will be completed prior to
  system-level RP qualification.
- **PDN BOM for H-TDP (VR spec, decoupling BOM) is unknown** and may differ from
  the standard TDP configuration.

---

### 6. Impact Assessment

| Domain | Impact of H-TDP vs. Standard TDP | Severity |
|--------|----------------------------------|----------|
| Thermal | Higher Tj; cooling solution must be re-validated at H-TDP | **High** |
| PDN | Higher current; VR load-line, PDN impedance, and decoupling BOM must be re-checked | **High** |
| Reliability | HTOL, ELFR, and thermal cycling data at standard TDP **not transferable** | **High** |
| Mechanical | Larger ΔT → higher solder joint fatigue and CTE stress | **Medium** |
| Derating | Rail current and component ratings must be re-verified at H-TDP | **Medium** |
| DFM/DFT | No expected change unless H-TDP requires layout or component change | **Low** |
| Material/Regulatory | No expected change unless new components are added for H-TDP PDN | **Low** |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | H-TDP wattage value for Pine Stream COR AP 20CH — confirmed TDP delta vs. standard SKU | Thermal / PDN | **Yes** |
| 2 | Thermal simulation or test data at H-TDP conditions (Tj, θja, cooling solution margin) | Thermal | **Yes** |
| 3 | PDN analysis at H-TDP — VR spec, load-line, peak current, PDN impedance simulation | PDN | **Yes** |
| 4 | Reliability stress test scope for H-TDP SKUs — HTOL temperature/voltage, ELFR, thermal cycling conditions | Reliability | **Yes** |
| 5 | Cooling solution specification for H-TDP — heatsink, TIM, airflow, Tj_max budget | Thermal | **Yes** |
| 6 | Derating table re-verification for H-TDP current/power levels on all affected rails | Derating | **Yes** |
| 7 | Solder joint reliability re-assessment under H-TDP ΔT cycling profile | Mechanical | **Yes** |
| 8 | Confirmation of whether H-TDP SKUs are in scope for Pine Stream COR AP 20CH RP | All | **Yes** |
| 9 | Intel component qualification status at H-TDP (component-level cert available?) | Reliability | No |
| 10 | SKU ordering guide confirming H-TDP vs. standard TDP product differentiation | Program | No |

---

### 8. Risk Assessment

#### H-TDP Thermal Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 4 | H-TDP increases Tj; if cooling solution is not re-validated, system thermal failure is possible |
| Occurrence | 3 | H-TDP is a known delta from standard TDP; thermal issues occur when margin is not re-assessed |
| Detection | 3 | Thermal monitoring exists but may not detect margin erosion before damage under sustained H-TDP load |
| **RPN** | **36** | Medium Risk — engineering evidence required |
| Data Confidence | 1 | No H-TDP thermal data provided; H-TDP wattage not confirmed |

> Because Data Confidence = 1 (≤ 2), the **Low Confidence** flag is triggered
> and this domain is treated as **High Risk** pending data submission.

#### H-TDP Reliability Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 4 | Higher Tj accelerates EM, TDDB, HCI, NBTi; potential field failure if not re-qualified |
| Occurrence | 4 | Standard TDP reliability data is not transferable to H-TDP without assessment |
| Detection | 3 | Reliability degradation may not be detectable during normal functional testing |
| **RPN** | **48** | Medium Risk — approaching High threshold |
| Data Confidence | 1 | No H-TDP reliability test data provided |

> Because Data Confidence = 1 (≤ 2), the **Low Confidence** flag is triggered
> and this domain is treated as **High Risk** pending data submission.

#### H-TDP PDN Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 3 | PDN under-sizing causes voltage droop and potential functional failures |
| Occurrence | 3 | Likely requires PDN re-simulation if H-TDP current exceeds current VR spec headroom |
| Detection | 2 | PDN monitoring and simulation are standard engineering checks |
| **RPN** | **18** | Low-Medium Risk — simulation required |
| Data Confidence | 1 | No H-TDP PDN data provided |

> Because Data Confidence = 1 (≤ 2), the **Low Confidence** flag is triggered.

#### Overall Risk Posture

**HIGH RISK** — Multiple domains (Thermal, Reliability, PDN) are simultaneously
Low Confidence. Per escalation rules, two or more domains at High Risk elevates
the aggregate to **High Risk**. Sign-off on H-TDP SKU inclusion is **BLOCKED**
until thermal, reliability, and PDN evidence at H-TDP conditions are provided.

---

### 9. PQRE Recommendation

> **HOLD — H-TDP SKU Qualification Evidence Required**
>
> H-TDP SKUs represent a more severe operating configuration than standard TDP
> SKUs across Thermal, PDN, Reliability, and Mechanical domains. The following
> technical guidance applies:
>
> **1. Thermal:** The cooling solution (heatsink, TIM, airflow) validated for
> standard TDP must be formally re-assessed at H-TDP. Provide Tj simulation and
> bench test data demonstrating margin compliance at H-TDP with the target
> cooling solution. Tj_max from the component datasheet must not be exceeded
> under any operating condition.
>
> **2. PDN:** Re-simulate or re-measure PDN impedance and VR load-line compliance
> at H-TDP peak and sustained current. Confirm decoupling BOM adequacy. If the
> H-TDP current exceeds the current VR spec headroom, a VR upgrade or PDN BOM
> change is required before approval.
>
> **3. Reliability:** Standard TDP HTOL and ELFR data are **not directly
> applicable** to H-TDP SKUs. A formal comparability assessment is required.
> If the Tj increase under H-TDP is significant (typically > 5–10°C above
> standard TDP Tj), a new HTOL test at H-TDP conditions is required. Lifetest
> Arrhenius extrapolation from standard TDP data cannot be assumed valid without
> analysis.
>
> **4. Mechanical:** Re-assess solder joint reliability under the H-TDP thermal
> cycling profile (larger ΔT). If the new cycling amplitude exceeds the validated
> range, Coffin-Manson lifetime re-calculation or new thermal cycling test data
> is required.
>
> **5. Derating:** Re-verify all affected component ratings (VR, capacitors,
> connectors, PCB copper current capacity) at H-TDP operating current and power.
>
> Do not approve H-TDP SKU inclusion in the Pine Stream COR AP 20CH RP BOM until
> the evidence items in Section 7 are submitted and reviewed by PQRE.

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次審查由 Issue #93 觸發，主題為 **Pine Stream COR AP 20CH 預算需求收集啟動會議**。
代理人指令提出以下具體技術問題：

> **「關於 H-TDP SKU — 其配置是否比一般系統更為嚴苛？」**

**答：是的。H-TDP（高熱設計功耗）SKU 在多個 PQRE 領域中，均代表比標準 TDP SKU
更為嚴苛的操作配置，且需視為獨立的資格驗證範疇。**

H-TDP SKU 以高於同處理器家族基準/標稱 TDP 的額定功耗為定義特徵。此較高功耗包絡
提升了熱負荷、電流需求、熱機械應力，並加速以下領域的老化暴露量：

- **Thermal（熱設計）：** TDP 升高 → 接面溫度（Tj）升高 → 熱設計餘裕降低，若散熱方案未在 H-TDP 條件下重新驗證，存在熱失控風險。
- **PDN（電源分配網路）：** TDP 升高 → 峰值與持續電流升高 → 若 PDN 按標準 TDP 設計，存在阻抗超標、VR 負載線違規與電壓跌落風險。
- **Reliability（可靠度）：** Tj 升高加速所有主要半導體磨損機制（電致遷移、TDDB、HCI、NBTi）。在標準 TDP 條件下取得的 HTOL 及 ELFR 資料，**不可直接套用於 H-TDP SKU**，須進行重新資格驗證或正式可比性評估。
- **Mechanical（機構）：** H-TDP 操作產生更大的溫度梯度（ΔT），增加銲錫接點疲勞累積速率與 CPU 封裝至板面 CTE 不匹配應力。
- **Derating（降額）：** H-TDP SKU 可能使電源軌電流、電容 ESR 負載及連接器電流額定值超出標準 TDP 配置所建立的降額限制。

**H-TDP SKU 納入之整體風險態勢：高風險 — 需完成獨立資格驗證活動，方可核准 H-TDP SKU。**

---

### 2. 請求分類（Request Classification）

- **請求型態：** 需求收集啟動會議中的技術查詢
- **平台：** Pine Stream COR AP 20CH
- **問題 SKU 類型：** H-TDP（高熱設計功耗）變體 vs. 基準/標準 TDP SKU
- **H-TDP 影響領域：** Thermal、PDN、Reliability、Mechanical、Derating
- **H-TDP 不直接影響領域：** DFT、Material、Regulatory
  *（假設除電源輸送外，PCB 佈局、材料疊層、元器件均無變更）*
- **風險層級：** 高風險
- **是否需要行動：** 是

---

### 3. 是否需要行動（Action Required: Yes/No）

**是（Yes）。** H-TDP SKU 需要獨立的資格驗證證據，不能直接引用標準 TDP 系統的現有資格驗證資料，須完成正式可比性評估與缺口補足計畫。

---

### 4. 已知問題（Known Issues）

1. **H-TDP 使接面溫度（Tj）高於標準 TDP 基線。** Tj 升高加速所有熱激活磨損機制。在標準 TDP 條件下執行的可靠度壓力資料（HTOL、ELFR、熱循環）不可直接適用於 H-TDP SKU。

2. **H-TDP 對 PDN 施加更高的峰值與持續電流。** VR 規格、負載線設定、PDN 阻抗目標及去耦電容 BOM，均可能需針對 H-TDP 功耗包絡重新審查。

3. **H-TDP 散熱方案充分性尚未確認。** 為標準 TDP 驗證的熱阻預算（θja、θjb）及散熱方案規格（散熱器、TIM、氣流量），在 H-TDP 下可能不足。

4. **熱機械應力隨熱負荷升高而增加。** H-TDP 操作下，熱循環幅度（ΔT）更大，加速銲錫接點疲勞累積，並增加 CPU 封裝與電路板介面的 CTE 不匹配應力。

5. **需求收集階段 — H-TDP SKU 範疇尚未定義。** 本 Issue 源自預算需求收集啟動會議。H-TDP SKU 是否列入 Pine Stream COR AP 20CH RP 範疇、H-TDP 功耗值及目標散熱方案，均尚未確認。

---

### 5. 未知風險（Unknown Risks）

- **H-TDP 精確功耗值未知。** 重新資格驗證的嚴重程度取決於標準 TDP 與 H-TDP 的差值。5% 的增量與 30% 以上的增量代表截然不同的風險狀況。
- **H-TDP SKU 是否在 Pine Stream COR AP 20CH RP 現行範疇內未知。** 若 H-TDP SKU 不在 RP 範疇，本問題僅為資訊性查詢。
- **Pine Stream COR AP 20CH 是否將與 DMR-AP 平台共用散熱方案未知。** 即使共用散熱方案，其 H-TDP 充分性仍需重新驗證。
- **H-TDP 可靠度壓力測試範疇未知。** 尚未確認 Intel 元器件資格驗證是否已在 H-TDP 條件下完成。
- **H-TDP 的 PDN BOM（VR 規格、去耦 BOM）未知**，可能與標準 TDP 配置不同。

---

### 6. 影響評估（Impact Assessment）

| 領域 | H-TDP vs. 標準 TDP 之影響 | 嚴重程度 |
|------|--------------------------|----------|
| Thermal | Tj 升高；散熱方案須在 H-TDP 條件下重新驗證 | **高** |
| PDN | 電流升高；VR 負載線、PDN 阻抗及去耦 BOM 須重新確認 | **高** |
| Reliability | 標準 TDP 的 HTOL、ELFR 及熱循環資料**不可直接套用** | **高** |
| Mechanical | ΔT 更大 → 銲錫接點疲勞與 CTE 應力升高 | **中** |
| Derating | 需在 H-TDP 電流/功耗水準下重新驗證元器件額定值 | **中** |
| DFM/DFT | 除非 H-TDP 要求佈局或元器件變更，否則預期無影響 | **低** |
| Material/Regulatory | 除非 H-TDP PDN 新增元器件，否則預期無影響 | **低** |

---

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | 阻擋性 |
|---|---------|------|--------|
| 1 | Pine Stream COR AP 20CH H-TDP 功耗值 — 確認與標準 SKU 的 TDP 差值 | Thermal / PDN | **是** |
| 2 | H-TDP 條件下的熱模擬或測試資料（Tj、θja、散熱方案餘裕） | Thermal | **是** |
| 3 | H-TDP 的 PDN 分析 — VR 規格、負載線、峰值電流、PDN 阻抗模擬 | PDN | **是** |
| 4 | H-TDP SKU 可靠度壓力測試範疇 — HTOL 溫度/電壓、ELFR、熱循環條件 | Reliability | **是** |
| 5 | H-TDP 散熱方案規格 — 散熱器、TIM、氣流量、Tj_max 預算 | Thermal | **是** |
| 6 | 所有受影響電源軌的 H-TDP 電流/功耗水準降額表重新驗證 | Derating | **是** |
| 7 | H-TDP ΔT 循環剖面下的銲錫接點可靠度重新評估 | Mechanical | **是** |
| 8 | 確認 H-TDP SKU 是否列入 Pine Stream COR AP 20CH RP 範疇 | 全域 | **是** |
| 9 | Intel 元器件 H-TDP 資格驗證狀態（元器件級認證是否已可取得？） | Reliability | 否 |
| 10 | 確認 H-TDP 與標準 TDP 產品區分的 SKU 訂購指南 | 專案管理 | 否 |

---

### 8. 風險評估（Risk Assessment）

#### H-TDP Thermal 領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 4 | H-TDP 升高 Tj；若散熱方案未重新驗證，系統熱失效可能發生 |
| Occurrence（發生機率） | 3 | H-TDP 為標準 TDP 之已知差值；未重新評估餘裕時，熱問題可能發生 |
| Detection（可偵測性） | 3 | 熱監控機制存在，但在持續 H-TDP 負荷下可能無法於損壞前偵測餘裕侵蝕 |
| **RPN** | **36** | 中風險 — 需提供工程佐證 |
| Data Confidence | 1 | 未提供 H-TDP 熱資料；H-TDP 功耗值尚未確認 |

> Data Confidence = 1（≤ 2），觸發**低可信度**旗標，本領域升級為**高風險**，待資料提交後再行評估。

#### H-TDP Reliability 領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 4 | Tj 升高加速 EM、TDDB、HCI、NBTi；若未重新資格驗證，存在現場失效潛力 |
| Occurrence（發生機率） | 4 | 標準 TDP 可靠度資料不可不經評估直接轉用於 H-TDP SKU |
| Detection（可偵測性） | 3 | 可靠度退化在一般功能測試中可能無法偵測 |
| **RPN** | **48** | 中風險 — 接近高風險門檻 |
| Data Confidence | 1 | 未提供 H-TDP 可靠度測試資料 |

> Data Confidence = 1（≤ 2），觸發**低可信度**旗標，本領域升級為**高風險**，待資料提交後再行評估。

#### H-TDP PDN 領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 3 | PDN 設計不足導致電壓跌落及潛在功能失效 |
| Occurrence（發生機率） | 3 | 若 H-TDP 電流超過現行 VR 規格容限，可能需重新進行 PDN 模擬 |
| Detection（可偵測性） | 2 | PDN 監控與模擬為標準工程確認項目 |
| **RPN** | **18** | 低中風險 — 需進行模擬確認 |
| Data Confidence | 1 | 未提供 H-TDP PDN 資料 |

> Data Confidence = 1（≤ 2），觸發**低可信度**旗標。

#### 整體風險態勢

**高風險** — Thermal、Reliability、PDN 多個領域同時處於低可信度狀態。依照升級規則，兩個以上領域達高風險，整體升級為**高風險**。H-TDP SKU 納入之簽核**暫緩**，直至 Thermal、Reliability 及 PDN 在 H-TDP 條件下的佐證資料提交並通過審查。

---

### 9. PQRE 建議（PQRE Recommendation）

> **暫緩（HOLD）— 需提交 H-TDP SKU 資格驗證佐證**
>
> H-TDP SKU 在 Thermal、PDN、Reliability 及 Mechanical 領域中，均代表比標準 TDP SKU 更為嚴苛的操作配置。適用以下技術指引：
>
> **1. Thermal（熱設計）：** 需正式重新評估為標準 TDP 驗證的散熱方案（散熱器、TIM、氣流量）在 H-TDP 條件下的適用性。需提供 H-TDP 下的 Tj 模擬與實測資料，確認在目標散熱方案下符合餘裕要求。任何操作條件下均不得超過元器件資料手冊中的 Tj_max。
>
> **2. PDN（電源分配網路）：** 需在 H-TDP 峰值與持續電流條件下重新模擬或量測 PDN 阻抗與 VR 負載線符合性，確認去耦 BOM 充分性。若 H-TDP 電流超過現行 VR 規格容限，則在核准前需進行 VR 升規或 PDN BOM 變更。
>
> **3. Reliability（可靠度）：** 標準 TDP 的 HTOL 與 ELFR 資料**不可直接適用**於 H-TDP SKU。需進行正式可比性評估。若 H-TDP 下的 Tj 升高幅度顯著（通常高於標準 TDP Tj 超過 5–10°C），則需在 H-TDP 條件下執行新的 HTOL 測試。不可在未分析的情況下假設以標準 TDP 資料進行 Arrhenius 外推有效。
>
> **4. Mechanical（機構）：** 需在 H-TDP 熱循環剖面（較大 ΔT）下重新評估銲錫接點可靠度。若新的循環幅度超出已驗證範圍，則需重新進行 Coffin-Manson 壽命計算或新的熱循環測試。
>
> **5. Derating（降額）：** 需在 H-TDP 操作電流與功耗下重新驗證所有受影響元器件額定值（VR、電容、連接器、PCB 銅箔載流能力）。
>
> 在 Section 7 所列佐證項目提交並經 PQRE 審查前，不得核准 H-TDP SKU 納入 Pine Stream COR AP 20CH RP BOM。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-17.
This review is an advisory output. Final engineering decisions require human sign-off.*
