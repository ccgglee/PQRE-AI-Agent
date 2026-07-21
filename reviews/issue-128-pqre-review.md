# PQRE Risk Review — Issue #128

**Issue:** [AI Risk Review] Re: Add PQRE SOW regulatory ownership review for Pine Stream COR AP 20CH
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/128
**Related PR:** https://github.com/ccgglee/PQRE-AI-Agent/pull/127
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-21
**Requestor:** ccgglee
**Platform:** Pine Stream COR AP 20CH (Anderson City ANC 1S / 2S)
**Agent Instruction:** The SOW Section 4 clearly states that OxM is responsible for regulatory execution. A prior AI response incorrectly indicated there was no obvious person in charge ("沒有明顯安排負責人"). This review corrects that error and provides a full PQRE SOW regulatory ownership analysis.

---

## ⚠️ Correction Notice

A prior AI response on this platform incorrectly stated that there was **no obvious
responsible party** ("沒有明顯安排負責人") for the regulatory work on Pine Stream COR
AP 20CH. This is **factually incorrect** and contradicts the contractual SOW language.

**SOW Section 4.1 — Regulatory Program Management** explicitly and unambiguously
designates **OxM (Original x Manufacturer)** as the primary owner of all regulatory
execution activities. Intel's role is review, approval, and sign-off — not primary
execution. See Section 2 and Section 8 of this review for the corrected ownership
matrix derived directly from the SOW.

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #128, which challenges a prior incorrect AI
determination regarding regulatory ownership for **Pine Stream COR AP 20CH** (Anderson
City ANC 1S / 2S). The prior response stated "no obvious person in charge" for the
regulatory domain. This conclusion is **incorrect**: the contractual Statement of Work
(SOW) **Section 4 — Regulatory and Ecology** contains explicit language assigning
**OxM** as the primary responsible party for all regulatory program management,
execution planning, EMC testing, and compliance data delivery.

This review:
1. Corrects the ownership determination based on SOW contractual language.
2. Documents the full SOW-defined regulatory requirements and test obligations.
3. Provides a PQRE risk assessment for the regulatory domain.
4. Establishes the correct ownership matrix for all regulatory activities.

**Overall risk posture: MEDIUM RISK** — The regulatory domain has Severity = 5
(regulatory non-compliance is a market-access blocker), which triggers
auto-escalation regardless of base RPN. Ownership is **clearly assigned to OxM**
per the SOW. The risk lies in verifying that OxM has an active execution plan and
that deliverables are on schedule for Intel's required approval milestones.

---

### 2. Request Classification

- **Request type:** SOW Regulatory Ownership Clarification / Correction of Prior AI Error
- **Platform:** Pine Stream COR AP 20CH (Anderson City ANC 1S / 2S)
- **SOW reference:** Section 4 — Regulatory and Ecology; Section 4.1 — Regulatory
  Program Management
- **Domain in scope:** Regulatory (EMC, RoHS, CE/FCC/UL, ECCN)
- **Domains out of scope for this review:** Thermal, SI, PDN, Mechanical, DFM, DFT,
  Material, Reliability *(covered by separate PQRE reviews)*
- **Risk tier:** Medium Risk (Severity = 5 auto-escalation applies)
- **Action Required:** Yes

---

### 3. Action Required (Yes/No)

**Yes.** The following actions are required:

1. **Correct the record:** The prior PQRE AI response that stated "no obvious
   responsible party" for regulatory work must be formally corrected. The SOW
   contractual language unambiguously assigns OxM as the responsible party.

2. **OxM Execution Plan:** Confirm that OxM has submitted or is preparing a
   detailed product regulatory execution plan and schedule per SOW Section 4.1,
   covering all EMC, RoHS, CE, FCC, and other applicable certification activities.

3. **Intel Review Gate:** Intel Regulatory and Ecology engineers must be engaged
   to review OxM's execution plan at each approval milestone per SOW Section 4.1.

4. **EMC Test Track:** Verify that OxM has engaged an accredited test laboratory
   for the EMC measurements listed in the SOW and that preliminary test results
   or engineering compliance assessments are on schedule.

---

### 4. Known Issues

1. **Prior AI response incorrectly stated no ownership was assigned.** SOW
   Section 4.1 explicitly assigns OxM as the primary owner of regulatory program
   management and execution. This error has been corrected in this review.

2. **OxM regulatory execution plan status is unknown.** The SOW requires OxM to
   provide a detailed regulatory execution plan and schedule for Intel review and
   approval. It is not confirmed whether this plan has been submitted or is in
   progress.

3. **EMC test status is unconfirmed.** The SOW requires EMC testing at an
   accredited laboratory and preliminary test results or engineering compliance
   assessments to be provided to Intel. Current test readiness is unknown.

4. **Design change impact on compliance scope is unconfirmed.** The SOW requires
   OxM to identify any product design changes that may impact compliance work. It
   is not confirmed whether a formal design-change-impact assessment has been
   completed for Pine Stream COR AP 20CH.

---

### 5. Unknown Risks

1. **OxM lab selection and accreditation status** — If OxM has not yet selected
   an accredited EMC test laboratory, this could delay FCC Part 15 and EN 55032
   certification and block product shipment.

2. **CE marking scope creep** — If the device is CE marked at DV (Design
   Validation) stage, the SOW notes that additional testing and certification
   may be in scope. The extent of this additional work has not been assessed.

3. **Incremental compliance work from design changes** — Any late-stage hardware
   change (layout revision, component substitution, new power configuration) may
   require incremental EMC re-testing. The risk magnitude depends on the change
   type and delta from the previously tested configuration.

4. **EN 61000-3-2 harmonic current limits** — For high-power server platforms,
   EN 61000-3-2 compliance may require power factor correction (PFC) or other
   design measures. The compliance margin for Pine Stream COR AP 20CH power
   supply configuration has not been confirmed.

---

### 6. Impact Assessment

| Domain | Impact Description | Risk Level |
|--------|-------------------|------------|
| Regulatory (EMC) | FCC Part 15 / EN 55032 non-compliance blocks US and EU market entry | **High** |
| Regulatory (RoHS / REACH) | Non-compliance blocks product sale in EU; legal and financial exposure | **High** |
| Regulatory (CE) | CE marking failure blocks EU market entry; customer contract risk | **High** |
| Schedule | Delays in OxM execution plan or EMC testing delay Intel's approval milestones | **Medium** |
| Scope | CE marked DV units may trigger additional tests not budgeted in current plan | **Medium** |

---

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | OxM regulatory execution plan and schedule for Intel review | Regulatory | **Yes** |
| 2 | OxM-selected accredited EMC test laboratory identity and accreditation scope | Regulatory (EMC) | **Yes** |
| 3 | EMC test plan: radiated emissions, conducted emissions, immunity tests per SOW | Regulatory (EMC) | **Yes** |
| 4 | Preliminary EMC test results or OxM engineering compliance assessment | Regulatory (EMC) | No |
| 5 | Design change log for Pine Stream COR AP 20CH — changes with potential compliance impact | Regulatory | **Yes** |
| 6 | CE marking scope assessment — is DV unit CE marked? Are additional tests required? | Regulatory (CE) | No |
| 7 | EN 61000-3-2 harmonic current compliance status for PSU configuration | Regulatory (EMC) | No |
| 8 | RoHS / REACH SVHC compliance declaration for Pine Stream COR AP 20CH BOM | Regulatory | **Yes** |

---

### 8. SOW Regulatory Ownership Matrix

The following table is derived directly from **SOW Section 4 — Regulatory and
Ecology** and represents the correct, contractually-defined ownership for each
regulatory activity. This table supersedes any prior AI determination that stated
"no obvious responsible party."

#### SOW Section 4.1 — Regulatory Program Management

| Obligation | Owner | Intel Role |
|------------|-------|------------|
| Provide detailed product regulatory execution plan and schedule | **OxM** | Review and Approve |
| Manage execution plan to Intel's required completion schedule and approval milestones | **OxM** | Monitor and Accept |
| Provide sufficient data to Intel Regulatory and Ecology engineers at each approval milestone | **OxM** | Review |
| Identify product design changes that may impact product compliance scope | **OxM** | Assess impact jointly with OxM |

#### SOW Section 4 — EMC Testing Ownership

| Activity | Owner | Standard / Requirement |
|----------|-------|----------------------|
| Radiated Emissions test (30 MHz – 5th harmonic of highest frequency or 40 GHz) | **OxM** | FCC Part 15 Subpart B, EN 55032 Class A |
| Conducted Emissions test — all applicable ports: AC mains, wired network, optical fiber (150 kHz – 30 MHz) | **OxM** | FCC Part 15 Subpart B, EN 55032 Class A |
| ESD Immunity — IEC 61000-4-2 | **OxM** | EN 55035 / CISPR 35 Class A |
| Radiated RF Immunity — IEC 61000-4-3 | **OxM** | EN 55035 / CISPR 35 Class A |
| EFT (Electrical Fast Transient) — IEC 61000-4-4 | **OxM** | EN 55035 / CISPR 35 Class A |
| Surge — IEC 61000-4-5 | **OxM** | EN 55035 / CISPR 35 Class A |
| Conducted RF Immunity — IEC 61000-4-6 | **OxM** | EN 55035 / CISPR 35 Class A |
| Magnetic Field Immunity — IEC 61000-4-8 | **OxM** | EN 55035 / CISPR 35 Class A |
| Voltage Dips and Interruptions — IEC 61000-4-11 | **OxM** | EN 55035 / CISPR 35 Class A |
| Harmonic Current — EN 61000-3-2 & EN 61000-3-3 | **OxM** | EN 61000-3-2 & EN 61000-3-3 |
| Preliminary EMC testing or engineering compliance assessment | **OxM** | Provide to Intel |
| Intel Review and Approval of EMC test results | Intel | Final acceptance |

> **Note:** All EMC testing must be conducted at an **accredited test laboratory**.
> Test reports must be provided to Intel for review.  
> **If the device is CE marked at DV stage, additional testing and certification
> may be in scope** — OxM and Intel must assess the incremental work jointly.

---

### 8. Risk Assessment

#### Regulatory Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 5 | FCC/CE/EN 55032 non-compliance is a market-access blocker; RoHS non-compliance creates legal liability; any violation prevents product shipment |
| Occurrence | 2 | OxM is contractually obligated per SOW; standard EMC test processes are well-established; incremental risk comes from late design changes |
| Detection | 1 | All EMC tests are mandatory pre-shipment; RoHS/REACH declarations are reviewed per BOM; 100% coverage if OxM follows SOW obligations |
| **RPN** | **10** | Low Risk (base RPN) |
| Data Confidence | 2 | OxM execution plan status and test progress are unconfirmed; data confidence is low until OxM submits execution plan |

> **Auto-escalation:** Although base RPN = 10 (Low Risk), **Severity = 5 triggers
> mandatory auto-escalation** per Risk Scoring Criteria. The regulatory domain
> is flagged as requiring formal sign-off.
>
> **Low Confidence flag:** Data Confidence = 2 (≤ 2) triggers the **Low
> Confidence** flag, elevating the minimum review level to Engineering Manager
> until OxM submits the regulatory execution plan and preliminary test evidence.
>
> **Effective risk posture: HIGH RISK (pending OxM execution plan submission)**

#### Overall Risk Posture

**MEDIUM RISK (escalated from Low)** — Severity = 5 auto-escalation and Low
Confidence flag apply. Risk is driven not by technical complexity but by the
unconfirmed status of OxM's regulatory execution plan and EMC test progress.
**Once OxM submits the execution plan and confirms lab engagement, the risk
posture will reduce to Low Risk.**

---

### 9. PQRE Recommendation

> **CONDITIONAL APPROVE — Subject to OxM Execution Plan Submission**
>
> The contractual SOW ownership is clear and unambiguous: **OxM is the primary
> responsible party for all regulatory program management and EMC execution
> activities** for Pine Stream COR AP 20CH. Intel's role is review, approval,
> and milestone acceptance.
>
> The following specific actions are required to close this review:
>
> **1. Correct Prior Record:** Any prior PQRE documents, GitHub comments, or
> issue notes that stated "no obvious responsible party" for regulatory work
> on Pine Stream COR AP 20CH must be updated to reflect the correct SOW-defined
> ownership (OxM = primary, Intel = review/approval).
>
> **2. OxM Execution Plan:** OxM must submit a detailed regulatory execution
> plan and schedule per SOW Section 4.1. The plan must cover: EMC testing
> (all tests listed in the SOW), RoHS/REACH BOM compliance review, CE/FCC/UL
> certification plan, and ECCN classification. Intel Regulatory and Ecology
> engineers must review and approve this plan.
>
> **3. Accredited Lab Confirmation:** OxM must confirm the name and accreditation
> scope of the laboratory selected for EMC testing. All tests listed in the SOW
> (radiated emissions, conducted emissions, IEC 61000-4-x series, EN 61000-3-2
> & -3) must be within the lab's accredited scope.
>
> **4. Intel Milestone Review Gate:** At each Intel approval milestone, OxM must
> deliver sufficient compliance data for Intel Regulatory and Ecology engineers
> to complete their review. PQRE sign-off is conditional on milestone data
> delivery.
>
> **5. Design Change Notification:** OxM must maintain a running log of any
> product design changes that may impact the compliance scope. OxM and Intel
> must jointly assess any such changes for incremental compliance work.

---

## 繁體中文（Traditional Chinese）

### ⚠️ 更正說明

先前的 AI 回應錯誤地指出，Pine Stream COR AP 20CH 在法規工作上**沒有明顯安排負責人**。
此結論**與 SOW 合約條文不符，屬事實錯誤**。

**SOW 第 4.1 節 — 法規計畫管理（Regulatory Program Management）** 明確且毫無疑義地
將 **OxM（原始製造商）** 指定為所有法規執行活動的主要責任方。Intel 的角色為審查、核准
與里程碑確認。本報告依 SOW 合約語言更正前述錯誤。

---

### 1. 執行摘要

本次 PQRE 審查由 Issue #128 觸發，目的在於針對 **Pine Stream COR AP 20CH**（Anderson
City ANC 1S / 2S）的法規負責人認定錯誤進行更正。先前的 AI 回應指出「法規領域沒有明顯
安排負責人」，此結論**不正確**。

依據合約性工作說明書（SOW）**第 4 節 — 法規與生態合規**，OxM 已被明確指定為法規計畫管理、
執行規劃、EMC 測試及合規資料交付的主要責任方。

本報告：
1. 依 SOW 合約語言更正先前的負責人認定錯誤。
2. 記錄 SOW 定義的完整法規要求與測試義務。
3. 提供法規領域的 PQRE 風險評估。
4. 建立所有法規活動的正確責任歸屬矩陣。

**整體風險態勢：中風險（MEDIUM RISK）** — 法規領域嚴重程度評分為 5（法規不合規為市場
准入阻斷項），依風險評分準則須自動升級審查。SOW 已**明確將責任指定給 OxM**。
風險在於確認 OxM 已制定有效執行計畫，且交付成果符合 Intel 所需核准里程碑的時程。

---

### 2. 請求分類（Request Classification）

- **請求類型：** SOW 法規負責人澄清 / 更正先前 AI 錯誤
- **平台：** Pine Stream COR AP 20CH（Anderson City ANC 1S / 2S）
- **SOW 參考條文：** 第 4 節 — 法規與生態合規；第 4.1 節 — 法規計畫管理
- **本次審查涵蓋領域：** 法規（EMC、RoHS、CE/FCC/UL、ECCN）
- **不涵蓋領域：** Thermal、SI、PDN、Mechanical、DFM、DFT、Material、Reliability
  *（由獨立 PQRE 審查涵蓋）*
- **風險等級：** 中風險（嚴重程度 = 5，自動升級規則適用）
- **是否需要採取行動：** 是

---

### 3. 是否需採取行動（Yes/No）

**是。** 必須採取以下行動：

1. **更正既有紀錄：** 先前 AI 回應中「沒有明顯安排負責人」的錯誤陳述，須正式更正為
   SOW 合約所定義的正確責任歸屬（OxM = 主要責任方，Intel = 審查/核准方）。

2. **OxM 執行計畫：** 確認 OxM 已提交或正在編制詳細的產品法規執行計畫與時程，
   依 SOW 第 4.1 節規定，涵蓋 EMC、RoHS、CE、FCC 及其他適用認證活動。

3. **Intel 審查門控：** Intel 法規與生態工程師須在每個核准里程碑節點，依 SOW 第 4.1
   節規定參與審查 OxM 的執行計畫。

4. **EMC 測試軌道：** 確認 OxM 已洽詢認可實驗室執行 SOW 所列 EMC 量測，且初步測試
   結果或工程合規評估報告按時程提供。

---

### 4. 已知問題（Known Issues）

1. **先前 AI 回應錯誤指出無明確負責人。** SOW 第 4.1 節明確將法規計畫管理與執行的
   主要責任指定給 OxM，本次已更正此錯誤。

2. **OxM 法規執行計畫狀態未知。** SOW 要求 OxM 提供詳細的法規執行計畫與時程供
   Intel 審查核准，目前尚不確認計畫是否已提交或正在進行。

3. **EMC 測試狀態未確認。** SOW 要求 OxM 在認可實驗室進行 EMC 測試，並提供初步測試
   結果或工程合規評估給 Intel。目前測試準備度未知。

4. **設計變更對合規範圍的影響尚未確認。** SOW 要求 OxM 識別可能影響合規工作的產品設計
   變更。目前尚未確認 Pine Stream COR AP 20CH 是否已完成正式的設計變更影響評估。

---

### 5. 未知風險（Unknown Risks）

1. **OxM 實驗室選擇與認可狀態** — 若 OxM 尚未選定認可 EMC 實驗室，可能延誤
   FCC Part 15 及 EN 55032 認證，阻礙產品出貨。

2. **CE 標誌範圍擴大** — 若 DV 裝置已 CE 標誌，SOW 說明可能需要額外測試與認證，
   相關工作量尚未評估。

3. **設計變更引發的增量合規工作** — 任何後期硬體變更（佈局修訂、零件替換、新電源
   配置）可能需要增量 EMC 重新測試，風險大小取決於變更類型與先前受測配置的差異。

4. **EN 61000-3-2 諧波電流限制** — 對高功率伺服器平台，EN 61000-3-2 合規可能需要
   功率因數校正（PFC）或其他設計措施。Pine Stream COR AP 20CH 電源供應配置的合規裕度
   尚未確認。

---

### 6. 影響評估（Impact Assessment）

| 領域 | 影響說明 | 風險等級 |
|------|---------|---------|
| 法規（EMC） | FCC Part 15 / EN 55032 不合規將阻止進入美國及歐盟市場 | **高** |
| 法規（RoHS / REACH） | 不合規阻止在歐盟銷售產品；存在法律及財務曝險 | **高** |
| 法規（CE 標誌） | CE 標誌失效阻止進入歐盟市場；存在客戶合約風險 | **高** |
| 時程 | OxM 執行計畫延遲或 EMC 測試延誤將影響 Intel 核准里程碑 | **中** |
| 範圍 | CE 標誌 DV 裝置可能觸發現有計畫未編列預算的額外測試 | **中** |

---

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | 阻擋性 |
|---|---------|------|--------|
| 1 | OxM 法規執行計畫及時程（供 Intel 審查） | 法規 | **是** |
| 2 | OxM 選定的認可 EMC 測試實驗室名稱及認可範圍 | 法規（EMC） | **是** |
| 3 | EMC 測試計畫：依 SOW 的輻射、傳導發射及抗擾度測試項目 | 法規（EMC） | **是** |
| 4 | EMC 初步測試結果或 OxM 工程合規評估報告 | 法規（EMC） | 否 |
| 5 | Pine Stream COR AP 20CH 設計變更記錄（具合規影響者） | 法規 | **是** |
| 6 | CE 標誌範圍評估 — DV 裝置是否已 CE 標誌？是否需要額外測試？ | 法規（CE） | 否 |
| 7 | 電源配置的 EN 61000-3-2 諧波電流合規狀態 | 法規（EMC） | 否 |
| 8 | Pine Stream COR AP 20CH BOM 的 RoHS / REACH SVHC 合規聲明 | 法規 | **是** |

---

### 8. SOW 法規責任歸屬矩陣（SOW Regulatory Ownership Matrix）

下表直接源自 **SOW 第 4 節 — 法規與生態合規**，代表各法規活動的正確合約性責任歸屬。
本表取代任何先前指出「沒有明顯安排負責人」的 AI 判斷。

#### SOW 第 4.1 節 — 法規計畫管理

| 義務 | 負責方 | Intel 角色 |
|------|--------|-----------|
| 提供詳細產品法規執行計畫與時程 | **OxM** | 審查與核准 |
| 管理執行計畫以符合 Intel 所需完成時程與核准里程碑 | **OxM** | 監控與接受 |
| 在每個核准里程碑提供足夠資料供 Intel 法規與生態工程師審查 | **OxM** | 審查 |
| 識別可能影響合規範圍的產品設計變更 | **OxM** | 與 OxM 共同評估影響 |

#### SOW 第 4 節 — EMC 測試責任歸屬

| 活動 | 負責方 | 標準 / 要求 |
|------|--------|-----------|
| 輻射發射測試（30 MHz – 最高頻率之五次諧波或 40 GHz） | **OxM** | FCC Part 15 Subpart B、EN 55032 Class A |
| 傳導發射測試 — 所有適用連接埠：AC 主電源、有線網路、光纖（150 kHz – 30 MHz） | **OxM** | FCC Part 15 Subpart B、EN 55032 Class A |
| ESD 抗擾度 — IEC 61000-4-2 | **OxM** | EN 55035 / CISPR 35 Class A |
| 輻射 RF 抗擾度 — IEC 61000-4-3 | **OxM** | EN 55035 / CISPR 35 Class A |
| EFT（電氣快速暫態）— IEC 61000-4-4 | **OxM** | EN 55035 / CISPR 35 Class A |
| 突波 — IEC 61000-4-5 | **OxM** | EN 55035 / CISPR 35 Class A |
| 傳導 RF 抗擾度 — IEC 61000-4-6 | **OxM** | EN 55035 / CISPR 35 Class A |
| 磁場抗擾度 — IEC 61000-4-8 | **OxM** | EN 55035 / CISPR 35 Class A |
| 電壓驟降與中斷 — IEC 61000-4-11 | **OxM** | EN 55035 / CISPR 35 Class A |
| 諧波電流 — EN 61000-3-2 & EN 61000-3-3 | **OxM** | EN 61000-3-2 & EN 61000-3-3 |
| 初步 EMC 測試或工程合規評估 | **OxM** | 提供給 Intel |
| Intel 審查與核准 EMC 測試結果 | Intel | 最終接受 |

> **注意：** 所有 EMC 測試須在**認可實驗室**進行，測試報告須提供 Intel 審查。  
> **若 DV 裝置已 CE 標誌，可能需要額外測試與認證** — OxM 與 Intel 須共同評估
> 增量工作範圍。

---

### 風險評估（Risk Assessment）

#### 法規領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| Severity（嚴重程度） | 5 | FCC/CE/EN 55032 不合規為市場准入阻斷項；RoHS 不合規產生法律責任；任何違規均阻止產品出貨 |
| Occurrence（發生機率） | 2 | OxM 依 SOW 具有合約義務；標準 EMC 測試流程完善；增量風險來自後期設計變更 |
| Detection（偵測能力） | 1 | 所有 EMC 測試均為出貨前強制要求；RoHS/REACH 聲明依 BOM 逐項審查；若 OxM 遵循 SOW 義務即達 100% 覆蓋率 |
| **RPN** | **10** | 低風險（基礎 RPN） |
| 資料可信度（Data Confidence） | 2 | OxM 執行計畫狀態與測試進度未確認；資料可信度偏低，直至 OxM 提交執行計畫後方可提升 |

> **自動升級：** 儘管基礎 RPN = 10（低風險），**嚴重程度 = 5 依風險評分準則觸發強制
> 自動升級**，法規領域須進行正式簽核。
>
> **低可信度標記：** 資料可信度 = 2（≤ 2）觸發**低可信度（Low Confidence）**標記，
> 最低審查層級提升至工程部門主管，直至 OxM 提交法規執行計畫及初步測試證據。
>
> **有效風險態勢：高風險（等待 OxM 執行計畫提交前）**

#### 整體風險態勢

**中風險（由低升級）** — 嚴重程度 = 5 自動升級及低可信度標記均適用。風險源非技術複雜度，
而是 OxM 法規執行計畫及 EMC 測試進度尚未確認。**一旦 OxM 提交執行計畫並確認已洽詢認可
實驗室，風險態勢將降回低風險。**

---

### 9. PQRE 建議（PQRE Recommendation）

> **有條件核准（CONDITIONAL APPROVE）— 以 OxM 提交執行計畫為前提**
>
> 合約性 SOW 責任歸屬清晰且毫無疑義：**OxM 是 Pine Stream COR AP 20CH 所有法規計畫
> 管理與 EMC 執行活動的主要責任方**。Intel 的角色為審查、核准與里程碑確認。
>
> 須採取以下具體行動以關閉本次審查：
>
> **1. 更正既有紀錄：** 任何先前指出 Pine Stream COR AP 20CH 法規工作「沒有明顯安排
> 負責人」的 PQRE 文件、GitHub 評論或問題備註，須更新為正確的 SOW 定義責任歸屬
>（OxM = 主要責任方，Intel = 審查/核准方）。
>
> **2. OxM 執行計畫：** OxM 須依 SOW 第 4.1 節提交詳細的法規執行計畫與時程，
> 涵蓋：EMC 測試（SOW 所列全部測試項目）、RoHS/REACH BOM 合規審查、CE/FCC/UL
> 認證計畫及 ECCN 分類。Intel 法規與生態工程師須審查並核准此計畫。
>
> **3. 確認認可實驗室：** OxM 須確認 EMC 測試所選實驗室的名稱及認可範圍。SOW 所列
> 全部測試（輻射發射、傳導發射、IEC 61000-4-x 系列、EN 61000-3-2 & -3）均須在
> 實驗室的認可範圍內。
>
> **4. Intel 里程碑審查門控：** 在每個 Intel 核准里程碑，OxM 須交付足夠的合規資料
> 供 Intel 法規與生態工程師完成審查。PQRE 簽核以里程碑資料交付為前提條件。
>
> **5. 設計變更通知：** OxM 須維護可能影響合規範圍之產品設計變更的持續記錄。
> 任何此類變更，OxM 與 Intel 須共同評估增量合規工作需求。
