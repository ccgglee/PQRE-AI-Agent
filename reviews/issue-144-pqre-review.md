# PQRE Risk Review — Issue #144

**Issue:** [AI Risk Review] Re: Pine stream COR AP 20CH - Budgetary Demand Collection Kick off meeting
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/144
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-22
**Requestor:** ccgglee
**Platform:** Pine Stream COR AP 20CH (Anderson City ANC 1S / 2S; SabreCity)
**Agent Instruction:** 要挑選哪幾台來做regulatory 才有代表性？ (Which systems should be selected for regulatory testing to be representative?)

---

## English

### 1. Executive Summary

This PQRE review addresses the regulatory representative system selection
question raised during the **Pine Stream COR AP 20CH Budgetary Demand
Collection Kick-off meeting**. The requestor provided a 19-configuration
system list spanning three distinct form-factor families and two platform
families (ANC and SabreCity) and asks which configurations must be
independently submitted for regulatory testing (EMC, Safety, RoHS/REACH,
CE/FCC/UL) to provide full market-access coverage.

**Regulatory representative selection is governed by two principles:**

1. **Worst-case coverage within a form-factor family** — the highest-power,
   highest-emission configuration of a shared enclosure/board family covers
   all lower-power variants of the same family under a single type approval
   ("worst-case EUT" rule per CISPR 32 / FCC Part 15 family testing guidance).

2. **Mandatory unique submission per distinct form factor and per distinct
   platform** — different enclosure designs and different motherboard platforms
   cannot share a single type approval regardless of power level.

Applying these two principles to the 19 configurations listed, the minimum
representative set is **4 systems**, as detailed in Section 5 and 6 below.

**Overall risk posture: MEDIUM RISK** — Regulatory scope is well-defined;
primary risk is schedule and resource planning for 4 independent regulatory
test submissions during budgetary demand collection.

---

### 2. Request Classification

- **Request type:** Regulatory representative system selection — budgetary
  demand collection
- **Platform:** Pine Stream COR AP 20CH — Anderson City (ANC) 1S/2S;
  SabreCity L6
- **Domain in scope:** Regulatory (EMC, Safety, RoHS/REACH, CE/FCC/UL, ECCN)
- **Domains out of scope:** Thermal, SI, PDN, Mechanical, DFM, DFT, Material,
  Reliability *(covered by separate PQRE reviews)*
- **Risk tier:** Medium Risk
- **Action Required:** Yes

---

### 3. Action Required

**Yes.** The following actions are required:

1. **Confirm the regulatory testing budget** for 4 independent type-approval
   submissions (POK ANC, SabreCity POK, 3U Closed ANC, 5U Closed ANC) based
   on the representative system selection in Section 5.

2. **Confirm whether E1 silicon reaches market.** If E1-based configurations
   are not shipped to end customers, E1 silicon need not be separately
   certified; the E3 production-stepping certification covers the product.
   If E1 is shipped, a separate certification assessment is required.

3. **Engage OxM regulatory team** to initiate regulatory test planning for
   each of the 4 representative systems, per SOW Section 4 ownership
   (OxM executes; Intel reviews and approves).

4. **Confirm 1SPC vs 2SPC production intent.** If 1SPC configurations are
   production SKUs distinct from 2SPC, the regulatory family approval must
   explicitly list both as EUT variants under the 2SPC worst-case test. This
   is acceptable under family testing guidelines provided the only difference
   is socket population.

---

### 4. Selection Logic — Worst-Case EUT Principles

For EMC type approval (FCC Part 15 Class A, CISPR 32, EN 55032), the
regulatory standard allows a single Equipment Under Test (EUT) to represent
a product family when the following conditions are met:

| Condition | Requirement |
|-----------|-------------|
| Same motherboard / board layout | All variants in the family share the same PCB |
| Same enclosure / shielding class | Enclosure geometry and shielding effectiveness are identical or the EUT is the worst-case configuration |
| Highest power configuration tested | The tested EUT operates at the highest power level within the family |
| All I/O ports represented | All port types present on any family member are represented on the EUT |

**Worst-case ranking for emissions (highest → lowest risk):**

| Parameter | Higher Risk | Lower Risk |
|-----------|-------------|------------|
| Socket count | 2SPC (two CPUs, more memory, higher power) | 1SPC |
| TDP variant | H-TDP (higher processor power) | Standard TDP |
| CPU stepping | E3 (production silicon, highest bin) | E1 (early sample, lower freq) |
| System openness | Closed enclosure (conducted/radiated profile differs from open POK) | POK (no shielding) |

**Conclusion:** Within each form-factor family, the configuration
**2SPC + H-TDP + E3** is the worst-case EUT and covers all other variants
of the same mechanical family.

---

### 5. System Classification and Representative Selection

#### 5.1 Full Configuration List with Classification

| # | System Type | Config | System Description | Form Factor | Platform | SPC | CPU | TDP | Worst Case? |
|---|-------------|--------|--------------------|-------------|----------|-----|-----|-----|-------------|
| 1 | POK System | 1SPC | ANC 1SPC POK System | Open / POK | ANC | 1 | — | Std | No |
| **2** | **POK System** | **2SPC** | **ANC 2SPC POK System** | **Open / POK** | **ANC** | **2** | **—** | **Std** | **YES — Worst-case ANC POK** |
| 3 | POK System | 1SPC | SabreCity Power on Kit (POK) L6 | Open / POK | Sabre | 1 | — | Std | Separate platform |
| 4 | Closed 3U | 1SPC | ANC 1SPC, E1, 3U Closed System (BIK) | 3U Closed | ANC | 1 | E1 | Std | No |
| 5 | Closed 3U | 1SPC | ANC 1SPC, E1, 3U Closed System H-TDP (BIK) | 3U Closed | ANC | 1 | E1 | H-TDP | No |
| 6 | Closed 3U | 2SPC | ANC 2SPC, E1, 3U Closed System (BIK) | 3U Closed | ANC | 2 | E1 | Std | No |
| 7 | Closed 3U | 2SPC | ANC 2SPC, E1, 3U Closed System H-TDP (BIK) | 3U Closed | ANC | 2 | E1 | H-TDP | No |
| 8 | Closed 3U | 1SPC | ANC 1SPC, E3, 3U Closed System (BIK) | 3U Closed | ANC | 1 | E3 | Std | No |
| 9 | Closed 3U | 1SPC | ANC 1SPC, E3, 3U Closed System H-TDP (BIK) | 3U Closed | ANC | 1 | E3 | H-TDP | No |
| 10 | Closed 3U | 2SPC | ANC 2SPC, E3, 3U Closed System (BIK) | 3U Closed | ANC | 2 | E3 | Std | No |
| **11** | **Closed 3U** | **2SPC** | **ANC 2SPC, E3, 3U Closed System H-TDP (BIK)** | **3U Closed** | **ANC** | **2** | **E3** | **H-TDP** | **YES — Worst-case 3U** |
| 12 | Closed 5U | 1SPC | ANC 1SPC, E1 5U Closed System | 5U Closed | ANC | 1 | E1 | Std | No |
| 13 | Closed 5U | 1SPC | ANC 1SPC, E1 5U Closed System H-TDP | 5U Closed | ANC | 1 | E1 | H-TDP | No |
| 14 | Closed 5U | 2SPC | ANC 2SPC, E1 5U Closed System | 5U Closed | ANC | 2 | E1 | Std | No |
| 15 | Closed 5U | 2SPC | ANC 2SPC, E1 5U Closed System H-TDP | 5U Closed | ANC | 2 | E1 | H-TDP | No |
| 16 | Closed 5U | 1SPC | ANC 1SPC, E3 5U Closed System | 5U Closed | ANC | 1 | E3 | Std | No |
| 17 | Closed 5U | 1SPC | ANC 1SPC, E3 5U Closed System H-TDP | 5U Closed | ANC | 1 | E3 | H-TDP | No |
| 18 | Closed 5U | 2SPC | ANC 2SPC, E3 5U Closed System | 5U Closed | ANC | 2 | E3 | Std | No |
| **19** | **Closed 5U** | **2SPC** | **ANC 2SPC, E3 5U Closed System H-TDP** | **5U Closed** | **ANC** | **2** | **E3** | **H-TDP** | **YES — Worst-case 5U** |

> **SabreCity POK (#3):** SabreCity and Anderson City are distinct platforms
> with separate motherboard designs. Even though both use the Pine Stream
> COR AP 20CH CPU, the board layout, clock topology, and I/O integration
> differ. A separate regulatory submission is required.

---

### 6. Recommended Representative System Set (Minimum 4)

| Priority | System | Rationale |
|----------|---------|-----------|
| **1** | ANC 2SPC POK System | Worst-case open platform for ANC. No enclosure shielding; 2SPC is highest emission risk for POK family. Covers ANC 1SPC POK. |
| **2** | SabreCity Power on Kit (POK) L6 | Independent platform (different motherboard from ANC). Cannot be covered by ANC POK approval. Mandatory separate submission. |
| **3** | ANC 2SPC, E3, 3U Closed System H-TDP (BIK) | Worst-case closed 3U. Covers all 3U variants (#4–#11): 1SPC, 2SPC, E1, E3, Std TDP, H-TDP. |
| **4** | ANC 2SPC, E3 5U Closed System H-TDP | Worst-case closed 5U. Covers all 5U variants (#12–#19): 1SPC, 2SPC, E1, E3, Std TDP, H-TDP. |

**Coverage summary:**

| Form Factor | Test Unit | Systems Covered |
|-------------|-----------|-----------------|
| ANC POK (open) | ANC 2SPC POK | #1, #2 |
| SabreCity POK | SabreCity L6 | #3 |
| 3U Closed (ANC) | ANC 2SPC E3 3U H-TDP | #4, #5, #6, #7, #8, #9, #10, #11 |
| 5U Closed (ANC) | ANC 2SPC E3 5U H-TDP | #12, #13, #14, #15, #16, #17, #18, #19 |

**Total: 4 regulatory submissions cover all 19 configurations.**

---

### 7. Known Issues

1. **[ASSUMPTION] E3 covers E1 emissions.** This assumes E3 produces equal or
   higher emissions than E1 across all frequency bands. If E1 operates at a
   unique clock frequency or power mode absent in E3 that generates a
   distinct emissions peak, a separate E1 scan would be required. Confirm
   with platform BIOS and CPU power management team.

2. **[EVIDENCE NOT FOUND] SabreCity POK L6 board design delta vs. ANC.**
   The regulatory submission boundary between SabreCity and ANC POK requires
   a board-level I/O and clock topology comparison to confirm they cannot
   share a family approval. This analysis has not been submitted to PQRE.

3. **[EVIDENCE NOT FOUND] 3U vs 5U shielding equivalence.** The 3U and 5U
   enclosures have different dimensions and potentially different shielding
   effectiveness. No aperture/shielding analysis has been submitted to confirm
   whether they could be treated as one family. Separate submissions are
   required until equivalence is demonstrated.

4. **[ASSUMPTION] 1SPC is covered under 2SPC family approval.** This is
   standard practice under FCC Part 15 family testing when the only hardware
   difference is socket population (one CPU absent). Confirm with Intel
   regulatory team that the FCC/CE family filing can list both 1SPC and 2SPC
   as product variants under the 2SPC worst-case EUT.

---

### 8. Gap Analysis

| Domain | Current Gap | Evidence Missing | Impact |
|--------|-------------|-----------------|--------|
| EMC (FCC/CE) | Worst-case EUT selection not formally documented | EMC pre-compliance scan data for 2SPC H-TDP configurations | High |
| Safety (UL/IEC 62368) | Safety scope for 3U vs 5U not confirmed | Input power, creepage/clearance, fusing specifications for each enclosure | Medium |
| RoHS / REACH | BOM coverage scope not confirmed for new E3 stepping | Material declaration for E3 CPU and any new BOM components | High |
| Regulatory family filing | 1SPC/2SPC variant listing in FCC/CE approval not confirmed | Regulatory engineer confirmation of family filing strategy | Medium |
| SabreCity delta | Board-level I/O / clock topology comparison with ANC not available | PCB schematic / block diagram comparison | Medium |

---

### 9. Risk Assessment

| Risk | Severity | Occurrence | Detection | RPN | Band |
|------|----------|------------|-----------|-----|------|
| Missing regulatory submission for a form factor (market access blocker) | 9 | 3 | 3 | 81 | **HIGH** |
| E1 silicon unique emissions not covered by E3 certification | 6 | 2 | 4 | 48 | Medium |
| SabreCity incorrectly included under ANC family approval | 7 | 2 | 3 | 42 | Medium |
| 1SPC variant not listed in 2SPC family filing | 5 | 3 | 3 | 45 | Medium |
| Schedule overrun due to 4 parallel regulatory submissions | 5 | 4 | 2 | 40 | Medium |

> **Auto-escalation note:** Any item with Severity ≥ 7 (market-access risk)
> is escalated regardless of RPN. Item 1 (missing submission) and Item 3
> (SabreCity mis-classification) are escalated.

---

### 10. Recommendation

> **CONDITIONAL APPROVE — Proceed to budgetary demand planning with 4
> regulatory submissions; resolve open items in Section 7 before final
> regulatory test plan submission.**

**Minimum representative test set for regulatory (4 systems):**

1. **ANC 2SPC POK System**
2. **SabreCity Power on Kit (POK) L6**
3. **ANC 2SPC, E3, 3U Closed System H-TDP (BIK)**
4. **ANC 2SPC, E3 5U Closed System H-TDP**

These 4 configurations provide full worst-case coverage for all 19 listed
systems across all distinct form-factor families and platform families.

Open items that must be resolved before final regulatory test plan submission:

- [ ] Confirm E3 emissions worst-case vs. E1 with platform BIOS/CPU team
- [ ] Confirm SabreCity board-level delta vs. ANC with platform design team
- [ ] Confirm 1SPC/2SPC family filing strategy with Intel regulatory engineer
- [ ] Confirm Safety scope (3U vs 5U) with safety test lab

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-22.
Issue: https://github.com/ccgglee/PQRE-AI-Agent/issues/144*

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本 PQRE 審查針對 **Pine Stream COR AP 20CH 預算需求收集啟動會議** 中提出的法規代表性系統選擇問題進行回應。需求方提供了一份涵蓋三種不同尺寸規格系列及兩個平台系列（ANC 與 SabreCity）的 19 種配置系統清單，並詢問哪些配置必須各自獨立送測，以確保法規測試（EMC、安全、RoHS/REACH、CE/FCC/UL）的完整市場准入覆蓋。

**法規代表性系統選擇遵循兩大原則：**

1. **同一尺寸規格系列內選最差情境** — 同一機箱/主板系列中，功耗最高、輻射最強的配置，可在單一型式認可（Type Approval）下涵蓋同系列所有低功耗變體（依據 CISPR 32 / FCC Part 15 系列測試指引之「最差 EUT」原則）。

2. **不同尺寸規格及不同平台須各自獨立送測** — 不同機箱設計及不同主板平台，無論功耗高低，均不得共用單一型式認可。

將上述兩項原則套用至 19 種配置後，最低代表性測試組合為 **4 台系統**，詳見第 5 節及第 6 節。

**整體風險評級：中等風險** — 法規範疇明確；主要風險在於預算需求收集階段 4 件獨立法規送測的時程與資源規劃。

---

### 2. 需求分類

- **需求類型：** 法規代表性系統選擇 — 預算需求收集
- **平台：** Pine Stream COR AP 20CH — Anderson City (ANC) 1S/2S；SabreCity L6
- **審查範疇：** 法規（EMC、安全、RoHS/REACH、CE/FCC/UL、ECCN）
- **排除範疇：** 熱學、SI、PDN、機械、DFM、DFT、材料、可靠度（另以獨立 PQRE 審查涵蓋）
- **風險等級：** 中等風險
- **是否需要行動：** 是

---

### 3. 需要採取的行動

**是。** 需採取以下行動：

1. **確認 4 件型式認可送測的法規測試預算**（ANC POK、SabreCity POK、3U Closed ANC、5U Closed ANC），依第 5 節的代表性系統選擇結果編列。

2. **確認 E1 矽晶是否上市出貨。** 若 E1 配置不出貨給最終客戶，E1 矽晶不需獨立取得認證；E3 量產矽晶認證即可涵蓋整個產品系列。若 E1 需出貨，則須另行進行認證評估。

3. **知會 OxM 法規團隊**，針對 4 台代表性系統啟動法規測試規劃，依 SOW 第 4 節的責任歸屬（OxM 執行；Intel 審查並核准）。

4. **確認 1SPC 與 2SPC 量產意圖。** 若 1SPC 配置為獨立量產 SKU，法規系列認可文件必須明確將兩者均列為 2SPC 最差情境測試下的 EUT 變體。依系列測試指引，若唯一差異為插槽填裝數，此做法為可接受的處理方式。

---

### 4. 選擇邏輯 — 最差情境 EUT 原則

針對 EMC 型式認可（FCC Part 15 Class A、CISPR 32、EN 55032），法規標準允許單一受測設備（EUT）代表一個產品系列，條件如下：

| 條件 | 要求 |
|------|------|
| 相同主板／板端佈局 | 系列內所有變體共用同一 PCB |
| 相同機箱／遮蔽等級 | 機箱幾何尺寸及屏蔽效能相同，或 EUT 為最差情境配置 |
| 測試配置為最高功耗 | 受測 EUT 以系列中最高功耗條件運行 |
| 涵蓋所有 I/O 連接埠 | 系列中任一成員具備的所有連接埠類型，均需在 EUT 上呈現 |

**輻射發射最差情境排名（由高至低風險）：**

| 參數 | 較高風險 | 較低風險 |
|------|----------|----------|
| 插槽數 | 2SPC（雙 CPU、更多記憶體、更高功耗） | 1SPC |
| TDP 變體 | H-TDP（較高處理器功耗） | 標準 TDP |
| CPU 步進 | E3（量產矽晶，最高 bin） | E1（工程樣品，較低頻率） |
| 系統開放性 | 封閉機箱（傳導/輻射特性與開放式 POK 不同） | POK（無遮蔽） |

**結論：** 在每個尺寸規格系列內，**2SPC + H-TDP + E3** 為最差情境 EUT，可涵蓋同一機械系列的所有其他變體。

---

### 5. 系統分類與代表性選擇

#### 5.1 完整配置清單與分類

| # | 系統類型 | 配置 | 系統描述 | 尺寸規格 | 平台 | SPC | CPU | TDP | 最差情境？ |
|---|----------|------|----------|----------|------|-----|-----|-----|-----------|
| 1 | POK 系統 | 1SPC | ANC 1SPC POK System | 開放式/POK | ANC | 1 | — | 標準 | 否 |
| **2** | **POK 系統** | **2SPC** | **ANC 2SPC POK System** | **開放式/POK** | **ANC** | **2** | **—** | **標準** | **是 — ANC POK 最差情境** |
| 3 | POK 系統 | 1SPC | SabreCity Power on Kit (POK) L6 | 開放式/POK | Sabre | 1 | — | 標準 | 獨立平台 |
| 4 | 封閉 3U | 1SPC | ANC 1SPC, E1, 3U 封閉系統 (BIK) | 3U 封閉 | ANC | 1 | E1 | 標準 | 否 |
| 5 | 封閉 3U | 1SPC | ANC 1SPC, E1, 3U 封閉系統 H-TDP (BIK) | 3U 封閉 | ANC | 1 | E1 | H-TDP | 否 |
| 6 | 封閉 3U | 2SPC | ANC 2SPC, E1, 3U 封閉系統 (BIK) | 3U 封閉 | ANC | 2 | E1 | 標準 | 否 |
| 7 | 封閉 3U | 2SPC | ANC 2SPC, E1, 3U 封閉系統 H-TDP (BIK) | 3U 封閉 | ANC | 2 | E1 | H-TDP | 否 |
| 8 | 封閉 3U | 1SPC | ANC 1SPC, E3, 3U 封閉系統 (BIK) | 3U 封閉 | ANC | 1 | E3 | 標準 | 否 |
| 9 | 封閉 3U | 1SPC | ANC 1SPC, E3, 3U 封閉系統 H-TDP (BIK) | 3U 封閉 | ANC | 1 | E3 | H-TDP | 否 |
| 10 | 封閉 3U | 2SPC | ANC 2SPC, E3, 3U 封閉系統 (BIK) | 3U 封閉 | ANC | 2 | E3 | 標準 | 否 |
| **11** | **封閉 3U** | **2SPC** | **ANC 2SPC, E3, 3U 封閉系統 H-TDP (BIK)** | **3U 封閉** | **ANC** | **2** | **E3** | **H-TDP** | **是 — 3U 最差情境** |
| 12 | 封閉 5U | 1SPC | ANC 1SPC, E1 5U 封閉系統 | 5U 封閉 | ANC | 1 | E1 | 標準 | 否 |
| 13 | 封閉 5U | 1SPC | ANC 1SPC, E1 5U 封閉系統 H-TDP | 5U 封閉 | ANC | 1 | E1 | H-TDP | 否 |
| 14 | 封閉 5U | 2SPC | ANC 2SPC, E1 5U 封閉系統 | 5U 封閉 | ANC | 2 | E1 | 標準 | 否 |
| 15 | 封閉 5U | 2SPC | ANC 2SPC, E1 5U 封閉系統 H-TDP | 5U 封閉 | ANC | 2 | E1 | H-TDP | 否 |
| 16 | 封閉 5U | 1SPC | ANC 1SPC, E3 5U 封閉系統 | 5U 封閉 | ANC | 1 | E3 | 標準 | 否 |
| 17 | 封閉 5U | 1SPC | ANC 1SPC, E3 5U 封閉系統 H-TDP | 5U 封閉 | ANC | 1 | E3 | H-TDP | 否 |
| 18 | 封閉 5U | 2SPC | ANC 2SPC, E3 5U 封閉系統 | 5U 封閉 | ANC | 2 | E3 | 標準 | 否 |
| **19** | **封閉 5U** | **2SPC** | **ANC 2SPC, E3 5U 封閉系統 H-TDP** | **5U 封閉** | **ANC** | **2** | **E3** | **H-TDP** | **是 — 5U 最差情境** |

> **SabreCity POK（#3）：** SabreCity 與 Anderson City 為獨立平台，採用不同主板設計。即便兩者均使用 Pine Stream COR AP 20CH CPU，板端佈局、時脈拓樸及 I/O 整合方式不同，須個別提交法規申請。

---

### 6. 建議代表性系統組合（最低 4 台）

| 優先順序 | 系統 | 選擇理由 |
|----------|------|----------|
| **1** | ANC 2SPC POK System | ANC 開放式平台最差情境。無機箱遮蔽；2SPC 為 POK 系列最高輻射風險配置。可涵蓋 ANC 1SPC POK。 |
| **2** | SabreCity Power on Kit (POK) L6 | 獨立平台（主板設計不同於 ANC）。無法由 ANC POK 認可涵蓋，必須獨立申請。 |
| **3** | ANC 2SPC, E3, 3U 封閉系統 H-TDP (BIK) | 3U 封閉式最差情境。可涵蓋所有 3U 變體（#4–#11）：1SPC、2SPC、E1、E3、標準 TDP、H-TDP。 |
| **4** | ANC 2SPC, E3 5U 封閉系統 H-TDP | 5U 封閉式最差情境。可涵蓋所有 5U 變體（#12–#19）：1SPC、2SPC、E1、E3、標準 TDP、H-TDP。 |

**涵蓋範圍摘要：**

| 尺寸規格 | 測試機台 | 涵蓋系統編號 |
|----------|----------|------------|
| ANC POK（開放式） | ANC 2SPC POK | #1、#2 |
| SabreCity POK | SabreCity L6 | #3 |
| 3U 封閉式（ANC） | ANC 2SPC E3 3U H-TDP | #4、#5、#6、#7、#8、#9、#10、#11 |
| 5U 封閉式（ANC） | ANC 2SPC E3 5U H-TDP | #12、#13、#14、#15、#16、#17、#18、#19 |

**總結：4 件法規送測可涵蓋全部 19 種配置。**

---

### 7. 已知問題

1. **【假設】E3 涵蓋 E1 輻射發射。** 此假設前提為 E3 在所有頻率段的輻射發射量等於或高於 E1。若 E1 在 E3 不存在的特定時脈頻率或電源模式下產生獨特的輻射峰值，則需另行掃描 E1。請與平台 BIOS 及 CPU 電源管理團隊確認。

2. **【未找到佐證資料】SabreCity POK L6 主板與 ANC 設計差異分析。** SabreCity 與 ANC POK 之間的法規送測邊界，需進行板端 I/O 及時脈拓樸比對，以確認兩者不能共用系列認可。此分析尚未提交至 PQRE。

3. **【未找到佐證資料】3U 與 5U 屏蔽等效性。** 3U 與 5U 機箱尺寸不同，屏蔽效能可能有差異。尚無開孔／屏蔽分析提交以確認兩者是否可視為同一系列。在等效性獲得確認前，需各自獨立送測。

4. **【假設】1SPC 可納入 2SPC 系列認可。** 在 FCC Part 15 系列測試中，若硬體差異僅為插槽填裝數（缺少一顆 CPU），此為標準慣例。請與 Intel 法規工程師確認 FCC/CE 系列申請文件可將 1SPC 與 2SPC 均列為 2SPC 最差情境 EUT 下的產品變體。

---

### 8. 差距分析

| 領域 | 現有差距 | 缺少的佐證資料 | 影響 |
|------|----------|--------------|------|
| EMC（FCC/CE） | 最差情境 EUT 選擇尚未正式記錄 | 2SPC H-TDP 配置的 EMC 預合規掃描資料 | 高 |
| 安全（UL/IEC 62368） | 3U 與 5U 的安全範疇尚未確認 | 各機箱的輸入功率、爬電距離/電氣間隙、保險絲規格 | 中 |
| RoHS / REACH | E3 步進新組件的 BOM 涵蓋範圍尚未確認 | E3 CPU 及所有新 BOM 組件的材料聲明書 | 高 |
| 法規系列申請 | 1SPC/2SPC 變體列入 FCC/CE 核准文件的方式尚未確認 | 法規工程師對系列申請策略的確認 | 中 |
| SabreCity 差異分析 | 與 ANC 的板端 I/O／時脈拓樸比對尚未完成 | PCB 原理圖／方塊圖比對 | 中 |

---

### 9. 風險評估

| 風險 | 嚴重度 | 發生率 | 偵測度 | RPN | 風險等級 |
|------|--------|--------|--------|-----|----------|
| 缺少某尺寸規格的法規送測（市場准入阻斷） | 9 | 3 | 3 | 81 | **高風險** |
| E1 矽晶獨特輻射發射未被 E3 認證涵蓋 | 6 | 2 | 4 | 48 | 中等風險 |
| SabreCity 被錯誤納入 ANC 系列認可 | 7 | 2 | 3 | 42 | 中等風險 |
| 1SPC 變體未列入 2SPC 系列申請 | 5 | 3 | 3 | 45 | 中等風險 |
| 4 件平行法規送測導致時程延遲 | 5 | 4 | 2 | 40 | 中等風險 |

> **自動升級注意事項：** 嚴重度 ≥ 7（市場准入風險）的項目無論 RPN 多少均需升級處理。項目 1（缺少送測）及項目 3（SabreCity 誤分類）需升級處理。

---

### 10. PQRE 建議

> **附條件核准（CONDITIONAL APPROVE）— 以 4 件法規送測進行預算需求規劃；在最終法規測試計畫提交前，解決第 7 節列出的未決項目。**

**最低代表性法規測試組合（4 台系統）：**

1. **ANC 2SPC POK System**
2. **SabreCity Power on Kit (POK) L6**
3. **ANC 2SPC, E3, 3U 封閉系統 H-TDP (BIK)**
4. **ANC 2SPC, E3 5U 封閉系統 H-TDP**

以上 4 種配置，針對所有獨立尺寸規格系列及平台系列，提供 19 種列出系統的完整最差情境涵蓋。

最終法規測試計畫提交前須解決的未決項目：

- [ ] 與平台 BIOS/CPU 團隊確認 E3 輻射發射最差情境是否涵蓋 E1
- [ ] 與平台設計團隊確認 SabreCity 主板與 ANC 的板端差異
- [ ] 與 Intel 法規工程師確認 1SPC/2SPC 系列申請策略
- [ ] 與安全測試實驗室確認 3U 與 5U 的安全範疇

---

> ⚠️ **草稿 — 請勿發送** — 任何外部通訊均須在獲得人工審核批准後方可發出。

---

*由 pqre-risk-review-agent v1.0.0 於 2026-07-22 生成。
Issue: https://github.com/ccgglee/PQRE-AI-Agent/issues/144*
