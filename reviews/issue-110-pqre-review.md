# PQRE Risk Review — Issue #110

**Issue:** [AI Risk Review] Anderson City 1/2 (Pine Stream COR 20CH)
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/110
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-17
**Requestor:** ccgglee
**Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20CH
**Agent Instruction:** 我要做 Hardware reliability, Regulatory 和 packing drop vibration，所以我該如何回答下面問題 (How should I answer the HSDES HCR form questions for Hardware reliability, Regulatory, and Packaging Drop/Vibration activities?)

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #110 for **Anderson City (ANC) 1S / 2S —
Pine Stream COR 20CH**. The requestor is preparing to submit a Hardware Change
Request (HCR) via the Intel HSDES form and is asking for PQRE-guided answers to
the ten standard HCR intake questions, specifically for the following three
qualification domains:

1. **Hardware Reliability** — HTOL, ELFR, thermal cycling, FIT rate assessment
2. **Regulatory** — RoHS, REACH SVHC, CE/FCC/UL, ECCN
3. **Packaging Drop / Vibration** — Mechanical drop and vibration testing of
   the shipping package

All three domains involve activities that directly affect or validate Platform
Hardware (Anderson City RP, Pine Stream COR 20CH). Section 10 of this review
provides the recommended HCR form answers for each question. Sections 2–9
provide the underlying PQRE risk analysis and engineering rationale.

**Overall risk posture: MEDIUM RISK** — The three domains require formal
qualification activities but are standard, well-defined processes for a
production platform. No blocking technical unknowns exist at this stage; the
primary risk is schedule and data completeness.

---

### 2. Request Classification

- **Request type:** HCR (Hardware Change Request) HSDES intake — qualification
  activity scoping
- **Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20CH
- **Predecessor platform (baseline):** Johnson City (JNC) — DMR AP RP
- **Domains in scope:** Reliability, Regulatory, Mechanical (Packaging)
- **Domains out of scope for this HCR:** Thermal, SI, PDN, Derating, DFM, DFT,
  Material *(qualification activities for these domains are separate HCR items
  or are covered by design collateral reviews)*
- **Risk tier:** Medium Risk
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.** The requestor must submit the HSDES HCR with answers calibrated to the
Hardware Reliability, Regulatory, and Packaging Drop/Vibration scope. The
recommended answers are provided in Section 10. Three parallel action tracks
must also be initiated:

1. **Reliability track** — Confirm design delta vs. JNC1/JNC2 (DMR AP RP);
   determine which JNC reliability data can be re-used and which tests must be
   repeated for ANC Pine Stream COR 20CH.

2. **Regulatory track** — Initiate RoHS/REACH BOM review and CE/FCC/UL
   certification planning for Anderson City.

3. **Packaging track** — Confirm packaging specification and select applicable
   drop/vibration test standard (ISTA 2A, ASTM D4169, or Intel-specific
   specification).

---

### 4. Known Issues

1. **Design delta between JNC (DMR AP RP) and ANC (Pine Stream COR 20CH) is
   not yet documented.** Before JNC1/JNC2 reliability data can be formally
   re-used for ANC qualification, a design delta analysis must be completed
   covering CPU TDP, memory channel count (20CH), board form factor, component
   changes, and thermal cycling amplitude (ΔT).

2. **Regulatory BOM scope is not confirmed.** Any new components added for
   Pine Stream COR 20CH (relative to JNC BOM) that are not already covered by
   an existing RoHS/REACH declaration must be reviewed. ECCN re-classification
   must be checked if any dual-use components are new to the BOM.

3. **Packaging specification for ANC is not confirmed.** The shipping package
   design (carton, cushion material, form fit) for Anderson City may differ
   from JNC. If the package is new or modified, a new drop/vibration test is
   required; JNC packaging test data cannot be directly re-used.

4. **HTOL and thermal cycling test conditions for Pine Stream COR 20CH are not
   yet defined.** Whether the Pine Stream COR junction temperature (Tj) and
   operating power envelope bound or exceed the JNC DMR AP conditions must be
   confirmed before a re-use decision can be made.

---

### 5. Unknown Risks

- **Tj and TDP delta between DMR AP and Pine Stream COR is unknown.** If Pine
  Stream COR operates at higher Tj or higher TDP than DMR AP, additional HTOL
  stress time or new test runs at elevated conditions may be required.

- **Memory subsystem change (20CH) may introduce new reliability stress
  conditions** not covered by JNC qualification data, particularly for board-
  level solder joint thermal cycling and memory interface SI margin.

- **ANC 1S vs. 2S configuration reliability coverage** — If JNC was qualified
  primarily as a 1S platform, the 2S UPI interface and dual-socket power
  delivery reliability coverage may be absent from JNC data.

- **Packaging material changes** — If Anderson City uses a different package
  material (PCB substrate, lid material, solder alloy) from JNC, packaging
  drop test data from JNC may not bound the ANC drop performance.

- **Export classification (ECCN) status of new Pine Stream COR components is
  unknown** — Any new high-performance processing or memory components may
  require ECCN review.

---

### 6. Impact Assessment

| Domain | Impact if Not Executed | Severity |
|--------|------------------------|----------|
| Reliability | Platform cannot achieve production qualification sign-off; field failures and customer complaints without validated reliability data; potential product recall | **High** |
| Regulatory | Product cannot legally be sold in target markets (EU, US, and others); RoHS/CE/FCC non-compliance is a market access showstopper | **Critical** |
| Packaging Drop/Vibration | Increased risk of hardware damage during shipping and handling; elevated DOA (Dead On Arrival) rate at customer site; warranty and logistics cost escalation | **Medium** |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | Design delta document: ANC Pine Stream COR 20CH vs. JNC1/JNC2 DMR AP RP | Reliability | **Yes** |
| 2 | HTOL test plan for ANC — Tj target, voltage stress, duration, sample size | Reliability | **Yes** |
| 3 | Thermal cycling test plan — ΔT range, dwell time, number of cycles for ANC | Reliability | **Yes** |
| 4 | ELFR data plan for new component steppings (if any) in ANC vs. JNC | Reliability | No |
| 5 | Complete ANC BOM with RoHS/REACH compliance declaration for each new part | Regulatory | **Yes** |
| 6 | CE / FCC / UL certification plan and lab selection for ANC | Regulatory | No |
| 7 | ECCN classification review for any new dual-use components in ANC BOM | Regulatory | No |
| 8 | ANC packaging specification (carton, cushion, form fit, gross weight) | Packaging | **Yes** |
| 9 | Applicable drop/vibration test standard and test plan for ANC packaging | Packaging | **Yes** |
| 10 | JNC packaging test report (to assess re-use potential for ANC) | Packaging | No |

---

### 8. Risk Assessment

#### Hardware Reliability Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 4 | Field failures are possible if reliability qualification is skipped; platform production sign-off is blocked |
| Occurrence | 3 | Reliability issues are occasional in RP-to-RP platform transitions; JNC data provides a starting baseline |
| Detection | 2 | HTOL and thermal cycling are standard tests that detect most wearout failure modes reliably |
| **RPN** | **24** | Medium Risk — design delta analysis and qualification plan required |
| Data Confidence | 2 | JNC DMR AP data exists but applicability to Pine Stream COR 20CH is unconfirmed |

> Because Data Confidence = 2 (≤ 2), the **Low Confidence** flag is triggered
> and the domain is treated as **High Risk** pending design delta analysis and
> qualification plan submission.

#### Regulatory Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 5 | Regulatory non-compliance (RoHS/CE/FCC) is a market access blocker; legal and financial exposure |
| Occurrence | 2 | ANC is an evolution of JNC; most components carry over with existing compliance declarations |
| Detection | 1 | RoHS/REACH declarations are reviewed 100% per BOM; CE/FCC certification is mandatory pre-shipment |
| **RPN** | **10** | Low Risk (base calculation) |
| Data Confidence | 3 | JNC compliance data exists; ANC delta BOM review is standard process |

> Although RPN = 10 (Low Risk), Severity = 5 triggers **auto-escalation** per
> Risk Scoring Criteria. The regulatory domain is flagged as requiring formal
> sign-off. Any gap in RoHS/REACH declarations or lapsed CE/FCC certification
> must be resolved before production shipment.

#### Packaging Drop / Vibration Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 3 | Customer DOA rates increase if package does not protect hardware during shipping; functional impact with workaround available |
| Occurrence | 2 | Packaging designs for server platforms are typically mature; minor risk if ANC package is a carryover design |
| Detection | 2 | ISTA/ASTM D4169 drop and vibration tests are standardised and detect most packaging failure modes |
| **RPN** | **12** | Low Risk — standard packaging qualification process applies |
| Data Confidence | 2 | JNC packaging test data may exist but ANC-specific packaging spec is unconfirmed |

> Because Data Confidence = 2 (≤ 2), the **Low Confidence** flag is triggered
> for the Packaging domain pending ANC packaging specification and test plan
> confirmation.

#### Overall Risk Posture

**MEDIUM RISK** — One domain (Reliability) is Medium Risk with Low Confidence.
One domain (Regulatory) has Severity = 5 requiring auto-escalation. Standard
qualification workflows exist for all three domains. **Sign-off is conditional
on submission of the items listed in Section 7.**

---

### 9. PQRE Recommendation

> **CONDITIONAL APPROVE — Subject to Qualification Plan Submission**
>
> Submit the HSDES HCR as guided in Section 10. Initiate the three parallel
> qualification tracks (Reliability, Regulatory, Packaging). The following
> specific actions are required:
>
> **1. Reliability:** Conduct a formal design delta analysis between JNC1/JNC2
> (DMR AP RP) and ANC (Pine Stream COR 20CH). Determine which HTOL, ELFR, and
> thermal cycling test data from JNC is applicable to ANC and what additional
> tests are required. Submit the delta analysis and qualification plan to PQRE
> before starting test execution.
>
> **2. Regulatory:** Perform a BOM delta review. For every new or changed
> component in ANC vs. JNC, obtain and attach an updated RoHS/REACH SVHC
> compliance declaration. Confirm CE/FCC/UL certification status and initiate
> re-certification if any hardware change affects the certified configuration.
> Complete ECCN re-classification check for any new dual-use components.
>
> **3. Packaging Drop/Vibration:** Confirm the ANC shipping package
> specification. If the package is identical to JNC, attach the JNC packaging
> test report and confirm applicability. If the package is new or modified,
> execute a full drop/vibration qualification per ISTA 2A or ASTM D4169 (or
> the applicable Intel packaging specification) and submit the test report to
> PQRE.
>
> **Note on HCR Form:** See Section 10 for the recommended answers to each of
> the ten HSDES HCR intake questions.

---

### 10. HCR Form Answers — Guided Responses

The following provides recommended answers to each question in the HSDES HCR
intake form for the Anderson City 1S/2S (Pine Stream COR 20CH) Hardware
Reliability, Regulatory, and Packaging Drop/Vibration activities.

---

**Q1. Is this a Request affecting Platform Hardware (Including Validation
Hardware)?**

> **Answer: Yes**
>
> Hardware Reliability qualification (HTOL, thermal cycling, ELFR), Regulatory
> compliance verification (RoHS/REACH/CE/FCC/UL), and Packaging Drop/Vibration
> testing are all activities that directly validate, characterise, or certify
> Platform Hardware. All three activities are necessary for production release
> of Anderson City 1S/2S (Pine Stream COR 20CH) as a Platform Hardware RP.

---

**Q2. Is this feature already part of the baseline PRDs, Program LZ or
Platform Architecture Specification?**

> **Answer: Yes**
>
> Hardware reliability qualification, regulatory compliance, and packaging
> mechanical testing are standard qualification requirements mandated in the
> baseline PRD and Platform Architecture Specification for every production-
> targeted Intel server reference platform. For Anderson City / Pine Stream
> COR 20CH, these requirements are inherited from the Johnson City (JNC) —
> DMR AP RP baseline PRDs. Refer to the baseline PRD query on HSDES (leveraged
> from Johnson City) to confirm the specific PRD line items covering reliability
> qualification, regulatory sign-off, and packaging validation.

---

**Q3. Team requesting this feature**

> **Answer example:** DCAI Server Q&R — Platform Quality & Reliability
> Engineering (PQRE) — Boards & Systems Team
>
> *(Adjust to reflect your actual org name and function. Avoid acronyms only;
> provide the full org path and engineering function as instructed by the
> form.)*

---

**Q4. Provide the IDSID of a technical expert from the requesting team**

> **Answer:** Enter your own IDSID, or the IDSID of the designated technical
> expert for the specific domain:
> - Reliability domain: IDSID of the PQRE reliability engineer owning the ANC
>   qualification plan
> - Regulatory domain: IDSID of the regulatory/compliance engineer
> - Packaging domain: IDSID of the packaging / mechanical engineer
>
> If a single owner covers all three domains, one IDSID is sufficient.
> Verify the IDSID at https://workers.intel.com/ before submitting.

---

**Q5. Give a Title to your request**

> **Answer:** Anderson City 1S/2S (Pine Stream COR 20CH) — Hardware
> Reliability, Regulatory Compliance, and Packaging Drop/Vibration
> Qualification Plan

---

**Q6. Describe the Hardware feature you are requesting, its purpose and
usage model**

> **Answer:**
>
> This request covers three mandatory qualification domains for the Anderson
> City (ANC) 1S/2S Reference Platform (Pine Stream COR 20CH):
>
> **1. Hardware Reliability:** Qualification scope includes HTOL (High
> Temperature Operating Life) testing, ELFR (Early Life Failure Rate)
> assessment, board-level solder joint thermal cycling, and FIT rate analysis
> for all new or changed components relative to the predecessor platform
> (Johnson City / DMR AP RP). A design delta analysis between JNC1/JNC2 and
> ANC will determine the extent to which JNC reliability data can be re-used
> vs. requiring new test execution. The purpose is to demonstrate that ANC
> Pine Stream COR 20CH meets Intel server platform reliability targets for the
> expected field operating life.
>
> **2. Regulatory:** Full BOM-level RoHS/REACH SVHC compliance declaration
> review for all components in the ANC BOM delta (new or changed parts relative
> to JNC). CE marking, FCC Part 15 (Class A), and UL certification assessment
> for the ANC RP configuration. ECCN classification confirmation for any new
> high-performance or dual-use components. The purpose is to ensure ANC is
> compliant with all applicable regulations for product sale in EU, US, and
> other target markets.
>
> **3. Packaging Drop/Vibration:** Mechanical qualification of the ANC shipping
> package per ISTA 2A / ASTM D4169 (or the applicable Intel Packaging
> Specification). Test scope includes random vibration (simulation of transport
> over road/rail/air) and shock/drop (1-meter drop height, multiple faces and
> edges, per applicable standard) for both individual carton and palletised
> configurations. The purpose is to demonstrate that the ANC RP hardware
> arrives at the customer site undamaged after normal shipping and handling
> events.
>
> *(If applicable, attach a supporting document — test plan, PRD delta, or
> packaging specification — using the file upload in Q7.)*

---

**Q7. Optional file upload**

> **Answer:** Attach one of the following if available at time of submission:
> - ANC qualification test plan document (PDF or PPT)
> - Design delta document: ANC Pine Stream COR 20CH vs. JNC DMR AP RP
> - ANC shipping package specification sheet
>
> If no document is ready, leave blank and submit supporting collateral as
> a follow-up comment on the HSDES item.

---

**Q8. What would the impact be if the feature were NOT implemented?**

> **Answer:**
>
> - **Reliability (Not implemented):** Anderson City cannot achieve production
>   qualification sign-off. Without validated HTOL, thermal cycling, and ELFR
>   data, there is no engineering evidence that the platform meets field
>   reliability targets. Risk of systematic field failures, customer
>   escalations, and potential product recall.
>
> - **Regulatory (Not implemented):** Anderson City cannot be legally sold in
>   the EU or other regulated markets. RoHS non-compliance and absence of CE/
>   FCC certification are market access blockers. Intel is exposed to legal,
>   financial, and reputational risk.
>
> - **Packaging Drop/Vibration (Not implemented):** Without validated packaging
>   qualification, the risk of hardware damage during shipping and handling is
>   unquantified. Field DOA rates at customer sites may increase, raising
>   warranty costs, logistics expenses, and customer satisfaction risk.

---

**Q9. What would the workaround be if the feature were NOT implemented?**

> **Answer:**
>
> - **Reliability:** A Risk Acceptance waiver signed by the PQRE Manager and
>   Business Owner could be used as a temporary workaround to allow limited
>   pre-production shipments. This is not an acceptable long-term solution for
>   production volume. Alternatively, JNC1/JNC2 data could be referenced
>   provisionally pending formal comparability analysis, but this requires
>   explicit PQRE approval.
>
> - **Regulatory:** **No workaround is possible.** RoHS compliance and
>   CE/FCC/UL certification are legal requirements for market access. Products
>   cannot be shipped to regulated markets without these certifications.
>
> - **Packaging Drop/Vibration:** Enhanced packaging controls (additional
>   cushioning, reduced drop-height handling instructions) and increased DOA
>   monitoring at customer sites could reduce risk. This is a temporary measure
>   only; formal packaging qualification must be completed before volume
>   production shipment.

---

**Q10. Please point to a previous program where this feature was implemented**

> **Answer:** Johnson City (JNC1 / JNC2) — DMR AP Reference Platform
>
> Hardware Reliability qualification (HTOL, ELFR, thermal cycling), Regulatory
> compliance (RoHS/REACH/CE/FCC), and Packaging Drop/Vibration testing were
> all performed for the Johnson City DMR AP RP. The ANC Pine Stream COR 20CH
> RP will leverage JNC as the predecessor baseline, subject to a formal design
> delta analysis and gap-fill plan. Reference the JNC qualification report and
> packaging test report (HSDES items from the JNC program) for design
> collateral.
>
> If specific schematic pages or JNC HSDES item numbers for reliability,
> regulatory, and packaging sign-off are available, include those links in the
> HSDES item for traceability.

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-17.
Closes #110.*

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次審查由 Issue #110 觸發，對象為 **Anderson City (ANC) 1S / 2S —
Pine Stream COR 20CH**。需求方正準備透過 Intel HSDES 表單提交硬體變更請求（HCR），
並請求 PQRE 提供下列三個資格驗證領域的 HCR 十題回答建議：

1. **硬體可靠度（Hardware Reliability）** — HTOL、ELFR、熱循環、FIT 率評估
2. **法規合規（Regulatory）** — RoHS、REACH SVHC、CE/FCC/UL、ECCN
3. **包裝跌落 / 振動測試（Packaging Drop / Vibration）** — 出貨包裝機械測試

上述三個領域均屬於直接影響或驗證平台硬體的活動（Anderson City RP，Pine Stream COR 20CH）。
第 10 節提供每題的建議回答內容；第 2–9 節提供底層 PQRE 風險分析與工程依據。

**整體風險態勢：中等風險（MEDIUM RISK）** — 三個領域均需執行正式資格驗證活動，
但均屬成熟、定義明確的標準流程。目前無阻斷性技術未知項；主要風險為時程與資料完整性。

---

### 2. 請求分類（Request Classification）

- **請求類型：** HCR（硬體變更請求）HSDES 表單收件 — 資格驗證活動範圍定義
- **平台：** Anderson City (ANC) 1S / 2S — Pine Stream COR 20CH
- **前代平台（基線）：** Johnson City (JNC) — DMR AP RP
- **本次 HCR 涵蓋領域：** 可靠度、法規合規、機械（包裝）
- **本次 HCR 不涵蓋領域：** Thermal、SI、PDN、Derating、DFM、DFT、Material
  *（此類領域資格驗證為獨立的 HCR 項目或由設計文件審查涵蓋）*
- **風險等級：** 中等風險
- **需採取行動：** 是

---

### 3. 是否需採取行動（Yes/No）

**是。** 需求方必須提交 HSDES HCR，並依第 10 節的建議回答填寫三個資格驗證領域
的回答內容。同時需啟動三條平行行動軌道：

1. **可靠度軌道** — 確認與 JNC1/JNC2（DMR AP RP）的設計差異分析；
   判斷 JNC 可靠度數據哪些可重用、哪些必須為 ANC Pine Stream COR 20CH 重新執行測試。

2. **法規合規軌道** — 啟動 Anderson City 的 RoHS/REACH BOM 審查
   及 CE/FCC/UL 認證規劃。

3. **包裝軌道** — 確認包裝規格，並選擇適用的跌落 / 振動測試標準
   （ISTA 2A、ASTM D4169 或 Intel 內部包裝規格）。

---

### 4. 已知問題（Known Issues）

1. **JNC（DMR AP RP）與 ANC（Pine Stream COR 20CH）的設計差異尚未文件化。**
   在 JNC1/JNC2 可靠度數據正式重用於 ANC 資格驗證前，必須完成設計差異分析，
   涵蓋 CPU TDP、記憶體通道數（20CH）、板卡外型、元件變更及熱循環幅度（ΔT）。

2. **法規 BOM 範圍尚未確認。** ANC 中相較 JNC BOM 新增的所有元件，
   若尚未取得 RoHS/REACH 合規聲明，均需補充審查。若任何雙重用途新元件加入 BOM，
   需確認 ECCN 重新分類狀態。

3. **ANC 包裝規格尚未確認。** Anderson City 的出貨包裝設計（紙箱、緩衝材料、
   外型配合）可能與 JNC 不同。若包裝為新品或已修改，需執行新的跌落 / 振動測試；
   JNC 包裝測試數據不可直接重用。

4. **Pine Stream COR 20CH 的 HTOL 及熱循環測試條件尚未定義。**
   必須先確認 Pine Stream COR 接面溫度（Tj）及操作功耗包絡是否涵蓋或超過
   JNC DMR AP 條件，才能做出重用決定。

---

### 5. 未知風險（Unknown Risks）

- **DMR AP 與 Pine Stream COR 之間 Tj / TDP 差異未知。** 若 Pine Stream COR
  在更高 Tj 或更高 TDP 下運作，可能需要額外的 HTOL 應力時間或在升高條件下執行新測試。

- **記憶體子系統變更（20CH）可能帶來 JNC 資格驗證數據未涵蓋的新可靠度應力條件，**
  尤其是板級錫球熱循環及記憶體介面 SI 裕度。

- **ANC 1S 與 2S 配置的可靠度涵蓋範圍** — 若 JNC 主要以 1S 進行資格驗證，
  則 2S UPI 介面及雙插槽電源傳輸可靠度涵蓋可能在 JNC 數據中缺失。

- **包裝材料變更** — 若 Anderson City 使用與 JNC 不同的包裝材料
  （PCB 基板、蓋板材料、錫球合金），JNC 的包裝跌落測試數據可能無法保守涵蓋
  ANC 的跌落表現。

- **新 Pine Stream COR 元件的 ECCN 分類狀態未知** — 任何新型高效能處理或記憶體
  元件均可能需要 ECCN 審查。

---

### 6. 影響評估（Impact Assessment）

| 領域 | 未執行的影響 | 嚴重程度 |
|------|-------------|---------|
| 可靠度 | 平台無法完成量產資格驗證簽核；缺乏可靠度數據將導致現場故障、客戶抱怨及潛在召回 | **高** |
| 法規合規 | 產品無法在目標市場（EU、US 等）合法銷售；RoHS/CE/FCC 不合規是市場准入的阻斷項 | **關鍵（Critical）** |
| 包裝跌落 / 振動 | 出貨搬運過程中硬體損壞風險上升；客戶端 DOA（到貨故障）率升高；保固與物流成本增加 | **中** |

---

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | 阻斷性 |
|---|---------|------|--------|
| 1 | 設計差異文件：ANC Pine Stream COR 20CH vs. JNC1/JNC2 DMR AP RP | 可靠度 | **是** |
| 2 | ANC HTOL 測試計畫 — Tj 目標、電壓應力、測試時長、樣品數 | 可靠度 | **是** |
| 3 | 熱循環測試計畫 — ANC 的 ΔT 範圍、保溫時間、循環次數 | 可靠度 | **是** |
| 4 | ANC 相較 JNC 新增元件步進的 ELFR 數據規劃（若適用） | 可靠度 | 否 |
| 5 | ANC 完整 BOM 含每個新增零件的 RoHS/REACH 合規聲明 | 法規 | **是** |
| 6 | ANC 的 CE / FCC / UL 認證計畫及實驗室選擇 | 法規 | 否 |
| 7 | ANC BOM 中任何新型雙重用途元件的 ECCN 分類審查 | 法規 | 否 |
| 8 | ANC 包裝規格（紙箱、緩衝材、外型配合、總重） | 包裝 | **是** |
| 9 | ANC 包裝適用的跌落 / 振動測試標準及測試計畫 | 包裝 | **是** |
| 10 | JNC 包裝測試報告（評估 ANC 重用可能性） | 包裝 | 否 |

---

### 8. 風險評估（Risk Assessment）

#### 硬體可靠度領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 4 | 若跳過可靠度資格驗證，可能發生現場故障；平台量產簽核遭阻斷 |
| Occurrence（發生機率） | 3 | RP 世代交替中偶有可靠度問題；JNC 數據提供起始基線 |
| Detection（可偵測性） | 2 | HTOL 及熱循環為標準測試，可有效偵測大部分磨損失效模式 |
| **RPN** | **24** | 中等風險 — 需提交設計差異分析及資格驗證計畫 |
| 數據信心（Data Confidence） | 2 | JNC DMR AP 數據存在，但對 Pine Stream COR 20CH 的適用性尚未確認 |

> 由於數據信心 = 2（≤ 2），觸發**低信心（Low Confidence）**標誌，
> 在設計差異分析及資格驗證計畫提交前，本領域視為**高風險**。

#### 法規合規領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 5 | 法規不合規（RoHS/CE/FCC）是市場准入阻斷項；存在法律及財務曝險 |
| Occurrence（發生機率） | 2 | ANC 為 JNC 的演進版本；大部分元件沿用現有合規聲明 |
| Detection（可偵測性） | 1 | RoHS/REACH 聲明依 BOM 100% 審查；CE/FCC 認證為出貨前強制項 |
| **RPN** | **10** | 低風險（基礎計算） |
| 數據信心（Data Confidence） | 3 | JNC 合規數據存在；ANC 差異 BOM 審查為標準流程 |

> 儘管 RPN = 10（低風險），Severity = 5 觸發**自動升級（Auto-escalation）**。
> 法規領域被標記為需正式簽核。任何 RoHS/REACH 聲明缺口或 CE/FCC 認證失效，
> 均必須在量產出貨前解決。

#### 包裝跌落 / 振動領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 3 | 若包裝無法保護硬體免於出貨損壞，客戶 DOA 率上升；有功能影響但有替代方案 |
| Occurrence（發生機率） | 2 | 伺服器平台包裝設計通常成熟；若 ANC 包裝為延用設計，風險較低 |
| Detection（可偵測性） | 2 | ISTA/ASTM D4169 跌落及振動測試為標準化流程，可有效偵測大部分包裝失效模式 |
| **RPN** | **12** | 低風險 — 適用標準包裝資格驗證流程 |
| 數據信心（Data Confidence） | 2 | JNC 包裝測試數據可能存在，但 ANC 包裝規格尚未確認 |

> 由於數據信心 = 2（≤ 2），包裝領域觸發**低信心（Low Confidence）**標誌，
> 待 ANC 包裝規格及測試計畫確認後方可解除。

#### 整體風險態勢

**中等風險（MEDIUM RISK）** — 一個領域（可靠度）為中等風險且具低信心標誌。
一個領域（法規合規）Severity = 5，需自動升級。三個領域均有成熟的標準資格驗證
流程可循。**簽核條件取決於第 7 節所列項目的提交。**

---

### 9. PQRE 建議（PQRE Recommendation）

> **有條件核准（CONDITIONAL APPROVE）— 視資格驗證計畫提交情況而定**
>
> 依第 10 節的建議回答提交 HSDES HCR，同時啟動三條平行資格驗證軌道（可靠度、法規、包裝）。
> 必須執行下列具體行動：
>
> **1. 可靠度：** 對 JNC1/JNC2（DMR AP RP）與 ANC（Pine Stream COR 20CH）
> 進行正式設計差異分析。判斷 JNC HTOL、ELFR 及熱循環數據哪些可適用於 ANC，
> 哪些需要補做新測試。在開始測試執行前，先將差異分析報告及資格驗證計畫提交 PQRE 審查。
>
> **2. 法規合規：** 執行 BOM 差異審查。對 ANC 中相較 JNC 每個新增或變更的元件，
> 取得並附上更新後的 RoHS/REACH SVHC 合規聲明。確認 CE/FCC/UL 認證狀態；
> 若任何硬體變更影響已認證配置，啟動重新認證程序。
> 對任何新型雙重用途元件完成 ECCN 重新分類確認。
>
> **3. 包裝跌落 / 振動：** 確認 ANC 出貨包裝規格。若包裝與 JNC 相同，
> 附上 JNC 包裝測試報告並確認適用性。若包裝為新品或已修改，
> 依 ISTA 2A、ASTM D4169 或適用的 Intel 包裝規格執行完整跌落 / 振動資格驗證，
> 並將測試報告提交 PQRE。
>
> **HCR 表單填寫說明：** 請參閱第 10 節，查看十題 HSDES HCR 表單每題的建議回答。

---

### 10. HCR 表單回答建議（HCR Form Answers — Guided Responses）

以下提供 HSDES HCR 表單十道問題的建議回答，適用於 Anderson City 1S/2S
（Pine Stream COR 20CH）硬體可靠度、法規合規及包裝跌落 / 振動資格驗證活動。

---

**第 1 題：這是否為影響平台硬體（包含驗證硬體）的請求？**

> **回答：是（Yes）**
>
> 硬體可靠度資格驗證（HTOL、熱循環、ELFR）、法規合規驗證（RoHS/REACH/CE/FCC/UL），
> 以及包裝跌落 / 振動測試，均屬於直接驗證、表徵或認證平台硬體的活動。
> 上述三項活動均為 Anderson City 1S/2S（Pine Stream COR 20CH）平台硬體 RP
> 量產發布的必要條件。

---

**第 2 題：此功能是否已包含於基線 PRD、Program LZ 或平台架構規格中？**

> **回答：是（Yes）**
>
> 硬體可靠度資格驗證、法規合規及包裝機械測試，均是每個英特爾量產目標
> 伺服器參考平台的 PRD 及平台架構規格中所規定的標準資格驗證需求。
> 對 Anderson City / Pine Stream COR 20CH 而言，上述需求繼承自 Johnson City
>（JNC）— DMR AP RP 基線 PRD。可透過 HSDES 上的基線 PRD 查詢連結（從 Johnson City 繼承）
> 確認涵蓋可靠度資格驗證、法規簽核及包裝驗證的具體 PRD 條目。

---

**第 3 題：提出此功能的團隊**

> **回答範例：** DCAI Server Q&R — Platform Quality & Reliability Engineering
> (PQRE) — Boards & Systems Team（DCAI 伺服器品質與可靠度 — 平台品質可靠度工程
>（PQRE）— 板卡與系統團隊）
>
> *（請依實際組織名稱與職能調整。避免僅填寫縮寫；請依表單指示填寫完整組織路徑
> 及工程職能。）*

---

**第 4 題：提供負責技術專家的 IDSID**

> **回答：** 填入您自己的 IDSID，或各領域指定技術專家的 IDSID：
> - 可靠度領域：負責 ANC 資格驗證計畫的 PQRE 可靠度工程師 IDSID
> - 法規合規領域：法規 / 合規工程師 IDSID
> - 包裝領域：包裝 / 機械工程師 IDSID
>
> 若單一負責人涵蓋三個領域，填一個 IDSID 即可。
> 提交前請至 https://workers.intel.com/ 確認 IDSID 正確性。

---

**第 5 題：請為您的請求命名**

> **回答：** Anderson City 1S/2S (Pine Stream COR 20CH) — 硬體可靠度、
> 法規合規及包裝跌落 / 振動資格驗證計畫
>
> （英文標題：Anderson City 1S/2S (Pine Stream COR 20CH) — Hardware
> Reliability, Regulatory Compliance, and Packaging Drop/Vibration
> Qualification Plan）

---

**第 6 題：說明您請求的硬體功能、用途及使用模式**

> **回答：**
>
> 本請求涵蓋 Anderson City (ANC) 1S/2S 參考平台（Pine Stream COR 20CH）
> 三個必要資格驗證領域：
>
> **1. 硬體可靠度：** 資格驗證範圍包含 HTOL（高溫操作壽命）測試、ELFR
>（早期失效率）評估、板級錫球熱循環，以及相較前代平台（Johnson City / DMR AP RP）
> 所有新增或變更元件的 FIT 率分析。JNC1/JNC2 與 ANC 之間的設計差異分析，
> 將決定 JNC 可靠度數據的重用程度與需補做的新測試範圍。
> 目的在於證明 ANC Pine Stream COR 20CH 在預期現場使用壽命內符合英特爾
> 伺服器平台可靠度目標。
>
> **2. 法規合規：** 對 ANC BOM 差異中所有元件（相較 JNC 新增或變更的零件）
> 進行完整的 BOM 級 RoHS/REACH SVHC 合規聲明審查。評估 ANC RP 配置的
> CE 標誌、FCC Part 15（Class A）及 UL 認證狀態。確認任何新型高效能或
> 雙重用途元件的 ECCN 分類。目的在於確保 ANC 符合所有適用法規，
> 以合法進入 EU、US 及其他目標市場銷售。
>
> **3. 包裝跌落 / 振動：** 依 ISTA 2A / ASTM D4169（或適用的 Intel 包裝規格）
> 對 ANC 出貨包裝進行機械資格驗證。測試範圍包含隨機振動（模擬公路 / 鐵路 / 航空
> 運輸）及衝擊 / 跌落（1 公尺跌落高度，多面 / 邊緣，依適用標準），
> 涵蓋單箱及棧板配置。目的在於證明 ANC RP 硬體在正常出貨與搬運過程後，
> 能完好無損地送達客戶端。
>
> *（若適用，請透過第 7 題的檔案上傳功能附上支援文件，例如測試計畫、PRD 差異文件
> 或包裝規格書。）*

---

**第 7 題：選擇性 — 附上一個提供額外說明的檔案**

> **回答：** 若提交時已有以下文件，請附上其中一份：
> - ANC 資格驗證測試計畫文件（PDF 或 PPT）
> - 設計差異文件：ANC Pine Stream COR 20CH vs. JNC DMR AP RP
> - ANC 出貨包裝規格書
>
> 若文件尚未就緒，可先留空提交，後續在 HSDES 項目的評論中補充相關文件。

---

**第 8 題：若此功能未實施，影響為何？**

> **回答：**
>
> - **可靠度（未實施）：** Anderson City 無法完成量產資格驗證簽核。
>   在缺乏有效 HTOL、熱循環及 ELFR 數據的情況下，無工程依據證明平台符合
>   現場可靠度目標。有系統性現場故障、客戶升級及潛在產品召回的風險。
>
> - **法規合規（未實施）：** Anderson City 無法在 EU 或其他受管制市場合法銷售。
>   RoHS 不合規及缺乏 CE/FCC 認證是市場准入的阻斷項。英特爾面臨法律、財務
>   及聲譽風險。
>
> - **包裝跌落 / 振動（未實施）：** 缺乏包裝資格驗證，出貨及搬運過程中硬體
>   損壞的風險無法量化。客戶端 DOA（到貨故障）率可能上升，保固成本、
>   物流費用及客戶滿意度均受到影響。

---

**第 9 題：若此功能未實施，替代方案為何？**

> **回答：**
>
> - **可靠度：** 可由 PQRE 經理及業務負責人共同簽署風險接受豁免（Risk Acceptance
>   Waiver），作為允許有限量前量產出貨的臨時替代方案。這不是量產的長期可接受解決方案。
>   另一替代做法是在正式可比較性分析待核准的情況下，暫時參照 JNC1/JNC2 數據，
>   但需取得 PQRE 明確批准。
>
> - **法規合規：** **無替代方案。** RoHS 合規及 CE/FCC/UL 認證是進入受管制市場
>   的法律要求，在未取得這些認證的情況下不得出貨至受管制市場。
>
> - **包裝跌落 / 振動：** 可採用強化包裝管控措施（增加緩衝、降低搬運跌落高度
>   指示）並加強客戶端 DOA 率監控以降低風險。這僅為臨時措施；
>   在量產出貨前，必須完成正式包裝資格驗證。

---

**第 10 題：請指出此功能在哪個前代平台中已實施過**

> **回答：** Johnson City（JNC1 / JNC2）— DMR AP 參考平台
>
> 硬體可靠度資格驗證（HTOL、ELFR、熱循環）、法規合規（RoHS/REACH/CE/FCC）
> 及包裝跌落 / 振動測試均在 Johnson City DMR AP RP 中執行過。
> ANC Pine Stream COR 20CH RP 將以 JNC 作為前代基線進行設計差異分析並制定
> 差距補充計畫。請在 HSDES 項目中附上 JNC 資格驗證報告及包裝測試報告
>（JNC 計畫的 HSDES 項目）以利可追溯性。
>
> 若可取得 JNC 可靠度、法規及包裝簽核的特定電路圖頁面或 HSDES 項目編號，
> 請一併附上連結。

---

> ⚠️ **草稿 — 請勿發送** — 任何對外溝通均需經過人工審核核准後方可發送。

---

*由 pqre-risk-review-agent v1.0.0 於 2026-07-17 產生。
關閉 #110。*
