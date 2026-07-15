# PQRE Risk Review — Issue #36

**Issue:** [AI Risk Review] WW29'2026 COR 8 CH CSF Meeting Minutes
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/36
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-15
**Requestor:** Shou-Chin Lee (DCAI Q&R — Boards & Systems)
**Meeting Date:** WW29.2'2026
**Platform:** COR 8 CH (Coral 8 Channel)

---

## 1. Executive Summary

This PQRE review was triggered by Issue #36, containing meeting minutes from the
WW29.2'2026 COR 8 CH CSF (Customer Support Forum) meeting for the Coral 8 Channel
deployment program. The minutes document the current deployment status, process
procedures, and five open action items for the deployment team.

The most critical risk identified is the **unreleased ERB socket design (C1 vs
Scrambled Socket issue)**: the production socket has not been released, directly
impacting board readiness and causing potential shipment delays across the program.
As a risk-mitigation measure, an elastomer solution has been made available exclusively
for PDT validation teams. Fulfillment for other demand categories is limited until the
production socket is released, received, and soldered onto boards. The meeting also
documents OOC submission procedures, demand collection windows (DVH boards WW28–WW30;
POB/PO WW30–WW32), and finance approval demand handling protocols.

**No quantified data** on impacted board count, socket release timeline, or elastomer
qualification scope was provided in the meeting minutes. The preliminary risk posture is
**Medium Risk — CONDITIONAL APPROVE**, with two blocking actions (socket release
timeline and impact quantification) required before full-rate deployment can proceed.

---

## 2. Request Classification

- **Domains in scope:** Mechanical, Manufacturing / DFM, Supplier Readiness, Regulatory
- **Domains out of scope:** Thermal, Derating, SI/PI/PDN, Reliability *(deployment
  readiness review — no thermal or electrical change content provided in minutes)*
- **Risk Tier:** Medium Risk (aggregate; see Risk Assessment)
- **Action Required:** Yes

---

## 3. Action Required

**Yes.** Two blocking actions (Actions 1–2 in Section 8) must be resolved to enable
full-rate fulfillment. PDT priority demand may proceed using the elastomer solution
as an interim measure. Non-PDT demand is on HOLD pending socket release.

---

## 4. Known Issues

1. **ERB socket design not released** — The production socket for COR 8 CH boards has
   not been released as of WW29.2'2026. Board assembly cannot be completed without the
   production socket. The elastomer solution provides a partial mitigation for PDT
   validation teams only.

2. **Shipment dates impacted** — For requests that cannot be fulfilled using the
   elastomer workaround, shipment dates are delayed pending socket release, receipt,
   and soldering.

3. **PDT priority creates fulfillment sequencing risk** — Fulfillment is explicitly
   sequenced with PDT priority demand first. Non-PDT teams face indefinite delay with
   no published recovery timeline.

4. **OOC cutoff constraint** — OOC submissions for ship-to contact, site, group, or
   priority changes are closed 6 weeks prior to shipment. Requesters unaware of this
   cutoff risk losing the ability to modify their orders.

5. **Inactive Requester / Ship-to Contact risk** — Personnel transitions (people leaving
   Intel) assigned to Requester, Ship-to Contact, or On Behalf Of roles may create
   fulfillment failures if OOC format is not submitted promptly.

6. **Unapproved demand not submitted to ODM** — Finance-unapproved demand is withheld
   from ODM submission. Rejected demand is removed from My Samples. Downstream schedule
   impact is not quantified in the minutes.

---

## 5. Unknown Risks

- **Socket release timeline unknown** — No target date for ERB socket design release
  was communicated in the meeting. Any delay beyond the WW30–WW32 POB/PO window
  further compresses fulfillment lead time.

- **Elastomer solution qualification scope** — The minutes state the elastomer solution
  is available only for PDT validation teams, but the qualification envelope
  (temperature, vibration, insertion cycles) is not documented. Failures outside the
  validated scope are possible.

- **Demand collection shortfall** — The DVH board demand window (WW28–WW30) may close
  before socket constraints are resolved, causing demand that cannot be accurately
  scoped.

- **Ordering Guide format change impact** — The Ordering Guide format is changing to
  match the 16 CH format per customer feedback. Teams unfamiliar with the new format
  may submit incorrect orders.

- **Finance rejection cascade** — If a significant volume of demand is rejected by
  finance, downstream ODM planning and material procurement timelines may be disrupted
  without a documented recovery process.

- **Export re-classification risk** — ECCN references are listed but specific
  classification status for all SKUs is not documented in the minutes.

---

## 6. Impact Assessment

| Category | Impact | Severity |
|----------|--------|----------|
| Positive — process clarity | OOC procedures, demand windows, and finance approval flow documented and communicated | Beneficial |
| Positive — risk mitigation | Elastomer solution enables PDT priority validation to proceed without waiting for production socket | Beneficial |
| Risk — fulfillment delay | Non-PDT demand delayed indefinitely pending socket release; shipment dates impacted | Significant |
| Risk — schedule compression | Socket delay during WW29 with POB/PO window opening WW30 leaves very little buffer for socket receipt, soldering, and fulfillment | Significant |
| Risk — demand inaccuracy | DVH demand window (WW28–WW30) may be collected without confirmed socket availability, creating mismatch between demand and supply | Moderate |
| Risk — order management | Inactive requesters and missed OOC cutoffs may cause fulfillment failures or misdirected shipments | Moderate |
| Risk — elastomer scope | Using elastomer beyond its validated scope (outside PDT teams) could introduce uncharacterised failure modes | Moderate |
| Risk — export compliance | ECCN references without confirmed classification status create regulatory uncertainty | Low |

---

## 7. Information Gaps

| # | Missing Item | Domain | Blocking |
|---|-------------|--------|----------|
| 1 | ERB socket design release date — target WW and confirmation path | Mechanical / Supplier Readiness | **Yes** |
| 2 | Quantified number of requests / boards impacted by socket delay, with customer-by-customer breakdown | Manufacturing / Supplier Readiness | **Yes** |
| 3 | Elastomer solution qualification report — validated temperature range, vibration spec, and insertion cycle limit | Mechanical | No |
| 4 | DVH board demand total collected as of WW29 vs. capacity plan | Manufacturing | No |
| 5 | Finance approval status for current demand — percentage approved / pending / rejected | Supplier Readiness | No |
| 6 | ECCN classification confirmation for all COR 8 CH SKUs | Regulatory | No |
| 7 | Recovery timeline for non-PDT demand once socket becomes available | Supplier Readiness | No |
| 8 | Ordering Guide version change communication plan to customers | Manufacturing | No |

---

## 8. Risk Assessment

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|--------|-------------|----------------|---------------|-----|-----------------|-----------|
| Mechanical (Socket readiness) | 4 | 3 | 2 | 24 | 2 — No socket release date or qualification data ¹ | **Medium** |
| Manufacturing / DFM (Board readiness) | 3 | 3 | 2 | 18 | 2 — No board count or timeline data ¹ | **Medium** |
| Supplier Readiness (Socket & fulfillment) | 4 | 3 | 2 | 24 | 2 — No lead time or availability data ¹ | **Medium** |
| Regulatory (ECCN / Export) | 2 | 1 | 2 | 4 | 4 — ECCNs referenced but not confirmed per SKU | **Low** |

**Scoring rationale:**

- **Mechanical S=4**: Unreleased socket design prevents board assembly. System
  fulfillment failure occurs under current conditions; elastomer provides partial
  mitigation for PDT only.
- **Mechanical O=3**: Socket design release is a known open issue with moderate
  occurrence of delay-causing design closures in pre-production hardware programs.
- **Mechanical D=2**: Deployment team is actively monitoring; issue is visible and
  tracked, reducing detection risk.

- **Manufacturing S=3**: Board readiness is impacted but elastomer workaround exists
  for PDT teams. Full production readiness blocked.
- **Manufacturing O=3**: Board readiness blockage is current and ongoing.
- **Manufacturing D=2**: Board status is visible to deployment team; detection is high.

- **Supplier Readiness S=4**: Socket not available means fulfillment cannot proceed
  for non-PDT demand; significant schedule impact.
- **Supplier Readiness O=3**: Known supply constraint with no confirmed resolution date.
- **Supplier Readiness D=2**: Issue is known and tracked; detection risk is low.

- **Regulatory S=2**: ECCN references present but per-SKU confirmation missing; risk
  is low given existing export compliance infrastructure.
- **Regulatory O=1**: Export classification failures are rare for established Intel
  hardware programs.
- **Regulatory D=2**: ECCN documentation process provides reasonable detection.

¹ **Low Confidence flag triggered** — Data Confidence ≤ 2 for Mechanical, Manufacturing,
  and Supplier Readiness domains. All three domains require elevated engineering review
  per `KnowledgeBase/risk_scoring_criteria.md`.

> **Note:** No individual domain RPN ≥ 51; however, three domains simultaneously at
> Medium Risk triggers aggregate High Risk treatment per escalation rules.
> Aggregate risk posture: **Medium–High** pending socket release data.

---

## 9. Required Actions

| # | Action | Owner | Due Date | Blocking |
|---|--------|-------|----------|----------|
| 1 | Obtain and communicate ERB socket design release target date; establish weekly tracking checkpoint with socket supplier and board readiness team | [TBD — assign before closure] | [TBD] | **Yes** |
| 2 | Quantify total number of requests / boards impacted by socket delay; publish impact list with PDT vs. non-PDT categorisation and revised shipment estimates | [TBD — assign before closure] | [TBD] | **Yes** |
| 3 | Obtain and document elastomer solution qualification report: temperature range, vibration spec, insertion cycle limit, and approved use scope | [TBD] | [TBD] | No |
| 4 | Communicate WW30–WW32 POB/PO demand window and updated Ordering Guide format to all customer groups before WW30 | [TBD] | Before WW30 | No |
| 5 | Audit all active Requester / Ship-to Contact / On Behalf Of assignments for personnel departing Intel; submit OOC formats before 6-week cutoff | [TBD] | Ongoing | No |
| 6 | Report finance approval demand status: total demand, approved count, pending count, and rejected count; develop recovery plan for rejected demand | [TBD] | [TBD] | No |
| 7 | Confirm ECCN classification for all COR 8 CH SKUs; attach confirmation to issue before shipment | [TBD] | Before shipment | No |
| 8 | Publish non-PDT demand recovery timeline with socket availability as gating milestone | [TBD] | Upon socket release date confirmation | No |

---

## 10. PQRE Recommendation

> **CONDITIONAL APPROVE**
>
> The COR 8 CH deployment program has well-documented procedures, a structured
> deployment team, and an active risk-mitigation measure (elastomer solution for PDT
> teams). The meeting minutes demonstrate active management of the program's open
> items.
>
> However, two blocking information gaps (Actions 1–2) must be resolved before
> full-rate deployment sign-off:
>
> - **Action 1** — ERB socket release date is required. Without a confirmed release
>   date, no accurate shipment commitment can be made for non-PDT demand.
> - **Action 2** — Quantified impact assessment is required. The number of affected
>   requests and revised shipment dates must be documented before the deployment team
>   can provide binding customer commitments.
>
> **PDT priority demand** using the elastomer solution may proceed immediately.
> **Non-PDT demand** is on HOLD pending socket release and Actions 1–2 closure.
>
> Low Confidence flags are active for Mechanical, Manufacturing, and Supplier Readiness
> domains. Elevated engineering review is required until socket qualification data is
> provided.

---

## 11. Bilingual Summary (繁體中文摘要)

### 執行摘要

本次 PQRE 審查由 Issue #36 觸發，內容為 WW29.2'2026 COR 8 CH CSF（客戶支援論壇）
會議紀錄，涵蓋 Coral 8 Channel 部署計畫的現況、作業程序及五項未解決的行動項目。

本次會議紀錄所識別之最重要風險為 **ERB 插座設計尚未發布（C1 vs. Scrambled Socket
議題）**：量產插座設計至今未完成，直接影響電路板備料進度，並導致部分出貨日期延誤。
作為風險緩解措施，彈性體（elastomer）解決方案目前僅開放給 PDT 驗證團隊使用；在量產
插座完成發布、接收並焊接至電路板之前，非 PDT 需求的履行將受到嚴格限制。

會議亦記錄了以下程序要項：OOC（Out of Class）提交流程、需求蒐集時間窗口
（DVH 板：WW28–WW30；POB/PO：WW30–WW32），以及財務核准需求的處理規則。

會議紀錄中**未提供**受影響電路板數量、插座發布時程或彈性體解決方案資格認證範圍等量化
資料。初步風險評估為**中風險 — 有條件核准（CONDITIONAL APPROVE）**，
需完成兩項封鎖性行動（插座發布時程確認與影響量化）後，方可進行全速部署。

### PQRE 建議

> **有條件核准（CONDITIONAL APPROVE）**
>
> COR 8 CH 部署計畫具備完善的作業程序、結構化的部署團隊，以及主動的風險緩解措施
>（PDT 團隊可使用彈性體解決方案）。會議紀錄顯示部署團隊正積極管理各項未解決議題。
>
> 然而，以下兩項封鎖性資訊缺口（行動 1–2）須完成後，方可核發全速部署簽核：
>
> - **行動 1** — 必須確認 ERB 插座發布目標時程。若無確認的發布日期，
>   將無法對非 PDT 需求提供準確的出貨承諾。
> - **行動 2** — 必須完成量化影響評估。受影響的需求數量及修訂後的出貨日期
>   須完整記錄，方能向客戶提供具約束力的承諾。
>
> **PDT 優先需求** 可立即使用彈性體解決方案繼續推進。
> **非 PDT 需求** 處於暫停（HOLD）狀態，等待插座發布及行動 1–2 完成後方可繼續。
>
> 機械、製造及供應商就緒性三個領域的「低可信度」標記已觸發，
> 在提供插座資格認證資料之前，需進行升級工程審查。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external
> communication based on this review.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-15.
This review is an advisory output. Final engineering decisions require human sign-off.*
