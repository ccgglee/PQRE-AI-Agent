# PQRE Risk Review — Issue #101

**Issue:** [AI Risk Review] RE: PRD for Anderson City 1/2 (Pine Stream COR 20CH) is now open
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/101
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-17
**Requestor:** Eduardo Barajas Palomino (forwarded by ccgglee)
**Platform:** Anderson City (ANC) 1S / 2S — Pine Stream COR 20 CH

---

## English

### 1. Executive Summary

This intake announces that the Anderson City (ANC) 1S / 2S PRD window is open
and directs teams to submit new platform hardware feature requests through a
form. The request is relevant to PQRE because it concerns ANC platform hardware
qualification enablement, including new COR capabilities such as added DDR
channels, expanded power SKUs, security hardware integration, and DC-SCM
hardware changes. However, the email provides no engineering evidence, no
feature-by-feature delta analysis, and no ownership or qualification plan.
Current PQRE posture is **HOLD** for hardware-related items due to missing
evidence, with an additional routing rule that any request not related to
platform hardware or validation hardware (for example BMC firmware-only scope)
must be rejected from this workflow.

### 2. Request Classification

- **Request type:** PRD intake opening notice plus questionnaire/submission guidance
- **Hardware scope decision:** Mixed intake; platform hardware and validation
  hardware items are in scope, but non-hardware asks must be rejected or routed
  elsewhere
- **Domains in scope:** Thermal, SI / PDN, Mechanical, DFM, DFT, Material,
  Regulatory, Reliability
- **Potential out-of-scope content:** BMC firmware-only requests with no
  hardware impact
- **Risk tier:** High Risk (Low Confidence — no quantified engineering data)

### 3. Action Required (Yes/No)

**Yes.**

Hardware-related feature requests require a complete intake package before PQRE
can provide a sign-off-capable recommendation. In addition, any bundled request
must be split if it mixes platform hardware items with non-hardware items such
as firmware-only changes.

### 4. Known Issues

1. **PRD notice only; no technical evidence attached.** The intake includes the
   announcement and form link, but no feature-specific delta package, no
   reliability data, and no qualification plan.
2. **Multiple feature themes are bundled together.** The email references
   Caliptra, four additional DDR channels, 750 W / 1200 W power offerings, and
   a new DC-SCM with AST2700. These changes may affect different PQRE domains
   and should not be treated as a single undifferentiated qualification item.
3. **Reliability-stress impact is not yet defined.** There is no statement of
   whether existing platform or validation hardware stress coverage remains
   valid for the ANC deltas.
4. **Firmware / software adjacency risk exists.** The AST2700 mention may lead
   requestors to include BMC firmware-only asks. Those are out of scope for
   this hardware PQRE path unless tied to a hardware change.

### 5. Unknown Risks

- Whether added DDR channels change SI / PDN loading, routing complexity, or
  thermal density beyond previously qualified bounds
- Whether 750 W / 1200 W SKUs require new thermal, derating, and reliability
  stress coverage for platform hardware or validation hardware
- Whether DC-SCM mechanical, connector, or material changes introduce new DFM,
  DFT, shock, or packaging risks
- Whether prior DMR AP or other predecessor data can be re-used for ANC without
  supplemental stress
- Whether the submitted form will mix hardware and non-hardware requests,
  causing routing and sign-off confusion

### 6. Impact Assessment

| Category | Current Impact Assessment |
|----------|---------------------------|
| Schedule | PQRE sign-off is blocked until hardware feature deltas and evidence packages are submitted |
| Quality | Incomplete form responses could hide feature-specific qualification gaps |
| Reliability | New power, memory, and DC-SCM deltas may require new or supplemental stress coverage |
| Compliance | Regulatory and material declarations are not yet available for new hardware content |
| Process / Routing | Mixed hardware and non-hardware requests may be misrouted unless split clearly |

### 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | Feature-by-feature hardware delta list for ANC 1S / 2S submissions | All | **Yes** |
| 2 | Identification of which requested items affect platform hardware or validation hardware | Routing / Reliability | **Yes** |
| 3 | Thermal / power data for 750 W and 1200 W SKUs | Thermal / Reliability | **Yes** |
| 4 | SI / PDN evidence for four additional DDR channels | SI / PDN | **Yes** |
| 5 | DC-SCM hardware definition, interfaces, and mechanical impact | Mechanical / DFM / DFT | **Yes** |
| 6 | Reliability stress re-use assessment or new stress plan for ANC deltas | Reliability | **Yes** |
| 7 | Regulatory and material declarations for new hardware content | Regulatory / Material | **Yes** |
| 8 | Named owner, organization, and due date fields for each form submission | Program / Routing | No |

### 8. Required Actions

1. Submit separate or clearly partitioned form entries for each ANC hardware
   feature request; do not mix firmware-only asks into the same PQRE hardware
   submission.
2. For each hardware item, provide the affected platform hardware or validation
   hardware scope, design delta, and qualification objective.
3. Provide thermal, power, SI / PDN, and reliability evidence for any feature
   that changes the operating envelope relative to the existing baseline.
4. For DC-SCM or board-level feature requests, attach mechanical, DFM, DFT,
   and material evidence packages.
5. If an item is firmware-only (for example BMC firmware with no hardware
   change), reject or reroute it outside this hardware PQRE workflow.
6. Assign owner, team, and target date fields for each submission before PQRE
   closure.
7. Re-submit the completed evidence package for full PQRE review after the form
   entries are finalized.

### 9. PQRE Recommendation

> **HOLD — Hardware intake guidance issued; evidence package required**
>
> The ANC PRD opening notice is relevant to PQRE, but the current intake is only
> a routing and questionnaire notification. PQRE can support hardware-related
> form submissions for platform hardware and validation hardware, but cannot
> issue sign-off without feature-specific evidence.
>
> Any request that is not related to hardware (for example a BMC firmware-only
> ask with no hardware impact) must be **REJECTED** from this hardware PQRE
> workflow and routed through the appropriate non-hardware process.

### 10. Draft Questionnaire Responses

> ⚠️ **DRAFT — DO NOT SEND — Human approval required before any external communication.**

| Questionnaire Topic | Draft Response |
|---------------------|----------------|
| Reliability stress affecting Platform Hardware / Validation Hardware? | **Yes, potentially.** Any ANC feature request that changes platform hardware or validation hardware (for example power SKU, DDR channel count, DC-SCM hardware, connector, or board stack-up) must include a reliability-stress impact assessment and either a re-use justification or a supplemental / new stress plan. |
| Can existing data be referenced? | **TBD by delta analysis.** Prior platform data may be referenced only after a documented comparability review shows the ANC request remains within the previously qualified stress envelope. |
| Packing / drop impact | **TBD.** Mark this as applicable if the request changes chassis mass, heatsink mass, board form factor, packaging method, or validation hardware handling configuration. Otherwise provide evidence for `N/A`. |
| FA enablement | **Required for hardware items.** Provide failure analysis contact path, sample retention plan, and return-material/logistics flow for new ANC hardware features. Owner: `[TBD]`. |
| Regulatory readiness | **Not ready to claim.** RoHS / REACH and any applicable platform regulatory declarations must be attached before sign-off. Owner: `[TBD]`. |
| Requestor / team / owner identity fields | Use `[TBD]` where the form requires named owner, approver, or directory-backed identity data not present in the intake. Do not invent names. |
| BMC firmware-only request | **Reject from this hardware PQRE form.** If the request concerns firmware only and does not change platform hardware or validation hardware, route it to the appropriate firmware review path instead of PQRE hardware qualification. |

---

## 繁體中文（Traditional Chinese）

### 1. 執行摘要

本次受理通知 Anderson City（ANC）1S / 2S 的 PRD 視窗已開啟，並要求各團隊以表單提交新的平台硬體功能需求。此請求與 PQRE 相關，因其涉及 ANC 平台硬體資格驗證啟動，包括新增 DDR 通道、擴充 750 W / 1200 W 功耗 SKU、安全硬體整合，以及 DC-SCM 硬體變更等 COR 新功能。然而，郵件中未提供任何工程證據、逐項功能差異分析、負責人資訊或資格驗證計畫。因此，對於硬體相關項目，當前 PQRE 結論為 **HOLD**；若請求與平台硬體或驗證硬體無關（例如僅 BMC 韌體變更），則必須自本硬體 PQRE 流程中駁回。

### 2. 請求分類（Request Classification）

- **請求型態：** PRD 受理開啟通知，加上問卷 / 表單填寫指引
- **硬體範疇判定：** 混合型受理；平台硬體與驗證硬體項目屬於範疇內，但非硬體項目必須駁回或轉送其他流程
- **範疇內領域：** Thermal、SI / PDN、Mechanical、DFM、DFT、Material、Regulatory、Reliability
- **可能範疇外內容：** 不涉及硬體影響之 BMC 韌體-only 請求
- **風險等級：** High Risk（Low Confidence — 無量化工程資料）

### 3. 是否需要行動（Action Required）

**是。**

所有硬體相關功能需求都必須提交完整受理資料包，PQRE 才能提供可用於簽核的建議。另外，若同一份請求混合平台硬體項目與僅韌體項目，必須拆分處理。

### 4. 已知問題（Known Issues）

1. **目前只有 PRD 通知，未附技術證據。** 受理內容僅含公告與表單連結，沒有逐項功能差異資料、可靠度數據或資格驗證計畫。
2. **多個功能主題被綁在同一受理中。** 郵件同時提到 Caliptra、額外四個 DDR 通道、750 W / 1200 W 功耗 SKU，以及搭載 AST2700 的新 DC-SCM；這些變更可能影響不同 PQRE 領域，不應視為單一無差別項目。
3. **可靠度壓力影響尚未定義。** 尚未說明既有平台或驗證硬體壓力覆蓋是否仍適用於 ANC 差異。
4. **存在韌體 / 軟體相鄰範疇風險。** AST2700 的描述可能使申請者混入僅 BMC 韌體相關需求；若未連結到硬體變更，則不屬於此硬體 PQRE 路徑。

### 5. 未知風險（Unknown Risks）

- 額外 DDR 通道是否使 SI / PDN 負載、佈線複雜度或熱密度超出既有資格驗證邊界
- 750 W / 1200 W SKU 是否需要針對平台硬體或驗證硬體進行新的熱 / 降額 / 可靠度壓力覆蓋
- DC-SCM 機構、連接器或材料變更是否引入新的 DFM、DFT、衝擊或包裝風險
- 既有 DMR AP 或其他前代資料是否可在無補充壓力測試情況下複用至 ANC
- 送件表單是否會混入硬體與非硬體需求，導致路由與簽核混亂

### 6. 影響評估（Impact Assessment）

| 類別 | 當前影響評估 |
|------|--------------|
| 時程 | 在提交硬體功能差異與證據資料包之前，PQRE 簽核受阻 |
| 品質 | 若表單回覆不完整，可能掩蓋各功能項目的資格驗證缺口 |
| 可靠度 | 新功耗、記憶體與 DC-SCM 差異可能需要新的或補充性的壓力覆蓋 |
| 法規 / 材料 | 新硬體內容尚無法規與材料聲明 |
| 流程 / 路由 | 若硬體與非硬體需求未拆分，可能造成錯誤路由 |

### 7. 資訊缺口（Information Gaps）

| # | 缺失項目 | 領域 | Blocking |
|---|----------|------|----------|
| 1 | ANC 1S / 2S 各項送件之逐功能硬體差異清單 | 全域 | **Yes** |
| 2 | 各需求是否影響平台硬體或驗證硬體之判定 | Routing / Reliability | **Yes** |
| 3 | 750 W 與 1200 W SKU 的熱 / 功耗資料 | Thermal / Reliability | **Yes** |
| 4 | 四個新增 DDR 通道之 SI / PDN 證據 | SI / PDN | **Yes** |
| 5 | DC-SCM 硬體定義、介面與機構影響 | Mechanical / DFM / DFT | **Yes** |
| 6 | ANC 差異之可靠度壓力複用評估或新測試計畫 | Reliability | **Yes** |
| 7 | 新硬體內容之法規與材料聲明 | Regulatory / Material | **Yes** |
| 8 | 各表單提交所需之負責人、組織與日期欄位 | Program / Routing | No |

### 8. 必要行動（Required Actions）

1. 對每一項 ANC 硬體功能需求分別提交表單，或在同一表單中明確分段；不得將僅韌體需求混入 PQRE 硬體送件。
2. 對每個硬體項目說明其影響的平台硬體 / 驗證硬體範圍、設計差異及資格驗證目標。
3. 對任何改變既有操作邊界的功能提供熱、功耗、SI / PDN 與可靠度證據。
4. 若屬 DC-SCM 或板級功能變更，需附機構、DFM、DFT 與材料證據包。
5. 若某項目僅屬韌體（例如未牽涉硬體變更的 BMC 韌體），應自本硬體 PQRE 流程中駁回或轉送其他流程。
6. 在 PQRE 關閉前，補齊每一項送件的 owner、team 與 target date。
7. 表單定稿後，重新提交完整證據資料包以進行正式 PQRE 審查。

### 9. PQRE 建議（PQRE Recommendation）

> **HOLD — 已提供硬體受理指引；仍需證據資料包**
>
> ANC PRD 開啟通知與 PQRE 有關，但目前受理僅屬路由與問卷通知。PQRE 可支援平台硬體與驗證硬體之硬體相關表單送件，但在缺乏逐功能證據前，無法提供簽核。
>
> 任何與硬體無關之請求（例如未牽涉硬體影響的 BMC 韌體-only 請求）都必須在本硬體 PQRE 流程中 **REJECT**，並改由適當的非硬體流程處理。

### 10. 問卷回覆草稿（Draft Questionnaire Responses）

> ⚠️ **DRAFT — DO NOT SEND — Human approval required before any external communication.**

| 問卷主題 | 草稿回覆 |
|----------|----------|
| 是否影響 Platform Hardware / Validation Hardware 的可靠度壓力？ | **可能是。** 任何改變平台硬體或驗證硬體的 ANC 功能需求（例如功耗 SKU、DDR 通道數、DC-SCM 硬體、連接器或板層堆疊）都必須提供可靠度壓力影響評估，以及複用既有資料或進行補充 / 新測試的說明。 |
| 是否可引用既有資料？ | **待差異分析判定。** 只有在文件化可比性審查證明 ANC 需求仍位於既有已驗證壓力邊界內時，才可引用前代平台資料。 |
| Packing / drop 影響 | **TBD。** 若需求改變機箱重量、散熱器重量、板型、包裝方式或驗證硬體搬運配置，則應標示為適用；否則需提供 `N/A` 之依據。 |
| FA enablement | **硬體項目需要。** 請提供 failure analysis 聯絡窗口、樣品保留計畫，以及新 ANC 硬體功能之退料 / 物流流程。Owner：`[TBD]`。 |
| Regulatory readiness | **目前不可宣告 ready。** 簽核前必須附上 RoHS / REACH 及任何適用的平台法規聲明。Owner：`[TBD]`。 |
| Requestor / team / owner 身分欄位 | 若表單要求具名 owner、approver 或目錄型身分資料，而受理內容未提供，請填入 `[TBD]`，不得自行臆測姓名。 |
| 僅 BMC 韌體需求 | **自本硬體 PQRE 表單中駁回。** 若需求僅與韌體相關，且不影響平台硬體或驗證硬體，應改由適當的韌體審查流程處理，而非硬體 PQRE 資格驗證。 |
