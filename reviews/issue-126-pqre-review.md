# PQRE Risk Review — Issue #126

**Issue:** [AI Risk Review] Re: Pine stream COR AP 20CH - Budgetary Demand Collection Kick off meeting
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/126
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-21
**Requestor:** ccgglee
**Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20CH
**Agent Instruction:** 請幫忙確認 過去的SOW中 關於regulatory 由誰負責執行 和準備 硬體 軟體
*(Please confirm from past SOW records: who is responsible for executing and preparing regulatory hardware and software.)*

---

## English

### 1. Executive Summary

This PQRE review was triggered by Issue #126, which is associated with the
**Pine Stream COR AP 20CH Budgetary Demand Collection Kick-off Meeting**. The
agent instruction asks to review **past SOW (Statement of Work) records** to
confirm:

1. Who is responsible for **executing** Regulatory activities.
2. Who is responsible for **preparing Hardware** for Regulatory activities.
3. Who is responsible for **preparing Software** for Regulatory activities.

A cross-review of all existing PQRE records for Pine Stream COR AP 20CH
(Issues #59, #80, #110) was conducted. The findings indicate that regulatory
ownership assignments in all past intake records are currently listed as **[TBD]
(To Be Determined)**. No formally named responsible individuals or teams for
regulatory execution, hardware preparation, or software preparation have been
recorded in the available PQRE evidence base.

Issue #110 provides the most advanced regulatory planning context for ANC
Pine Stream COR 20CH and identifies the responsible function as the
**regulatory/compliance engineer** within **DCAI Server Q&R — Platform Quality
& Reliability Engineering (PQRE) — Boards & Systems Team**, but does not name
a specific individual.

> **Finding: Regulatory ownership — Execution, Hardware Preparation, and
> Software Preparation — is not formally assigned in available SOW records.
> Ownership gaps must be resolved before qualification activities can begin.**

---

### 2. SOW Regulatory Ownership — Cross-Review of Past Records

The following table summarises regulatory ownership as recorded in prior PQRE
review records for Pine Stream COR AP 20CH:

| Issue | Platform Record | Regulatory Owner | Hardware Prep Owner | Software Prep Owner | Status |
|-------|----------------|------------------|---------------------|---------------------|--------|
| #59 | Pine Stream COR AP 20CH — Initial query | [TBD] | [TBD] | [TBD] | Early intake placeholder; no SOW submitted |
| #80 | ANC 1S/2S — PRD opened | Reliability / PQRE team (general) | [TBD] | [TBD] | PRD stage; no qualification plan |
| #110 | ANC 1S/2S — HCR scoping (Reliability, Regulatory, Packaging) | Regulatory / compliance engineer (role, no name) | PQRE — Boards & Systems Team (role, no name) | Not explicitly addressed | Most detailed record; owner role defined, person TBD |

**Summary of Findings:**

- **Regulatory Execution Owner:** The regulatory compliance engineer within
  DCAI Server Q&R — PQRE — Boards & Systems Team is identified as the
  accountable role (Issue #110, Q4 guidance). No specific individual IDSID or
  name has been committed in any SOW record.

- **Hardware Preparation Owner:** Hardware preparation for regulatory activities
  (BOM delta review, physical sample submission to certification lab) is the
  responsibility of the **PQRE — Boards & Systems Team**. The specific hardware
  engineer or lab coordinator responsible for Anderson City sample submission has
  not been recorded.

- **Software Preparation Owner:** No SOW record for Pine Stream COR AP 20CH
  addresses software preparation for regulatory activities. For typical
  RoHS/REACH/CE/FCC certification workflows, firmware and embedded software
  content affecting CE/FCC emissions (e.g., RF emissions from PCIe, DDR, or
  network interfaces) may require software support. This ownership has not
  been assigned or documented in any past review.

---

### 3. Regulatory Activity Scope — What Needs an Owner

Based on the regulatory scope defined in Issue #110 and the PQRE Sign-Off
Criteria (`KnowledgeBase/pqre_signoff_criteria.md`), the following regulatory
activities require designated owners:

#### 3.1 Regulatory Execution Activities

| Activity | Description | Owner Required |
|----------|-------------|----------------|
| BOM delta review | Compare ANC BOM vs. JNC BOM; identify new/changed components | Regulatory / Compliance Engineer |
| RoHS compliance declaration | Obtain RoHS compliance declaration for each new component | Regulatory / Compliance Engineer |
| REACH SVHC declaration | Obtain REACH SVHC declaration for each new component | Regulatory / Compliance Engineer |
| CE / FCC / UL certification | Submit ANC hardware to accredited lab; manage certification process | Regulatory / Compliance Engineer + Lab Coordinator |
| ECCN re-classification | Review dual-use export classification for any new components | Regulatory / Export Control |

#### 3.2 Hardware Preparation Activities

| Activity | Description | Owner Required |
|----------|-------------|----------------|
| Engineering sample provisioning | Prepare ANC 1S/2S hardware samples in production-representative configuration | Hardware / Platform Engineer |
| BOM lock for regulatory submission | Confirm BOM revision used for certification; lock component list | Hardware / Design Engineer |
| EMC pre-compliance testing | Pre-screen for CE/FCC EMC (radiated/conducted emissions) prior to lab submission | Hardware / EMC Engineer |
| Physical sample shipping to lab | Package and ship ANC samples to certification lab | Lab Coordinator / Logistics |

#### 3.3 Software Preparation Activities

| Activity | Description | Owner Required |
|----------|-------------|----------------|
| Firmware version lock for certification | Identify and lock firmware/BIOS version used during CE/FCC testing | Firmware / BIOS Engineer |
| Software-controlled emissions configuration | Confirm software settings that affect EMC emissions (spread spectrum, PCIe ASPM, DDR power states) | Firmware / BIOS / Software Engineer |
| Test software readiness | Provide any required test utilities or configuration scripts for certification lab | Software / Validation Engineer |

---

### 4. Known Issues

1. **Regulatory ownership is unassigned in all past SOW records.** No
   individual or team has been formally named as the Regulatory Execution Owner,
   Hardware Preparation Owner, or Software Preparation Owner for Pine Stream
   COR AP 20CH regulatory activities.

2. **Software preparation for regulatory activities has never been addressed.**
   All past reviews focus on hardware-level regulatory compliance (BOM,
   RoHS/REACH, CE/FCC hardware emissions). Software-controlled emissions and
   firmware version lock — which are required for CE/FCC certification — have
   not been scoped or assigned.

3. **BOM delta analysis between JNC and ANC is not yet complete.** Until the
   delta BOM is confirmed, the full scope of regulatory work (new component
   count, re-certification need) cannot be estimated and work cannot be
   assigned to owners.

4. **No SOW document with formal owner assignments exists in the PQRE evidence
   base.** All past reviews used [TBD] placeholders. A formal SOW with named
   owners must be created before the qualification program can proceed.

---

### 5. Gap Analysis

| Gap | Domain | Impact | Blocking |
|-----|--------|--------|----------|
| Regulatory execution owner not named | Regulatory | Certification timeline undefined; no accountable engineer | **Yes** |
| Hardware preparation owner not named | Regulatory / Hardware | Sample provisioning and BOM lock may be delayed | **Yes** |
| Software preparation owner not named | Regulatory / Software | CE/FCC certification may fail if firmware version is not locked; emissions configuration undocumented | **Yes** |
| BOM delta (ANC vs. JNC) not completed | Regulatory | Cannot determine scope of new component declarations required | **Yes** |
| CE/FCC certification lab not selected | Regulatory | Test schedule cannot be set | No |
| ECCN review status unknown | Regulatory / Export | Export clearance may be delayed | No |

---

### 6. Risk Assessment

#### Regulatory Domain — Risk Scoring

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 5 | Regulatory non-compliance blocks market access (EU, US); legal and financial exposure |
| Occurrence | 3 | Ownership gaps and missing BOM delta increase the probability of missed compliance activities |
| Detection | 2 | RoHS/REACH and CE/FCC processes are auditable; gaps are detectable during BOM review and pre-compliance test |
| **RPN** | **30** | **Medium Risk** |
| Data Confidence | 2 | No formal SOW with named owners; BOM delta not confirmed |

> Severity = 5 triggers **auto-escalation** per Risk Scoring Criteria
> regardless of RPN value. This must be escalated to the PQRE Manager and
> Business Owner.
>
> Data Confidence = 2 (≤ 2) triggers the **Low Confidence** flag. The domain
> is treated as **High Risk** pending owner assignment and BOM delta submission.

**Overall Risk Posture: HIGH RISK** (Severity = 5 auto-escalation + Low
Confidence flag triggered).

---

### 7. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Assign named individual as Regulatory Execution Owner for ANC Pine Stream COR 20CH; record IDSID and org path in HSDES and this PQRE record | PQRE Manager | [TBD] | **Yes** |
| 2 | Assign named individual as Hardware Preparation Owner (BOM lock, sample provisioning, lab coordination) | Hardware / Platform Lead | [TBD] | **Yes** |
| 3 | Assign named individual as Software / Firmware Preparation Owner (firmware lock, emissions config documentation) | Firmware / BIOS Lead | [TBD] | **Yes** |
| 4 | Complete BOM delta analysis: ANC Pine Stream COR 20CH vs. JNC1/JNC2 (DMR AP RP) — identify all new/changed components requiring new compliance declarations | Regulatory Execution Owner | [TBD] | **Yes** |
| 5 | Initiate RoHS / REACH SVHC declaration collection for all new ANC components identified in Action 4 | Regulatory Execution Owner | [TBD] | **Yes** |
| 6 | Define firmware version to be used during CE / FCC certification testing; document in SOW | Software Prep Owner | [TBD] | **Yes** |
| 7 | Select CE / FCC / UL accredited test laboratory; confirm test schedule | Regulatory Execution Owner + Lab Coordinator | [TBD] | No |
| 8 | Conduct CE / FCC EMC pre-compliance screen on ANC hardware with locked firmware; address any failures before formal lab submission | Hardware Prep Owner + Software Prep Owner | [TBD] | No |
| 9 | Update PQRE SOW document with all named owners, scope, and target dates; submit to PQRE for record | PQRE Owner | [TBD] | **Yes** |

---

### 8. PQRE Recommendation

> **HOLD — Regulatory Ownership Not Assigned**
>
> Regulatory ownership for execution, hardware preparation, and software
> preparation is unassigned in all available Pine Stream COR AP 20CH SOW
> records. Qualification activities cannot proceed without named accountable
> engineers.
>
> The following immediate actions are required to clear this HOLD:
>
> 1. Assign named Regulatory Execution Owner (Action 1).
> 2. Assign named Hardware Preparation Owner (Action 2).
> 3. Assign named Software / Firmware Preparation Owner (Action 3).
> 4. Complete BOM delta analysis (Action 4).
>
> Once Actions 1–4 are complete, resubmit for PQRE review. A
> **CONDITIONAL APPROVE** can be issued when all blocking actions in Section 7
> are assigned with target dates, even if execution is not yet complete.

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次 PQRE 審查由 Issue #126 觸發，與 **Pine Stream COR AP 20CH 預算需求收集啟動會議（Budgetary Demand Collection Kick-off Meeting）** 相關。Agent 指令要求審查**過去 SOW（工作說明書）紀錄**，以確認：

1. **法規（Regulatory）活動的執行責任人**為誰。
2. **法規活動的硬體準備責任人**為誰。
3. **法規活動的軟體準備責任人**為誰。

本次審查對 Pine Stream COR AP 20CH 所有現有 PQRE 紀錄（Issues #59、#80、#110）進行交叉核查。結果顯示：**所有過去受理紀錄中，法規責任人均標記為 [TBD]（待確認）**。在現有 PQRE 證據資料庫中，尚無任何正式指定的法規執行、硬體準備或軟體準備負責人。

Issue #110 提供 ANC Pine Stream COR 20CH 最完整的法規規劃背景，並將負責職能定義為 **DCAI Server Q&R — Platform Quality & Reliability Engineering (PQRE) — Boards & Systems Team** 中的**法規/合規工程師**，但未指名具體人員。

> **發現：法規活動的執行責任、硬體準備及軟體準備，在現有 SOW 紀錄中均未正式指定負責人，必須在資格驗證活動啟動前完成責任歸屬。**

---

### 2. SOW 法規責任人 — 歷史紀錄交叉核查

下表彙整 Pine Stream COR AP 20CH 歷次 PQRE 審查紀錄中的法規責任人資訊：

| Issue | 平台紀錄 | 法規執行責任人 | 硬體準備責任人 | 軟體準備責任人 | 狀態 |
|-------|---------|-------------|-------------|-------------|------|
| #59 | Pine Stream COR AP 20CH — 初始查詢 | [TBD] | [TBD] | [TBD] | 前期受理佔位；未提交 SOW |
| #80 | ANC 1S/2S — PRD 開啟 | 可靠度 / PQRE 團隊（籠統說法） | [TBD] | [TBD] | PRD 階段，無資格驗證計畫 |
| #110 | ANC 1S/2S — HCR 範疇界定（可靠度、法規、包裝） | 法規/合規工程師（職能描述，無具體人名） | PQRE — Boards & Systems Team（職能描述，無具體人名） | 未明確說明 | 最完整紀錄；已定義職能，人員待確認 |

**核查結果摘要：**

- **法規執行責任人：** Issue #110 Q4 指引中將 DCAI Server Q&R — PQRE — Boards & Systems Team 中的法規合規工程師列為應負責職能。所有 SOW 紀錄中均未承諾具體個人 IDSID 或姓名。

- **硬體準備責任人：** 法規活動的硬體準備（BOM 差異審查、實體樣品送交認證實驗室）由 **PQRE — Boards & Systems Team** 負責。負責 Anderson City 樣品送件的具體硬體工程師或實驗室協調員尚未記錄。

- **軟體準備責任人：** 現有 Pine Stream COR AP 20CH SOW 紀錄均未涉及法規活動的軟體準備。典型 CE/FCC 認證流程中，影響 CE/FCC 電磁輻射的韌體及嵌入式軟體（例如 PCIe、DDR、網路介面的電磁輻射設定）需要軟體層面的配合，但此責任歸屬從未在歷次審查中指定或記錄。

---

### 3. 法規活動範疇 — 需要指定責任人的項目

依據 Issue #110 界定的法規範疇及 PQRE 簽核標準（`KnowledgeBase/pqre_signoff_criteria.md`），以下法規活動均需指定負責人：

#### 3.1 法規執行活動

| 活動 | 說明 | 所需責任人 |
|------|------|----------|
| BOM 差異審查 | 比對 ANC 與 JNC BOM；識別新增/變更元件 | 法規/合規工程師 |
| RoHS 合規聲明 | 為每個新元件取得 RoHS 合規聲明 | 法規/合規工程師 |
| REACH SVHC 聲明 | 為每個新元件取得 REACH SVHC 聲明 | 法規/合規工程師 |
| CE / FCC / UL 認證 | 將 ANC 硬體送交認證實驗室；管理認證流程 | 法規/合規工程師 + 實驗室協調員 |
| ECCN 重新分類 | 針對 BOM 中新增元件進行雙重用途出口管制分類審查 | 法規/出口管制 |

#### 3.2 硬體準備活動

| 活動 | 說明 | 所需責任人 |
|------|------|----------|
| 工程樣品備料 | 以量產代表性配置備妥 ANC 1S/2S 硬體樣品 | 硬體/平台工程師 |
| 法規送件 BOM 鎖定 | 確認並鎖定認證所用 BOM 版本及元件清單 | 硬體/設計工程師 |
| EMC 預合規測試 | 正式實驗室送件前進行 CE/FCC 電磁相容性預篩測試 | 硬體/EMC 工程師 |
| 實體樣品寄送至實驗室 | 包裝並寄送 ANC 樣品至認證實驗室 | 實驗室協調員/物流 |

#### 3.3 軟體準備活動

| 活動 | 說明 | 所需責任人 |
|------|------|----------|
| 認證用韌體版本鎖定 | 確認並鎖定 CE/FCC 測試所用韌體/BIOS 版本 | 韌體/BIOS 工程師 |
| 軟體控制之輻射設定確認 | 確認影響 EMC 輻射之軟體設定（展頻、PCIe ASPM、DDR 電源狀態等） | 韌體/BIOS/軟體工程師 |
| 測試軟體就緒確認 | 提供認證實驗室所需測試工具或設定腳本 | 軟體/驗證工程師 |

---

### 4. 已知問題（Known Issues）

1. **所有過去 SOW 紀錄中，法規責任人均未指定。** 未有任何個人或團隊被正式指名為 Pine Stream COR AP 20CH 法規執行責任人、硬體準備責任人或軟體準備責任人。

2. **法規活動的軟體準備從未被納入討論。** 所有歷次審查均聚焦於硬體層面的法規合規（BOM、RoHS/REACH、CE/FCC 硬體輻射）。軟體控制的電磁輻射設定及韌體版本鎖定——CE/FCC 認證的必要條件——從未被界定範疇或指定責任人。

3. **JNC 至 ANC 的 BOM 差異分析尚未完成。** BOM 差異未確認前，無法估算法規工作的完整範疇（新元件數量、是否需要重新認證），工作亦無法分配給責任人。

4. **PQRE 證據資料庫中不存在具有正式責任人指定的 SOW 文件。** 所有過去審查均使用 [TBD] 占位符。必須建立具名責任人的正式 SOW，資格驗證計畫才能推進。

---

### 5. 缺口分析（Gap Analysis）

| 缺口 | 領域 | 影響 | 阻擋性 |
|-----|------|------|--------|
| 法規執行責任人未指定 | 法規 | 認證時程無法確定；無當責工程師 | **是** |
| 硬體準備責任人未指定 | 法規/硬體 | 樣品備料與 BOM 鎖定可能延誤 | **是** |
| 軟體準備責任人未指定 | 法規/軟體 | CE/FCC 認證可能因韌體版本未鎖定而失敗；輻射設定未記錄 | **是** |
| BOM 差異（ANC vs. JNC）未完成 | 法規 | 無法確定所需新元件聲明的範疇 | **是** |
| CE/FCC 認證實驗室未選定 | 法規 | 測試時程無法確定 | 否 |
| ECCN 審查狀態未知 | 法規/出口管制 | 出口許可可能延誤 | 否 |

---

### 6. 風險評估（Risk Assessment）

#### 法規領域 — 風險評分

| 參數 | 評分 | 說明 |
|------|------|------|
| 嚴重度（S） | 5 | 法規不符規定將阻斷市場進入（歐盟、美國）；涉及法律與財務風險 |
| 發生頻率（O） | 3 | 責任歸屬缺口與 BOM 差異未確認，增加錯漏合規活動的可能性 |
| 可偵測性（D） | 2 | RoHS/REACH 及 CE/FCC 流程具可稽核性；BOM 審查與預合規測試可偵測缺口 |
| **RPN** | **30** | **中等風險（Medium Risk）** |
| 資料可信度 | 2 | 無具名責任人的正式 SOW；BOM 差異未確認 |

> 嚴重度 = 5，依據風險評分標準觸發**自動升級**，無論 RPN 數值為何，必須升級至 PQRE Manager 及 Business Owner。
>
> 資料可信度 = 2（≤ 2），觸發**低可信度旗標**。在完成責任人指定與 BOM 差異確認前，本領域視同**高風險（High Risk）**。

**整體風險態勢：高風險（HIGH RISK）**（嚴重度 = 5 自動升級 + 低可信度旗標）。

---

### 7. 必要行動（Required Actions）

| # | 行動 | 責任人 | 到期日 | 阻擋性 |
|---|------|--------|--------|--------|
| 1 | 指定具名法規執行責任人；在 HSDES 及本 PQRE 紀錄中記錄其 IDSID 及組織路徑 | PQRE Manager | [TBD] | **是** |
| 2 | 指定具名硬體準備責任人（BOM 鎖定、樣品備料、實驗室協調） | 硬體/平台主管 | [TBD] | **是** |
| 3 | 指定具名軟體/韌體準備責任人（韌體鎖定、輻射設定記錄） | 韌體/BIOS 主管 | [TBD] | **是** |
| 4 | 完成 BOM 差異分析：ANC Pine Stream COR 20CH vs. JNC1/JNC2（DMR AP RP）— 識別所有需要新合規聲明的新增/變更元件 | 法規執行責任人 | [TBD] | **是** |
| 5 | 啟動對行動 4 識別的所有 ANC 新元件的 RoHS / REACH SVHC 聲明收集工作 | 法規執行責任人 | [TBD] | **是** |
| 6 | 確定 CE / FCC 認證測試所用韌體版本；記錄於 SOW | 軟體準備責任人 | [TBD] | **是** |
| 7 | 選定 CE / FCC / UL 認可測試實驗室；確認測試時程 | 法規執行責任人 + 實驗室協調員 | [TBD] | 否 |
| 8 | 使用鎖定韌體版本對 ANC 硬體進行 CE / FCC EMC 預合規篩測；正式送件前解決發現的問題 | 硬體準備責任人 + 軟體準備責任人 | [TBD] | 否 |
| 9 | 更新 PQRE SOW 文件，記錄所有具名責任人、範疇及目標日期；送交 PQRE 存檔 | PQRE 負責人 | [TBD] | **是** |

---

### 8. PQRE 建議（PQRE Recommendation）

> **暫緩（HOLD）— 法規責任人未指定**
>
> Pine Stream COR AP 20CH 現有所有 SOW 紀錄中，法規執行、硬體準備及軟體準備的責任人均未指定。在指定具名當責工程師之前，資格驗證活動無法推進。
>
> 解除本次暫緩需完成以下立即行動：
>
> 1. 指定具名法規執行責任人（行動 1）。
> 2. 指定具名硬體準備責任人（行動 2）。
> 3. 指定具名軟體/韌體準備責任人（行動 3）。
> 4. 完成 BOM 差異分析（行動 4）。
>
> 完成行動 1–4 並提交重新審查後，若第 7 節所有阻擋性行動均已指定責任人與目標日期（即使執行尚未完成），可發出**有條件批准（CONDITIONAL APPROVE）**。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-21.
This review is an advisory output. Final engineering decisions require human sign-off.*
