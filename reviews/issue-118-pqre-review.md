# PQRE Risk Review — Issue #118

**Issue:** [AI Risk Review] Meeting Notes: ww29 COR-8CH SXT
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/118
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-21
**Requestor:** ccgglee (DCAI Q&R — Boards & Systems)
**Meeting Date:** WW29'2026 (Thursday, July 16, 2026)
**Platform:** Coral SP COR-8CH SXT (Oak Stream RP SXT Program)

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #118, which contains the meeting minutes
from the **WW29 COR-8CH SXT program meeting** held on Thursday, July 16, 2026.
The Coral SP platform (8-Channel SXT) is in active pre-production development. The
meeting minutes document an ongoing action item tracker with items open since as
far back as WW10'26, plus new action items and program passdowns originating in WW29.

**Three engineering risk domains are identified in this review:**

- **Medium Risk — SI (Signal Integrity): DC-SCM PCB Stack-Up Impedance Review:**
  A new WW29 action item (owner: Pedro) requires the PCB stack-up to be sent to
  the vendor for impedance review. The PCB supplier for DC-SCM is confirmed, but
  no impedance review data, stack-up specification, or target impedance values are
  present in this issue. This is an open SI gap that must be closed before board
  fabrication can be committed.

- **Medium Risk — Mechanical: Scramble Socket Lifecycle and ERB Build Plan:**
  The meeting documents cycle life assumptions for the scramble socket
  (50 cycles with power, 100 cycles without power) and an ERB board quantity of
  61 units. No qualification data, vendor datasheet, or formal cycle-life test
  report for the scramble socket is attached. Exceeding rated insertion cycles
  risks socket contact degradation and unreliable test results during platform
  validation.

- **Low–Medium Risk — DFT/Program: N-1 Interposer Usage by SMC in 1H'27:**
  SMC will use N-1 interposers because CPUs are confirmed not to be available in
  1H'27. No formal DFT impact assessment or interoperability qualification between
  N-1 interposers and the COR-8CH SXT platform is documented. N-1 hardware deltas
  may affect test coverage, debug capability, and platform validation timing.

**Overall risk posture: MEDIUM RISK.** No single domain reaches RPN ≥ 51, but
multiple domains carry open evidence gaps with Data Confidence ≤ 2. Per escalation
rules, two or more domains at Medium Risk elevates the aggregate to High Risk
pending closure of blocking actions. Sign-off cannot be issued until the SI
stack-up impedance review, scramble socket qualification data, and N-1 interposer
DFT assessment are submitted.

---

### 2. Request Classification

- **Request type:** Program meeting minutes — action item tracker and passdown intake
- **Platform:** Coral SP COR-8CH SXT (Oak Stream RP SXT Program)
- **Meeting reference:** WW29'2026, Thursday July 16, 2026 — Recap via Microsoft Teams
- **Domains in scope:** SI (PCB impedance), Mechanical (scramble socket), DFT/Program
  (N-1 interposer), Material/Procurement (validation HW, thermal tools, DIMM demand)
- **Domains out of scope:** Thermal, PDN, Reliability stress, Regulatory, DFM
  *(no thermal simulation, power delivery, reliability test, or regulatory content
  present in the meeting notes)*
- **Risk tier:** Medium Risk (aggregate; see Risk Assessment in Section 8)
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.** Three blocking actions (Actions 1–3 in Section 8) must be resolved before
PQRE can issue a sign-off-capable recommendation. Additionally, several non-blocking
actions (Actions 4–7) are required to complete the information picture.

---

### 4. Known Issues

1. **DC-SCM PCB stack-up impedance review pending:** A new WW29 action item
   requires Pedro to send the DC-SCM board stack-up to Jack and Mark Chen for
   forwarding to the PCB vendor for impedance review. No stack-up document,
   controlled impedance specification, or review result is available in the issue.
   Both vendor and Intel impedance review are required. This is a pre-fabrication
   gate for SI compliance.

2. **Scramble socket cycle life not formally qualified in this intake:**
   The meeting notes state usage assumptions of 50 cycles (with power) and 100
   cycles (without power) for the scramble socket. An ERB board quantity of 61 is
   documented. No formal qualification report, vendor-stated cycle life limit, or
   test data is provided to validate these assumptions. Cycle-life exceedance
   would degrade socket contact reliability and invalidate test results.

3. **N-1 interposer use by SMC confirmed for 1H'27:** Thu confirms that SMC will
   not receive COR-8CH CPUs in 1H'27. SMC will therefore use N-1 interposers for
   validation activities during this period. No DFT compatibility matrix, formal
   delta assessment between N-1 and COR-8CH, or test coverage gap analysis is
   documented.

4. **Multiple procurement and logistics action items open since WW10'26:**
   Several action items covering DVH validation hardware ordering/deployment,
   billback uncertainty, and thermal tool procurement have been open since WW10'26
   (approximately 19 weeks). Several remain without a closed status or target date.
   Prolonged open procurement actions may create supply shortages that delay
   platform validation milestones.

5. **HCC (Hardware Checkpoint/Commit) scheduled for WW30, EC TBD:**
   The HCC milestone is approaching imminently (next week). Engineering Commit (EC)
   date is not yet determined. Key engineering gaps (PCB impedance, scramble socket
   qualification) must be resolved before or at HCC to avoid carrying open risk
   into hardware commitment.

---

### 5. Unknown Risks

- **DC-SCM PCB impedance review outcome:** Whether the vendor's impedance analysis
  will identify stack-up non-conformance, controlled impedance layer misalignment,
  or trace geometry corrections needed is unknown until the review is completed.

- **Scramble socket supplier cycle life specification:** The actual vendor-rated
  insertion cycle limit for the specific scramble socket used on COR-8CH SXT is
  not documented in the meeting notes. If the vendor limit is lower than the
  assumed 50/100 cycle guidance, existing ERB build and validation plans may
  need revision.

- **DFT coverage gap from N-1 interposer usage:** The functional, SI, and DFT
  test coverage delta between COR-8CH native HW and N-1 interposers is unknown.
  Silicon validation on N-1 HW may miss COR-8CH-specific failure modes.

- **MDP demand for SMC and N-1 HW:** Whether any team has formally entered demand
  for SMC N-1 hardware through the POB/PO Sample Event (opening WW30) is unconfirmed.
  A missed demand entry could delay SMC's validation readiness.

- **Maple Stream SharePoint migration impact:** Gloria is investigating changing the
  current SXT SharePoint to a generic name to host all platforms. Until this is
  finalized, engineering teams may access stale or misdirected links, creating
  documentation traceability risk.

- **Bare board and test coupon demand completeness:** Tracking of bare board and
  test coupon needs was added to the ordering guide (WW19 action, closed WW17).
  Whether all teams have entered their requirements into the POB/PO Sample Event
  is not confirmed in the meeting notes.

---

### 6. Impact Assessment

| Category | Impact | Severity |
|----------|--------|----------|
| SI — DC-SCM PCB impedance | Stack-up impedance not yet validated; board fabrication cannot proceed without vendor and Intel impedance review sign-off | **Significant** |
| Mechanical — Scramble socket lifecycle | Cycle life assumptions undocumented relative to vendor qualification; risk of contact degradation during ERB/validation phase | **Moderate** |
| DFT/Program — N-1 interposer usage | Validation on N-1 HW may not cover COR-8CH-specific failure modes; test coverage gap unquantified | **Moderate** |
| Program — HCC milestone readiness | HCC at WW30 with open SI and socket engineering gaps; EC date not set; risk of carrying unresolved technical debt past hardware commit | **Significant** |
| Material — Procurement action items (WW10) | Long-outstanding procurement ARs (DVH HW, thermal tools, billback clarity) may compress material availability window ahead of validation builds | **Low–Moderate** |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | DC-SCM PCB stack-up document and controlled impedance specification; vendor and Intel impedance review results | SI | **Yes** |
| 2 | Scramble socket vendor qualification data: rated insertion cycle limit, contact resistance spec, and applicable lot/part number for COR-8CH SXT | Mechanical | **Yes** |
| 3 | N-1 interposer DFT compatibility assessment: delta analysis vs. COR-8CH native HW, test coverage gap, and SMC WW30 demand entry confirmation | DFT / Program | **Yes** |
| 4 | HCC readiness checklist: list of open technical gates (beyond this review) required to be closed before WW30 HCC | Program | No |
| 5 | Thermal tool procurement path decision: confirmation of whether Intel or SMC owns procurement of Thermal Margining and Debug tools post WW28 PRD window | Material | No |
| 6 | ERB board build plan vs. scramble socket cycle life budget: total cycles planned across all validation teams vs. rated limit | Mechanical | No |
| 7 | DVH validation hardware ordering and deployment plan: final decision on Sigmatron (boards) vs. separate procurement (thermal tools, debug tools) | Material | No |
| 8 | Risk scoring inputs (S/O/D) and data confidence values for SI and Mechanical domains from responsible engineers | SI / Mechanical | No |

---

### 8. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Send DC-SCM PCB stack-up to Jack and Mark Chen; coordinate SMC to distribute to PCB vendor for impedance review; submit review results to this PQRE issue | Pedro / Jack / SMC | Before WW30 HCC | **Yes** |
| 2 | Provide scramble socket vendor qualification data: rated cycle life limit, part number, contact resistance spec; confirm cycle-life assumption (50/100 cycles) is within rated limit | Thu / Component Engineering | Before WW30 HCC | **Yes** |
| 3 | Submit N-1 interposer DFT impact assessment: functional delta vs. COR-8CH native HW, test coverage gap analysis, and confirmation of WW30 demand entry for SMC | Thu / DFT team | Before WW31 PXT Map Day | **Yes** |
| 4 | Confirm HCC readiness gate status: list of all open technical items and their closure plan before WW30 HCC | Program Manager (Thu / Miranda) | WW29–WW30 | No |
| 5 | Close or update DVH validation HW procurement action (open since WW10'26): confirm final procurement path for Thermal Margining tools and Debug HW | Thu | Before validation build start | No |
| 6 | Confirm all teams have entered bare board, test coupon, and N-1 HW demand into the WW30 POB/PO Sample Event | Miranda / Thu | WW30 Sample Event | No |
| 7 | Confirm Maple Stream SharePoint migration plan and communicate new link to all PDLs; ensure COR-8CH SXT documentation is not broken by the migration | Gloria | WW29–WW30 | No |
| 8 | Re-submit for PQRE review after Actions 1–3 are completed and evidence is attached to this issue | ccgglee / PQRE Engineer | After blocking actions closed | **Yes** |

---

### 9. PQRE Recommendation

> **MEDIUM RISK — CONDITIONAL HOLD**
>
> The WW29 COR-8CH SXT meeting minutes identify three active engineering risk areas:
> (1) an open DC-SCM PCB impedance review that is a pre-fabrication SI gate,
> (2) unvalidated scramble socket cycle-life assumptions for ERB builds, and
> (3) confirmed N-1 interposer usage by SMC with no DFT compatibility assessment.
>
> Individually, each domain scores Medium Risk (RPN 21–50). Per escalation rules,
> two or more domains simultaneously at Medium Risk elevates the aggregate to
> **High Risk** pending closure of the blocking actions. The Data Confidence level
> for SI and Mechanical domains is ≤ 2 (Low Confidence), triggering the Low
> Confidence flag per risk scoring criteria.
>
> **PQRE cannot issue a sign-off recommendation** until the following blocking
> actions are confirmed closed:
>
> - **Action 1** — DC-SCM PCB stack-up sent to vendor; impedance review result
>   submitted and reviewed.
> - **Action 2** — Scramble socket vendor qualification data attached, confirming
>   cycle life assumptions are within rated limits.
> - **Action 3** — N-1 interposer DFT compatibility assessment submitted, covering
>   test coverage gap vs. COR-8CH native HW.
>
> With the HCC milestone at WW30 (next week), these items require immediate owner
> attention. Carrying open SI and mechanical engineering gaps past HCC into hardware
> commitment is not recommended.

---

### 8a. Risk Scoring Summary

#### SI — DC-SCM PCB Impedance Review

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 4 | SI non-compliance discovered post-fabrication can require board re-spin, causing schedule delay and cost impact |
| Occurrence | 3 | New PCB supplier engaged; no impedance verification data available yet |
| Detection | 3 | Impedance non-conformance detectable via post-fab coupon test, but not before fabrication commit |
| **RPN** | **36** | **Medium Risk** |
| Data Confidence | 1 | No stack-up document or impedance target values available in this intake |

#### Mechanical — Scramble Socket Lifecycle

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 3 | Contact degradation after cycle limit exceedance causes marginal electrical contact, affecting test reliability |
| Occurrence | 3 | Cycle life assumptions not backed by vendor qualification data; ERB plan assumes 61 boards |
| Detection | 3 | Contact degradation may not be visible; detected via electrical margin or functional test failures |
| **RPN** | **27** | **Medium Risk** |
| Data Confidence | 2 | Informal assumptions present; no vendor datasheet or qualification report attached |

#### DFT/Program — N-1 Interposer Usage

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 3 | N-1 interposer may not support COR-8CH-specific test vectors; reduces validation coverage |
| Occurrence | 3 | CPU unavailability in 1H'27 is confirmed; N-1 HW usage is certain |
| Detection | 3 | Coverage gaps may not surface until silicon validation phase reveals failures on native HW |
| **RPN** | **27** | **Medium Risk** |
| Data Confidence | 2 | Confirmation of N-1 usage is present; no DFT delta analysis or compatibility matrix |

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次 PQRE 審查由 Issue #118 觸發，內容為 **WW29 COR-8CH SXT 計畫會議記錄**，
會議於 2026 年 7 月 16 日（星期四）舉行。Coral SP 平台（8 通道 SXT）目前正處於
積極的量產前開發階段。會議記錄記載了自 WW10'26 起持續追蹤的行動項目清單，以及 WW29
新增的行動項目和計畫下傳事項。

**本次審查識別出三個工程風險領域：**

- **中風險 — SI（訊號完整性）：DC-SCM PCB 疊構阻抗審查：**
  WW29 新增行動項目（負責人：Pedro）要求將 DC-SCM 板的 PCB 疊構發送給 Jack 和
  Mark Chen，請 SMC 轉發給 PCB 廠商進行阻抗審查。本 Issue 中未包含任何疊構文件、
  受控阻抗規格或審查結果。此為板卡製造前 SI 合規性的重要閘門。

- **中風險 — 機械：Scramble Socket 使用壽命與 ERB 建置計畫：**
  會議記錄中列出了 Scramble Socket 的使用循環假設（帶電 50 次、不帶電 100 次）
  及 61 片 ERB 板的計畫數量。但未提供任何正式資格認證報告、供應商規格或循環壽命
  測試數據以佐證上述假設。若超過額定插拔次數，可能導致接點劣化並影響驗證結果的
  可靠性。

- **低–中風險 — DFT/計畫：SMC 於 1H'27 使用 N-1 插座：**
  Thu 確認 SMC 將無法在 1H'27 取得 COR-8CH CPU，因此將使用 N-1 插座。目前未有
  N-1 插座與 COR-8CH SXT 平台之間的 DFT 相容性評估、功能差異分析或測試覆蓋率
  缺口報告。

**整體風險評估：中風險（MEDIUM RISK）。** 無單一領域達 RPN ≥ 51，但多個領域存在
資料信心度 ≤ 2 的未解決證據缺口。依升級規則，兩個以上領域同時處於中風險，即將整體
風險升級為高風險，直至封鎖性行動項目完成。在 SI 疊構阻抗審查、Scramble Socket
資格認證資料及 N-1 插座 DFT 評估提交之前，無法核發 PQRE 簽核建議。

---

### 2. 請求分類（Request Classification）

- **請求型態：** 計畫會議記錄 — 行動項目追蹤器與下傳事項受理
- **平台：** Coral SP COR-8CH SXT（Oak Stream RP SXT 計畫）
- **會議參考：** WW29'2026，2026 年 7 月 16 日星期四 — Microsoft Teams 會議回顧
- **審查領域：** SI（PCB 阻抗）、機械（Scramble Socket）、DFT/計畫（N-1 插座）、
  材料/採購（驗證硬體、熱工具、DIMM 需求）
- **排除領域：** 熱分析、PDN、可靠度應力測試、法規符合性、DFM
  （會議記錄中無熱模擬、電源傳輸、可靠度測試或法規相關內容）
- **風險等級：** 中風險（整體；詳見第 8 節風險評估）
- **是否需要行動：** 是

---

### 3. 是否需要行動（Action Required）

**是。** 須於核發 PQRE 簽核建議前完成三項封鎖性行動（第 8 節行動 1–3）。此外，
尚有數項非封鎖性行動（行動 4–7）需完成以補全資訊。

---

### 4. 已知問題（Known Issues）

1. **DC-SCM PCB 疊構阻抗審查尚待完成：**
   WW29 新增行動項目要求 Pedro 將 DC-SCM 板疊構發送給 Jack 和 Mark Chen，
   請 SMC 轉發給 PCB 廠商進行阻抗審查。本 Issue 中無疊構文件、受控阻抗規格或審查
   結果。廠商及 Intel 雙方均須完成阻抗審查，此為板卡製造前的 SI 合規性閘門。

2. **Scramble Socket 使用循環壽命未正式認證：**
   會議記錄指出帶電使用 50 次、不帶電使用 100 次的假設，以及 ERB 板數量 61 片。
   但未提供正式資格認證報告、供應商額定循環壽命限制或測試數據以驗證上述假設。
   若超出額定次數，可能造成接點可靠度降低，影響驗證結果的有效性。

3. **SMC 1H'27 確認使用 N-1 插座：**
   Thu 確認 SMC 在 1H'27 將無法取得 COR-8CH CPU，因此將使用 N-1 插座。目前
   尚未提供 DFT 相容性矩陣、COR-8CH 與 N-1 的正式差異評估，或測試覆蓋率缺口分析。

4. **多項採購及後勤行動項目自 WW10'26 起持續未結：**
   涵蓋 DVH 驗證硬體訂購/部署、費用分攤不確定性及熱工具採購的多項行動項目自
   WW10'26（約 19 週前）起持續開啟，部分項目仍未有明確結案狀態或目標日期。
   採購延誤可能壓縮驗證建置前的材料可用視窗。

5. **HCC 排定於 WW30，EC 日期待定：**
   HCC（硬體承諾/確認）里程碑即將到來（下週）。工程承諾（EC）日期尚未確定。
   PCB 阻抗和 Socket 工程缺口必須在 HCC 前後解決，以避免攜帶未解決技術風險進入
   硬體承諾。

---

### 5. 未知風險（Unknown Risks）

- **DC-SCM PCB 阻抗審查結果：** 廠商阻抗分析是否會發現疊構不符合規範、受控阻抗層
  偏差或需要修正的線路幾何尺寸，在審查完成前無法得知。

- **Scramble Socket 供應商循環壽命規格：** COR-8CH SXT 所使用的特定 Scramble
  Socket 的實際供應商額定插拔循環限制未記錄在會議記錄中。若供應商限制低於 50/100
  次的假設值，則現有 ERB 建置和驗證計畫可能需要修訂。

- **N-1 插座 DFT 覆蓋率缺口：** COR-8CH 原生硬體與 N-1 插座之間的功能性、SI 及
  DFT 測試覆蓋率差異未知。在 N-1 硬體上進行的矽片驗證可能遺漏 COR-8CH 特有的
  失效模式。

- **SMC N-1 硬體的 MDP 需求：** 是否已有團隊透過 WW30 開啟的 POB/PO 樣品活動正式
  填寫 SMC N-1 硬體需求尚未確認。若錯過需求登錄，可能延遲 SMC 的驗證就緒時程。

- **Maple Stream SharePoint 遷移影響：** Gloria 正在研究將當前 SXT SharePoint
  更改為通用名稱以承載所有平台。在確定之前，工程團隊可能存取過期或錯誤的連結，
  產生文件追溯風險。

---

### 6. 影響評估（Impact Assessment）

| 類別 | 影響 | 嚴重度 |
|------|------|--------|
| SI — DC-SCM PCB 阻抗 | 疊構阻抗尚未驗證；在廠商與 Intel 阻抗審查完成並簽核前，板卡製造無法推進 | **重大** |
| 機械 — Scramble Socket 壽命 | 使用循環假設未有供應商資格認證支撐；ERB/驗證階段存在接點劣化風險 | **中等** |
| DFT/計畫 — N-1 插座使用 | 在 N-1 硬體上進行驗證可能未能覆蓋 COR-8CH 特有失效模式；測試覆蓋率缺口未量化 | **中等** |
| 計畫 — HCC 里程碑就緒度 | WW30 HCC 時仍有 SI 及 Socket 工程缺口開放；EC 日期未定；技術債務攜入硬體承諾的風險 | **重大** |
| 材料 — 採購行動項目（WW10） | 長期未結採購行動（DVH HW、熱工具、費用分攤確認）可能壓縮驗證建置前的材料可用視窗 | **低–中等** |

---

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | 是否封鎖 |
|---|---------|------|---------|
| 1 | DC-SCM PCB 疊構文件及受控阻抗規格；廠商與 Intel 阻抗審查結果 | SI | **是** |
| 2 | Scramble Socket 供應商資格認證資料：額定插拔循環限制、接點電阻規格及 COR-8CH SXT 適用件號 | 機械 | **是** |
| 3 | N-1 插座 DFT 相容性評估：與 COR-8CH 原生硬體的差異分析、測試覆蓋率缺口及 SMC WW30 需求登錄確認 | DFT/計畫 | **是** |
| 4 | HCC 就緒度檢查清單：WW30 HCC 前須關閉的所有技術閘門清單（本審查範圍以外） | 計畫 | 否 |
| 5 | 熱工具採購路徑決策：WW28 PRD 視窗後 Intel 或 SMC 誰負責熱裕量及 Debug 工具採購的確認 | 材料 | 否 |
| 6 | ERB 板建置計畫與 Scramble Socket 循環壽命預算：所有驗證團隊計畫使用的總循環次數與額定限制的比較 | 機械 | 否 |
| 7 | DVH 驗證硬體訂購及部署計畫：Sigmatron（板卡）與獨立採購（熱工具、Debug 工具）的最終決策 | 材料 | 否 |
| 8 | SI 及機械領域的風險評分輸入（S/O/D）及資料信心值，由各負責工程師提供 | SI/機械 | 否 |

---

### 8. 必要行動（Required Actions）

| # | 行動 | 負責人 | 目標日期 | 是否封鎖 |
|---|------|--------|---------|---------|
| 1 | 將 DC-SCM PCB 疊構發送給 Jack 和 Mark Chen；協調 SMC 轉發給 PCB 廠商進行阻抗審查；將審查結果提交至本 PQRE Issue | Pedro / Jack / SMC | WW30 HCC 前 | **是** |
| 2 | 提供 Scramble Socket 供應商資格認證資料：額定循環壽命限制、件號及接點電阻規格；確認循環壽命假設（50/100 次）在額定範圍內 | Thu / 元件工程 | WW30 HCC 前 | **是** |
| 3 | 提交 N-1 插座 DFT 影響評估：與 COR-8CH 原生硬體的功能差異、測試覆蓋率缺口分析，以及 SMC WW30 需求登錄確認 | Thu / DFT 團隊 | WW31 PXT Map Day 前 | **是** |
| 4 | 確認 HCC 就緒度閘門狀態：列出 WW30 HCC 前所有未結技術項目及其關閉計畫 | 計畫經理（Thu / Miranda） | WW29–WW30 | 否 |
| 5 | 結案或更新 DVH 驗證硬體採購行動（自 WW10'26 開啟）：確認熱裕量工具及 Debug HW 的最終採購路徑 | Thu | 驗證建置開始前 | 否 |
| 6 | 確認所有團隊已將裸板、測試耦合板及 N-1 硬體需求登錄至 WW30 POB/PO 樣品活動 | Miranda / Thu | WW30 樣品活動 | 否 |
| 7 | 確認 Maple Stream SharePoint 遷移計畫並通知所有 PDL 新連結；確保 COR-8CH SXT 文件連結不受遷移影響 | Gloria | WW29–WW30 | 否 |
| 8 | 在行動 1–3 完成並將證據附件至本 Issue 後，重新提交 PQRE 審查 | ccgglee / PQRE 工程師 | 封鎖性行動完成後 | **是** |

---

### 9. PQRE 建議（PQRE Recommendation）

> **中風險 — 有條件暫緩（MEDIUM RISK — CONDITIONAL HOLD）**
>
> WW29 COR-8CH SXT 會議記錄識別出三個主動工程風險領域：
> （1）DC-SCM PCB 阻抗審查開放中，為製造前 SI 合規性閘門；
> （2）Scramble Socket 循環壽命假設未經驗證，ERB 建置計畫存在風險；
> （3）SMC 確認使用 N-1 插座，但無 DFT 相容性評估。
>
> 各領域個別評分均為中風險（RPN 21–50）。依升級規則，兩個以上領域同時處於中風險，
> 整體風險升級為**高風險**，直至封鎖性行動完成。SI 及機械領域的資料信心度 ≤ 2，
> 觸發低信心標誌，需提升至工程經理級別進行審查。
>
> **PQRE 無法核發簽核建議**，直至以下封鎖性行動確認完成：
>
> - **行動 1** — DC-SCM PCB 疊構已發送廠商；阻抗審查結果已提交並完成審查。
> - **行動 2** — Scramble Socket 供應商資格認證資料已附件，確認循環壽命假設
>   在額定範圍內。
> - **行動 3** — N-1 插座 DFT 相容性評估已提交，涵蓋與 COR-8CH 原生硬體的
>   測試覆蓋率缺口分析。
>
> 鑑於 HCC 里程碑於 WW30（下週）即將到來，上述項目需要相關負責人立即關注。
> 不建議將開放的 SI 及機械工程缺口攜入硬體承諾。
