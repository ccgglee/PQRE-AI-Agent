# PQRE Risk Review — Issue #161

**Issue:** [AI Risk Review] RE: RP Qualification criteria
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/161
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-23
**Requestor:** ccgglee
**Platform:** Johnson City (JNC1 / JNC2) — DMR AP Reference Platform; Navarre City RP
**Agent Instruction:** 我該如何回信？ (How should I reply to this email thread?)

---

## Knowledge Retrieval Log

| Source | Retrieved |
|---|---|
| `platform_alias.yaml` | Johnson City → JNC1/JNC2, DMR AP RP ✓ |
| `jnc_reliability_stress.md` | JNC TC upper dwell 100 °C; 325 / 525 cycle milestones ✓ |
| `pqre_signoff_criteria.md` | Reliability: Component MTBF/FIT at new conditions (blocking) ✓ |
| `risk_scoring_criteria.md` | RPN scale, Data Confidence scale ✓ |
| `intel_rule_taxonomy.yaml` | Reliability domain — Derating, FOQM applicable ✓ |
| `reviews/issue-163-pqre-review.md` | JNC1/JNC2 TC stress data captured ✓ |

---

## English

### 1. Executive Summary

This issue captures an active email thread titled **"RE: RP Qualification criteria"**
between Juan Orozco, Juan Zermeno (Carriedo), and Luis Murillo (Intel DCAI / DHE)
regarding Temperature Cycle (TC) qualification standards and test status for the
**Johnson City (JNC) DMR AP Reference Platform** and the upcoming **Navarre City RP**.

Key technical disclosures in the email thread:

- Juan Zermeno confirmed that **Navarre City RP** falls under the **Reference Design**
  qualification tier and its qualification plan includes **1000 TC-K cycles
  (0 °C to 125 °C)** for Solder Joint Reliability (SJR) and board component
  robustness assessment.
- For **DMR-RS** specifically: because it will **not** be soldered down in Navarre
  City, Zermeno plans to leverage ETB (Engineering Test Board) TC data collected by
  APTM QREs as part of the tech-cert process, supplemented by a **small sample-size
  run** covering medium- and high-risk board components. If the program decides to
  solder down DMR-RS in Navarre City, increased sample sizes and a full SoC SJR
  evaluation would be required.
- Zermeno noted that the typical TC condition for **Xeon products** is
  **TC-T (-40 °C to 100 °C, 1000 cycles)**.

**Juan Orozco's open question (requiring a reply):**
1. Is the **Johnson City Board TC-T testing done already**?
2. Were/are TC qualification tests tied to **specific program milestones**, and if so,
   at which milestones — **program level or SXT level**?

From the repository KnowledgeBase (`jnc_reliability_stress.md`, Issue #163):
JNC1/JNC2 **did complete TC testing** with an upper dwell of **100 °C** and milestone
cycle targets of **325 cycles** (3-year field life) and **525 cycles** (5-year field
life). However, the lower dwell temperature and the exact JEDEC TC profile
classification (TC-T vs. TC-K) for JNC are **not confirmed** in the KnowledgeBase.
The JNC cycle counts (325 / 525) also differ from the 1000-cycle target stated for
Navarre City.

**Risk Band:** **Low Risk** (RPN = 8) — This is a qualification status inquiry, not
a product escape or active field failure.

---

### 2. Request Classification

| Field | Value |
|---|---|
| Request type | Technical Q&A — qualification status inquiry and reply guidance |
| Platform (primary) | Johnson City (JNC1 / JNC2) — DMR AP Reference Platform |
| Platform (secondary) | Navarre City RP (Reference Design tier) |
| CPU / SoC | DMR AP (JNC); DMR-RS (Navarre City) |
| Domain in scope | Reliability — Temperature Cycle (TC) / Solder Joint Reliability (SJR) |
| Domains not in scope | Thermal, SI, PDN, Mechanical, DFM, DFT, Material, Regulatory |
| Evidence level | Partial — JNC TC data captured in KnowledgeBase; program milestone mapping absent |
| Action Required | **Yes** |

---

### 3. Action Required

**Yes.**

A draft reply is required to address Juan Orozco's two open questions:
(a) JNC Board TC-T completion status, and (b) program milestone alignment
(program level vs. SXT level).

---

### 4. Known Issues

1. **JNC TC profile not fully specified in KnowledgeBase**: The KnowledgeBase
   (`jnc_reliability_stress.md`) confirms an upper dwell of 100 °C and cycle
   counts of 325 and 525, but the **lower dwell temperature** (which determines
   the JEDEC TC-K vs. TC-T classification) is not recorded. TC-T is −40 °C to
   100 °C (ΔT = 140 °C); if JNC used TC-K (0 °C to 100 °C, ΔT = 100 °C), the
   two profiles are not equivalent.

2. **JNC cycle count differs from Navarre City**: JNC milestones are 325 and 525
   cycles, while Navarre City is planned at 1000 cycles. Direct reuse of JNC TC
   data for Navarre City requires a formal design-delta and profile
   comparability assessment.

3. **Qualification criterion image missing**: Zermeno's original email included an
   image showing three different RP qualification tiers, but the image is not
   viewable in the GitHub issue. The specific criteria that differentiate the
   three tiers (e.g., "Reference Design", "Board Ingredient", and a third tier)
   are therefore not confirmed from the issue content alone.

4. **TC-K vs. TC-T for Navarre City / DMR-RS**: Zermeno stated Navarre City uses
   TC-K (0 °C to 125 °C), whereas the typical Xeon TC condition is TC-T
   (−40 °C to 100 °C). The rationale for the TC-K selection for Navarre City
   (aligned to Nimbus) should be documented to avoid future confusion.

---

### 5. Unknown Risks

1. **Lower dwell temperature for JNC TC**: If JNC used TC-T (−40 °C lower dwell),
   the thermal excursion ΔT = 140 °C exceeds TC-K's ΔT = 125 °C, making JNC data
   more conservative and potentially reusable for Navarre City. Conversely, if JNC
   used TC-K (0 °C lower dwell), the comparability basis changes significantly.

2. **Program milestone alignment**: The specific Intel RP qualification milestones
   at which JNC TC was conducted (e.g., ES1/ES2 early-life qualification, QS
   qualification sample, PRQ product readiness) are not recorded in the
   KnowledgeBase. If TC tests were gated at a different milestone than expected,
   timing gaps may exist.

3. **SXT-level vs. board-level qualification scope**: "SXT level" likely refers
   to SoC- or silicon-level qualification conducted by APTM QREs (the ETB-based
   tech-cert process mentioned by Zermeno). If the questioner (Orozco) is asking
   whether the board-level TC was separately triggered at a program milestone
   beyond what APTM QREs cover, this distinction needs to be clarified in the reply.

4. **ETB-to-RP data transferability**: Zermeno's plan to leverage ETB TC data
   for Navarre City board components has not been formally reviewed. ETB and RP
   board construction, BOM, and stack-up may differ, affecting solder joint
   thermal fatigue accumulation.

---

### 6. Impact Assessment

| Scenario | Impact | Severity |
|---|---|---|
| JNC TC-T completed at 100 °C, 525 cycles | Low — data exists; comparability assessment needed for Navarre City | Low |
| JNC TC lower dwell = 0 °C (TC-K, not TC-T) | Medium — ΔT difference (125 °C vs. 140 °C) affects equivalency claim | Medium |
| JNC TC milestones do not cover 1000 cycles | Low — milestone counts differ, but test objective may still be met | Low |
| ETB TC data not acceptable as RP qualification basis | High — Navarre City would require new RP-level TC campaign | High |
| Program decides DMR-RS soldered down in Navarre City | High — requires full SJR qualification, larger sample size | High |

---

### 7. Information Gaps

| Gap | Evidence Missing | Priority |
|---|---|---|
| JNC TC lower dwell temperature (TC-T vs. TC-K classification) | Full JNC1/JNC2 TC test report or Shou-chin confirmation | High |
| JNC TC program milestone alignment (when test was triggered) | Program qualification schedule for JNC | Medium |
| Definition and scope of "SXT level" qualification in the requestor's context | Clarification from Juan Orozco or program team | Medium |
| Three-tier RP qualification criteria image (attached to Zermeno's original email) | Accessible version of the qualification criteria table | Medium |
| ETB-to-RP design-delta assessment for Navarre City TC data reuse | Formal comparability study (ETB vs. RP BOM, stack-up, thermal load) | High |
| Rationale for TC-K selection in Navarre City (vs. typical TC-T) | Qualification basis document citing Nimbus alignment | Low |

---

### 8. Required Actions

1. **Confirm JNC TC profile with Shou-chin or APTM QRE team**: Request the JNC1/JNC2
   TC test reports to confirm (a) lower dwell temperature, (b) JEDEC profile
   classification (TC-T vs. TC-K), and (c) the specific program milestone at which
   the test was conducted.

2. **Clarify "SXT level" definition for the program**: Confirm whether Juan Orozco's
   question about "SXT level" refers to the SoC/silicon-level qualification run by
   APTM QREs (ETB-based tech-cert process) or a distinct board-level qualification
   gate.

3. **Assess ETB-to-RP data transferability**: Before formally accepting ETB TC data
   as qualifying evidence for Navarre City board components, require a written
   design-delta comparison (ETB vs. Navarre City RP — BOM, PCB stack-up, solder
   alloy, component placement).

4. **Document TC-K selection rationale for Navarre City**: Record why TC-K
   (0 °C to 125 °C) was chosen for Navarre City RP instead of TC-T (−40 °C to
   100 °C), and confirm alignment with Nimbus qualification baseline documents.

5. **Update KnowledgeBase**: Once JNC TC-T report is confirmed and lower dwell
   temperature is verified, update `KnowledgeBase/platform/jnc_reliability_stress.md`
   with the complete TC profile.

6. **All external communications must remain DRAFT** until reviewed and approved
   by a human PQRE engineer.

---

### 9. PQRE Recommendation

#### Risk Assessment

| Parameter | Score | Rationale |
|---|---:|---|
| Severity | 2 | Qualification status inquiry — no confirmed product escape or active field failure |
| Occurrence | 2 | JNC is a mature platform; TC data exists in some form |
| Detection | 2 | Evidence gaps are visible and flagged; not hidden |
| **RPN** | **8** | **Low Risk** |
| Data Confidence | 3 | JNC TC upper dwell and cycle counts confirmed; lower dwell / profile type and milestone mapping absent |

**Risk Band:** **Low Risk** (RPN = 8)
**Disposition:** **CONDITIONAL APPROVE** for using the draft reply below, pending
human confirmation of the JNC TC test report details and program milestone
alignment by Shou-chin or the APTM QRE team.

---

#### Draft Reply (English)

> **DRAFT — DO NOT SEND without human review and approval**

> Hi Juan [Orozco],
>
> Thanks for following up. Here is what we can confirm from available records,
> along with a few open items to resolve:
>
> **1. Johnson City Board TC status:**
>
> JNC1/JNC2 (Johnson City DMR AP RP) did complete Temperature Cycle testing.
> The upper dwell temperature was **100 °C**, consistent with the TC-T range
> (−40 °C to 100 °C, ΔT = 140 °C). Board-level qualification milestones covered
> **325 cycles** (supporting a 3-year field life) and **525 cycles** (supporting
> a 5-year field life). Both were run unpowered.
>
> To confirm whether the full TC-T profile (including the −40 °C lower dwell)
> was applied vs. a TC-K-like condition (0 °C lower dwell), please reach out to
> Shou-chin or the APTM QRE team and request the JNC1/JNC2 TC test reports.
>
> **2. Program level vs. SXT level:**
>
> The JNC board-level TC was conducted as part of **RP-level (board/program)
> qualification** — separate from the SoC/silicon-level (SXT) qualification
> managed by APTM QREs. As Juan Zermeno noted, for Navarre City, the SoC-level
> data from ETBs (tech-cert process) will serve as background evidence, while a
> separate small-sample board run covers medium- and high-risk board components.
>
> So the short answer is: **both levels apply** — SXT-level runs under the
> APTM QRE tech-cert process; board/program-level (RP-level) TC runs under
> the RP qualification plan, gated to program milestones (typically Quality
> Sample / PRQ gates, but please confirm with Juan Zermeno which gates apply
> to Navarre City's Reference Design plan).
>
> **3. Note on TC-K vs. TC-T for Navarre City:**
>
> Navarre City RP is planned at **1000 TC-K cycles (0 °C to 125 °C)**, whereas
> the typical Xeon condition is TC-T (−40 °C to 100 °C). If you need to compare
> Navarre data with JNC, or reuse JNC TC data for Navarre qualification credit,
> a design-delta and thermal-comparability assessment is required.
>
> Please let me know if you need the JNC test reports pulled — I will follow up
> with Shou-chin.
>
> Best regards

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

## 繁體中文（Traditional Chinese）

### 1. Executive Summary（執行摘要）

本議題擷取了一封主旨為 **「RE: RP Qualification criteria」** 的郵件往來記錄，
往來人員為 Juan Orozco、Juan Zermeno（Carriedo）及 Luis Murillo（Intel DCAI / DHE），
討論主題為 **Johnson City（JNC）DMR AP Reference Platform** 與即將推出的
**Navarre City RP** 的溫度循環（TC）資格驗證標準與測試狀態。

郵件中的關鍵技術揭露：

- Juan Zermeno 確認 **Navarre City RP** 屬於 **Reference Design** 資格驗證層級，
  其資格驗證計畫包括 **1000 TC-K cycles（0 °C 至 125 °C）**，用於評估
  焊點可靠度（SJR）及板級元件穩健性。
- 針對 **DMR-RS**：由於 Navarre City 中 DMR-RS **不會焊接**，Zermeno 計畫
  利用 APTM QRE 在技術認證流程中以 ETB 收集的 TC 資料，並對中高風險板級元件
  執行**小樣本量測試**。若程式決定在 Navarre City 中焊接 DMR-RS，則需增加
  樣本數並進行完整的 SoC SJR 評估。
- Zermeno 指出，**Xeon 產品**的典型 TC 條件為 **TC-T（−40 °C 至 100 °C，
  1000 cycles）**。

**Juan Orozco 的未解問題（需回覆）：**
1. **Johnson City Board 的 TC-T 測試是否已完成？**
2. TC 資格驗證測試是否與**特定程式里程碑**綁定？若是，屬於**程式層級**
   還是 **SXT 層級**的里程碑？

根據 Repository KnowledgeBase（`jnc_reliability_stress.md`，Issue #163）：
JNC1/JNC2 **已完成 TC 測試**，上限溫度為 **100 °C**，里程碑循環次數為
**325 cycles**（對應 3 年現場壽命）及 **525 cycles**（對應 5 年現場壽命）。
然而，JNC 的下限溫度及精確的 JEDEC TC 規格分類（TC-T 或 TC-K）**尚未在
KnowledgeBase 中確認**。JNC 的循環次數（325 / 525）亦與 Navarre City 規劃的
1000 cycles 不同。

**Risk Band：低風險**（RPN = 8）— 本議題為資格驗證狀態詢問，並非產品逸失或
現場失效事件。

---

### 2. Request Classification（請求分類）

| 欄位 | 內容 |
|---|---|
| 請求類型 | 技術問答 — 資格驗證狀態詢問與回信指引 |
| 主要平台 | Johnson City（JNC1 / JNC2）— DMR AP Reference Platform |
| 次要平台 | Navarre City RP（Reference Design 層級） |
| CPU / SoC | DMR AP（JNC）；DMR-RS（Navarre City） |
| 範疇領域 | Reliability — 溫度循環（TC）/ 焊點可靠度（SJR） |
| 不在範疇內的領域 | Thermal、SI、PDN、Mechanical、DFM、DFT、Material、Regulatory |
| 證據層級 | 部分確認 — JNC TC 資料已存入 KnowledgeBase；程式里程碑對應尚缺 |
| 是否需要行動 | **是** |

---

### 3. Action Required（是否需要行動）

**是。**

需要起草一封回覆，解答 Juan Orozco 的兩個未解問題：
(a) JNC Board TC-T 完成狀態，及 (b) 程式里程碑對應（程式層級 vs. SXT 層級）。

---

### 4. Known Issues（已知問題）

1. **KnowledgeBase 中未記錄 JNC TC 完整規格**：`jnc_reliability_stress.md` 確認
   上限溫度為 100 °C 且循環次數為 325 / 525，但 **下限溫度**（決定 JEDEC
   TC-K 或 TC-T 分類的關鍵參數）未記錄。TC-T 為 −40 °C 至 100 °C
   （ΔT = 140 °C）；若 JNC 採用 TC-K（0 °C 至 100 °C，ΔT = 100 °C），
   兩種規格並不等效。

2. **JNC 循環次數與 Navarre City 不同**：JNC 里程碑為 325 和 525 cycles，而
   Navarre City 規劃為 1000 cycles。若要將 JNC TC 資料套用至 Navarre City，
   需要正式的設計差異與規格可比性評估。

3. **資格驗證等級圖表不可見**：Zermeno 原始郵件中含有一張比較三種 RP
   資格驗證層級的圖表，但在 GitHub Issue 中無法檢視。三種層級的具體差異
   因此無法從議題內容中確認。

4. **Navarre City / DMR-RS 使用 TC-K 而非 TC-T**：Zermeno 表示 Navarre City
   採用 TC-K（0 °C 至 125 °C），而 Xeon 產品典型條件為 TC-T（−40 °C 至
   100 °C）。選用 TC-K 的理由（對齊 Nimbus）應予文件化，以免未來產生混淆。

---

### 5. Unknown Risks（未知風險）

1. **JNC TC 下限溫度**：若 JNC 採用 TC-T（−40 °C 下限），則 ΔT = 140 °C
   大於 TC-K 的 ΔT = 125 °C，使 JNC 資料更保守，理論上更容易作為
   Navarre City 的引用依據。反之，若 JNC 採用 TC-K（0 °C 下限），
   可比性基礎則有顯著不同。

2. **程式里程碑對應不明確**：JNC TC 在哪個 Intel RP 資格驗證里程碑
   （例如 ES1/ES2 早期資格、QS Qualification Sample、PRQ 產品就緒資格）
   執行，KnowledgeBase 中並無記錄。若測試在與預期不同的里程碑觸發，
   可能存在時間缺口。

3. **SXT 層級 vs. 板級資格驗證範疇**：「SXT 層級」可能指 APTM QRE 執行的
   SoC / 矽晶層級資格驗證（ETB 技術認證流程）。若 Orozco 的問題是在
   詢問板級 TC 是否在 APTM QRE 涵蓋範圍之外另設程式里程碑，需在回覆中
   釐清這項區別。

4. **ETB 資料遷移至 RP 的可適用性**：Zermeno 計畫將 ETB TC 資料用於
   Navarre City 板級元件的資格驗證，但此方案尚未經過正式審查。ETB 與
   RP 板的構造、BOM 及疊層可能不同，影響焊點熱疲勞的累積行為。

---

### 6. Impact Assessment（影響評估）

| 情境 | 影響 | 嚴重程度 |
|---|---|---|
| JNC TC-T 於 100 °C / 525 cycles 已完成 | 低 — 資料存在；Navarre City 需要可比性評估 | 低 |
| JNC TC 下限溫度 = 0 °C（TC-K，非 TC-T） | 中 — ΔT 差異影響等效性主張 | 中 |
| JNC TC 里程碑未達 1000 cycles | 低 — 里程碑次數不同，但測試目標仍可能達成 | 低 |
| ETB TC 資料不被接受為 RP 資格驗證依據 | 高 — Navarre City 需重新執行 RP 層級 TC | 高 |
| 程式決定在 Navarre City 焊接 DMR-RS | 高 — 需完整 SJR 資格驗證、增加樣本數 | 高 |

---

### 7. Information Gaps（資訊缺口）

| 缺口 | 缺失證據 | 優先順序 |
|---|---|---|
| JNC TC 下限溫度（TC-T vs. TC-K 分類） | JNC1/JNC2 完整 TC 測試報告或 Shou-chin 確認 | 高 |
| JNC TC 程式里程碑對應（測試在何時觸發） | JNC 資格驗證時程表 | 中 |
| 詢問者語境中「SXT 層級」的定義與範疇 | Juan Orozco 或程式團隊的釐清 | 中 |
| 三種 RP 資格驗證層級圖表（Zermeno 原始郵件附件） | 可讀版本的資格驗證標準表 | 中 |
| Navarre City TC 資料重用的 ETB-to-RP 設計差異評估 | 正式可比性研究（ETB vs. RP BOM、疊層、熱負載） | 高 |
| Navarre City 選用 TC-K 而非 TC-T 的理由 | 引用 Nimbus 對齊的資格驗證基準文件 | 低 |

---

### 8. Required Actions（必要行動）

1. **向 Shou-chin 或 APTM QRE 團隊確認 JNC TC 規格**：索取 JNC1/JNC2 TC
   測試報告，確認 (a) 下限溫度、(b) JEDEC 規格分類（TC-T vs. TC-K），
   及 (c) 測試執行時的程式里程碑。

2. **釐清程式對「SXT 層級」的定義**：確認 Orozco 詢問的「SXT 層級」是否
   指 APTM QRE 執行的 SoC / 矽晶層級資格驗證（ETB 技術認證流程），
   或是有別於此的板級資格驗證閘門。

3. **評估 ETB 資料遷移至 RP 的可適用性**：在正式接受 ETB TC 資料作為
   Navarre City 板級元件資格驗證依據前，需提交書面設計差異比較
   （ETB vs. Navarre City RP — BOM、PCB 疊層、錫膏合金、元件佈局）。

4. **文件化 Navarre City 選用 TC-K 的理由**：記錄為何採用 TC-K
   （0 °C 至 125 °C）而非 TC-T（−40 °C 至 100 °C），並確認與 Nimbus
   資格驗證基準文件的對齊情況。

5. **更新 KnowledgeBase**：JNC TC-T 報告確認後，將完整 TC 規格（含下限溫度）
   更新至 `KnowledgeBase/platform/jnc_reliability_stress.md`。

6. **所有對外溝通僅可維持 draft only 狀態**，需經人工 PQRE 工程師審核後
   方可發送。

---

### 9. PQRE Recommendation（PQRE 建議）

#### Risk Assessment（風險評估）

| 參數 | 分數 | 說明 |
|---|---:|---|
| Severity | 2 | 資格驗證狀態詢問 — 無確認的產品逸失或現場失效事件 |
| Occurrence | 2 | JNC 為成熟平台；TC 資料某種形式已存在 |
| Detection | 2 | 證據缺口已清楚標示；非隱性風險 |
| **RPN** | **8** | **低風險** |
| Data Confidence | 3 | JNC TC 上限溫度與循環次數已確認；下限溫度 / 規格分類及里程碑對應尚缺 |

**Risk Band：低風險**（RPN = 8）
**Disposition：CONDITIONAL APPROVE** — 同意使用以下 draft 回信，但需經
Shou-chin 或 APTM QRE 團隊確認 JNC TC 測試報告細節及程式里程碑對應後，
方可由人工審核者核准發送。

---

#### Draft Reply（繁體中文）

> **DRAFT — 未經人工審核核准，請勿發送**

> Hi Juan [Orozco]，
>
> 感謝你的追蹤。以下是目前可確認的資訊，以及仍需釐清的項目：
>
> **1. Johnson City Board TC 狀態：**
>
> JNC1/JNC2（Johnson City DMR AP RP）已完成溫度循環（TC）測試。
> 上限溫度為 **100 °C**，符合 TC-T 規格的範圍（−40 °C 至 100 °C，
> ΔT = 140 °C）。板級資格驗證里程碑涵蓋 **325 cycles**（對應 3 年
> 現場壽命）及 **525 cycles**（對應 5 年現場壽命），測試條件均為
> 非上電（unpowered）狀態。
>
> 若需確認是否完整採用 TC-T 規格（含 −40 °C 下限溫度），而非 TC-K
> 類型條件（0 °C 下限），建議向 Shou-chin 或 APTM QRE 團隊索取
> JNC1/JNC2 TC 測試報告。
>
> **2. 程式層級 vs. SXT 層級：**
>
> JNC 板級 TC 是以 **RP 層級（板 / 程式層級）資格驗證**的方式執行，
> 與 APTM QRE 管理的 SoC / 矽晶層級（SXT）資格驗證是分開進行的。
> 如 Juan Zermeno 所提到的，對 Navarre City 而言，SoC 層級的 ETB 資料
> （技術認證流程）將作為背景依據，板級的小樣本測試則另外針對中高風險
> 板級元件執行。
>
> 簡單說：**兩個層級都適用** — SXT 層級由 APTM QRE 在技術認證流程中執行；
> 板 / 程式層級的 TC 則在 RP 資格驗證計畫中，綁定程式里程碑執行
> （通常是 QS 或 PRQ 閘門，請向 Juan Zermeno 確認 Navarre City 的
> Reference Design 計畫適用哪些閘門）。
>
> **3. Navarre City TC-K vs. TC-T 的差異說明：**
>
> Navarre City RP 規劃採用 **1000 TC-K cycles（0 °C 至 125 °C）**，
> 而 Xeon 產品典型條件為 TC-T（−40 °C 至 100 °C）。若需將 Navarre
> 資料與 JNC 資料進行比較，或將 JNC TC 資料作為 Navarre 資格驗證
> 的引用依據，必須先完成設計差異與熱可比性評估。
>
> 如需協助取得 JNC 測試報告，我將直接跟 Shou-chin 追蹤。
>
> Best regards

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-23. Closes #161.*
