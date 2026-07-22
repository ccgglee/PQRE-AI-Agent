# PQRE Risk Review — Issue #152

**Issue:** 5 ways to get MTBF
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/152
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-22
**Requestor:** ccgglee
**Platform:** PVC / JNC RP / Dunlow RP MTBF guidance for RP boards
**Agent Instruction:** How to reply to: "Is there any BKM for MTBF calculation for the RP boards that you can point me to? Also can you please confirm if this is done by the Intel board design team or something that is delivered by the ODM."

---

## English

### Executive Summary

This issue asks for a reply regarding **MTBF calculation BKM and ownership for
RP boards**. The visible issue body provides four explicit MTBF input paths:
ODM RD (PVC), real RMA data (JNC RP), reliability data, and BOM DPPM data
(Dunlow RP). The repository also confirms that MTBF/FIT evidence is a required
reliability sign-off input and that the Intel Rule reference base includes the
folders `FOQM/For PVC product` and `Lab and ODM requirement`. Based on the
available evidence, the safest answer is that there is **reference material /
BKM source content**, but not a single local standalone MTBF procedure in this
repo; and the MTBF package is **not solely an Intel board design deliverable**.
It should be treated as a joint flow where ODM prediction inputs are combined
with Intel review and sign-off judgement.

### Known Issues

1. The issue title says **"5 ways to get MTBF"**, but the visible issue body
   lists only **four** explicit MTBF input paths.
2. The referenced attachments are not present in the repository, so only their
   filenames can be cited; their internal formulas and assumptions are not
   directly verifiable here.
3. The repository currently exposes **reference folders** for MTBF-related
   knowledge, not one local self-contained MTBF-calculation BKM document.
4. Prior RP data re-use for a new platform is not automatic; existing repo
   guidance already requires a formal design-delta / comparability check.

### Gap Analysis

| Domain | Current Gap | Evidence Missing | Impact |
|---|---|---|---|
| Reliability method | No single local MTBF procedure is stored in the repo | Attachment contents / actual worksheet or formula package | Medium |
| Ownership | No explicit MTBF RACI is written in the issue body | Named owner for prediction creation, review, and approval | Medium |
| Reuse logic | JNC RP / Dunlow RP applicability is not formally bounded in the issue | Design-delta assessment for platform comparability | High |
| Traceability | BKM source exists as reference paths, not as a summarized local note | Consolidated guidance note for future replies | Low |

### Action Items

1. Use `KnowledgeBase/Rules/rp_board_mtbf_guidance.md` as the local reply
   baseline for future MTBF questions on RP boards.
2. Point requestors to the Intel Rule reference paths already indexed in the
   repository:
   - `FOQM/For PVC product`
   - `Lab and ODM requirement`
3. When prior RP data (for example JNC or Dunlow) is cited, require a formal
   comparability / design-delta check before claiming the old MTBF basis is
   reusable for a new RP.
4. Keep external communication in **draft only** form until a human reviewer
   approves the wording and audience.

### Risk Assessment

| Parameter | Score | Rationale |
|---|---:|---|
| Severity | 2 | This is a guidance / ownership clarification question, not a product escape by itself |
| Occurrence | 3 | MTBF ownership confusion can recur across RP programs |
| Detection | 2 | The gap is visible during review because the repo lacked one consolidated note |
| **RPN** | **12** | **Low Risk** |
| Data Confidence | 3 | The issue gives four explicit paths and the repository gives indexed reference folders; attachment details remain unavailable |

**Risk Band:** **Low Risk** (RPN = 12)  
**Disposition:** **CONDITIONAL APPROVE** for using the draft reply below, because
attachment contents and any program-specific ownership contract still require
human confirmation.

### Recommendation

**Draft reply (English):**

> Yes — there is BKM/reference material for MTBF work, but in the current
> repository it is represented as source folders rather than one standalone
> local MTBF procedure. The best starting points I can point you to are the
> Intel Rule references **`FOQM/For PVC product`** and
> **`Lab and ODM requirement`**.
>
> For RP boards, MTBF is normally built from several evidence paths: **(1) ODM
> RD prediction (PVC), (2) real RMA data from earlier RP boards such as JNC,
> (3) qualification / reliability data, and (4) BOM-based DPPM prediction such
> as the Dunlow RP example**.
>
> Based on the available evidence, this is **not purely an Intel board design
> team deliverable**. The **ODM typically prepares the prediction inputs /
> first-pass calculation**, while **Intel board design and PQRE review the
> assumptions, decide whether older RP data is reusable, and accept the final
> basis for sign-off**.

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

## 繁體中文（Traditional Chinese）

### Executive Summary（執行摘要）

本議題是在詢問 **RP board 的 MTBF 計算 BKM 與責任歸屬**。Issue 內文可確認
四個明確的 MTBF 輸入來源：ODM RD（PVC）、真實 RMA 資料（JNC RP）、
reliability data，以及 BOM 的 DPPM 資料（Dunlow RP）。Repository 也可確認
MTBF / FIT 證據屬於可靠度簽核所需項目，且 Intel Rule 參考路徑中已有
`FOQM/For PVC product` 與 `Lab and ODM requirement` 兩個可指向的來源。
因此，最安全的回覆方式是：**有可參考的 BKM / reference source，但此 repo
內沒有單一獨立的本地 MTBF 計算程序**；同時，這件事**不是單純由 Intel board
design team 獨立完成**，而是 ODM 提供預估輸入，再由 Intel 端進行審查與簽核判斷。

### Known Issues（已知問題）

1. Issue 標題寫的是 **「5 ways to get MTBF」**，但可見內文只列出 **4 個**
   明確來源。
2. 相關附件未存於 repository 中，因此目前只能引用檔名，無法直接驗證其內部
   計算公式與假設。
3. Repository 目前提供的是 **參考資料夾路徑**，而不是單一份本地 MTBF 計算
   BKM 文件。
4. 舊 RP 資料是否可重用於新平台並非自動成立；repo 既有指引已要求必須先做
   設計差異 / 可比性評估。

### Gap Analysis（缺口分析）

| 領域 | 目前缺口 | 缺失證據 | 影響 |
|---|---|---|---|
| Reliability method | repo 內沒有單一本地 MTBF 程序 | 附件內容 / 真正的 worksheet 或公式包 | 中 |
| Ownership | issue 內沒有明寫 MTBF RACI | 建模、審查、核准的具名 owner | 中 |
| Reuse logic | issue 未正式界定 JNC RP / Dunlow RP 的適用邊界 | 平台可比性的設計差異分析 | 高 |
| Traceability | BKM 來源存在，但先前未整理成單一本地摘要 | 可供後續直接引用的整理說明 | 低 |

### Action Items（行動項目）

1. 後續遇到 RP board 的 MTBF 問題時，以
   `KnowledgeBase/Rules/rp_board_mtbf_guidance.md` 作為本地回覆基線。
2. 將需求方導向 repository 已索引的 Intel Rule 參考路徑：
   - `FOQM/For PVC product`
   - `Lab and ODM requirement`
3. 若引用既有 RP 資料（例如 JNC 或 Dunlow），必須先完成正式的可比性 /
   設計差異評估，才能主張舊 MTBF 基礎可套用到新 RP。
4. 對外溝通內容僅可維持 **draft only**，需經人工審核後才可發送。

### Risk Assessment（風險評估）

| 參數 | 分數 | 說明 |
|---|---:|---|
| Severity | 2 | 此題屬於回覆方式與責任歸屬釐清，並非直接產品逸失 |
| Occurrence | 3 | RP 專案間常見 MTBF ownership 混淆 |
| Detection | 2 | repo 缺少整合說明時，審查過程中可被發現 |
| **RPN** | **12** | **低風險** |
| Data Confidence | 3 | issue 已給四個明確來源，repo 也有索引參考路徑，但附件細節仍不可見 |

**Risk Band：** **低風險**（RPN = 12）  
**Disposition：** 針對下方 draft reply，建議 **CONDITIONAL APPROVE**；
附件內容與專案別 ownership 契約仍需人工再次確認。

### Recommendation（建議）

**Draft reply（繁體中文）:**

> 有，MTBF 相關的 BKM / reference material 是有的，但在目前這個 repo
> 裡呈現的是 **source folder / reference path**，而不是單一份獨立的本地
> MTBF procedure。你可以先從 Intel Rule 參考路徑
> **`FOQM/For PVC product`** 與 **`Lab and ODM requirement`** 開始找。
>
> 對 RP boards 而言，MTBF 通常是由多個依據組成：**(1) ODM RD 預估（PVC）、
> (2) 舊 RP 如 JNC 的真實 RMA 資料、(3) qualification / reliability data、
> (4) BOM-based DPPM prediction，例如 Dunlow RP 的做法**。
>
> 依目前證據判斷，這**不是單純由 Intel board design team 獨立交付**的項目。
> 一般會由 **ODM 先準備 prediction inputs / first-pass calculation**，再由
> **Intel board design 與 PQRE 審查假設、判定舊 RP 資料是否可重用，並接受最終
> 的 sign-off basis**。

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-22. Closes #152.*
