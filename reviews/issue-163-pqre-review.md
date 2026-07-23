# PQRE Risk Review — Issue #163

**Issue:** JNC reliability stress update
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/163
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-23
**Requestor:** ccgglee
**Platform:** Johnson City (JNC1 / JNC2) — DMR AP Reference Platform
**Scope:** Temperature Cycle (TC) reliability stress conditions, cycle count
recommendations, and data applicability guidance for successor platforms

---

## English

### Executive Summary

This issue provides confirmed Temperature Cycle (TC) reliability stress data
for the Johnson City (JNC1 / JNC2) DMR AP Reference Platform, based on two
attached PDF reports (*Reliability Stress Summary JNC1* and *JNC2*).

Key confirmed data points:

- TC stress is run **powered on (active)**: CPU and platform components are
  energised during the full hot–cold excursion.
- **Upper dwell temperature: 100 °C** — chosen to accelerate CPU socket and
  BGA solder joint fatigue via increased ΔT.
- **Recommended cycle counts for a reference platform:**
  - **300 cycles** — maps to > 3-year field lifetime
  - **525 cycles** — extended margin / volume production confidence

This information has been stored in
`KnowledgeBase/platform/jnc_reliability_stress.md` for retrieval by future
PQRE reviews that reference JNC TC data.

---

### Known Issues

1. The two PDF source documents are attachments on the GitHub issue and are not
   stored locally in the repository. Only their described content is captured
   here; raw data tables, Weibull plots, and sample sizes are not directly
   verifiable from the repository.
2. The exact lower dwell temperature and ramp/dwell time profile are not stated
   in the issue text; these parameters affect the ΔT calculation and should be
   retrieved from the full PDF reports when performing a comparability
   assessment for a new platform.
3. Applicability of this JNC TC data to successor platforms (for example ANC
   Pine Stream COR 20CH) has **not** yet been confirmed. A formal design-delta
   and thermal-comparability analysis is required.

---

### Gap Analysis

| Domain | Current Gap | Evidence Missing | Impact |
|---|---|---|---|
| Reliability | TC lower dwell temperature, ramp rate, dwell time not captured from PDF | Full TC profile from JNC1/JNC2 reports | Medium |
| Reliability | Sample size, failure mode, and pass/fail summary not yet in KnowledgeBase | JNC1/JNC2 report data tables | Medium |
| Reliability | Data reuse decision for ANC / successor platforms not issued | Design-delta thermal comparability analysis | High |
| Material | PCB stack-up and solder alloy used in JNC TC test not documented here | JNC BOM and material spec | Low |

---

### Action Items

1. **Store TC profile details** (lower dwell, ramp rate, dwell time, sample
   size, failure mode summary) from JNC1/JNC2 PDF reports into
   `KnowledgeBase/platform/jnc_reliability_stress.md` once the PDFs are
   accessible in the repository or shared drive.
2. **For any new RP program referencing JNC TC data** (for example ANC, Sabre):
   - Confirm new platform's upper junction temperature ≤ 100 °C under TC
     stress conditions.
   - Confirm solder material system and PCB construction are equivalent.
   - If both confirmed → data reuse may be approved subject to formal
     sign-off.
   - If either not confirmed → require supplemental TC at 300 or 525 cycles.
3. **Keep this knowledge note updated** when full PDF report data becomes
   available.
4. Any external communication regarding this data must remain **draft only**
   until reviewed and approved by a human PQRE engineer.

---

### Risk Assessment

| Parameter | Score | Rationale |
|---|---:|---|
| Severity | 2 | This is a knowledge-capture and guidance update, not a product escape |
| Occurrence | 2 | JNC is a mature platform; no new failure mode reported |
| Detection | 2 | Data gaps are visible and flagged; not hidden |
| **RPN** | **8** | **Low Risk** |
| Data Confidence | 3 | Key TC conditions confirmed from issue text; full PDF details pending |

**Risk Band:** **Low Risk** (RPN = 8)
**Disposition:** **APPROVE** for storing this data in the KnowledgeBase.
**CONDITIONAL APPROVE** for reuse decisions on successor platforms — pending
formal design-delta and thermal comparability analysis.

---

### Recommendation

1. The JNC1/JNC2 TC stress conditions (powered on, 100 °C upper dwell, 300
   and 525 cycle recommendations) are now recorded in
   `KnowledgeBase/platform/jnc_reliability_stress.md`.
2. Future PQRE reviews that ask "can we reuse JNC TC data for platform X"
   **must** retrieve this file and apply the guidance in the *Usage Guidance
   for Future Reviews* section before issuing a disposition.
3. Successor platform programs should plan TC qualification using these cycle
   counts as the baseline unless a formal comparability analysis justifies
   deviation.

---

## 繁體中文（Traditional Chinese）

### Executive Summary（執行摘要）

本議題提供了 Johnson City（JNC1 / JNC2）DMR AP Reference Platform 經確認的
溫度循環（TC）可靠度壓力測試資料，來源為兩份附件 PDF 報告
（*Reliability Stress Summary JNC1* 及 *JNC2*）。

已確認的關鍵數據：

- TC 壓力測試為**上電狀態（active）**進行：整個高低溫循環過程中，CPU
  及平台元件均處於通電狀態。
- **溫度上限：100 °C** — 目的在於透過較大的 ΔT 加速 CPU socket 及
  BGA 焊點的疲勞失效。
- **Reference platform 建議循環次數：**
  - **300 cycles** — 對應 > 3 年現場使用壽命
  - **525 cycles** — 延伸可信度 / 量產資格確認用

本資訊已存入
`KnowledgeBase/platform/jnc_reliability_stress.md`，供後續引用 JNC TC
資料的 PQRE 審查使用。

---

### Known Issues（已知問題）

1. 兩份 PDF 來源文件以 GitHub 附件形式存在，未實際存於本 repository，
   因此目前僅能依 issue 文字內容摘錄，無法直接驗證原始數據表格、
   Weibull 圖及樣本數。
2. Issue 文字中未說明溫度下限及升降溫速率 / 停留時間；這些參數影響 ΔT
   計算，進行新平台可比性評估時須從完整 PDF 中取得。
3. 本 JNC TC 資料是否適用於後繼平台（如 ANC Pine Stream COR 20CH）
   **尚未確認**，必須完成正式設計差異與熱可比性分析。

---

### Gap Analysis（缺口分析）

| 領域 | 目前缺口 | 缺失證據 | 影響 |
|---|---|---|---|
| Reliability | TC 溫度下限、升降溫速率、停留時間未從 PDF 擷取 | JNC1/JNC2 完整 TC 測試規格 | 中 |
| Reliability | 樣本數、失效模式、Pass/Fail 摘要尚未存入 KnowledgeBase | JNC1/JNC2 報告數據表 | 中 |
| Reliability | ANC 及後繼平台的數據重用決策尚未發出 | 設計差異 / 熱可比性分析 | 高 |
| Material | JNC TC 測試所用 PCB 疊層及錫膏合金未在此文件化 | JNC BOM 及材料規格 | 低 |

---

### Action Items（行動項目）

1. **補充 TC 規格細節**（溫度下限、升降溫速率、停留時間、樣本數、失效模式
   摘要），在 PDF 可存取後更新至
   `KnowledgeBase/platform/jnc_reliability_stress.md`。
2. **後繼 RP 程式（如 ANC、Sabre）引用 JNC TC 資料時**：
   - 確認新平台在 TC 壓力條件下的最高接面溫度 ≤ 100 °C。
   - 確認錫膏材料系統及 PCB 構造等效。
   - 兩項均確認 → 可於正式 sign-off 後核准數據重用。
   - 任一未確認 → 需以 300 或 525 cycles 進行補充 TC 測試。
3. **持續更新此知識文件**，待完整 PDF 報告資料可取得時補充。
4. 任何對外溝通均須維持 **draft only** 狀態，經人工 PQRE 工程師審核後
   方可發送。

---

### Risk Assessment（風險評估）

| 參數 | 分數 | 說明 |
|---|---:|---|
| Severity | 2 | 屬知識擷取與指引更新，非產品逸失事件 |
| Occurrence | 2 | JNC 為成熟平台，無新失效模式回報 |
| Detection | 2 | 資料缺口已清楚標示，非隱性風險 |
| **RPN** | **8** | **低風險** |
| Data Confidence | 3 | 主要 TC 條件已由 issue 文字確認，完整 PDF 細節待補 |

**Risk Band：** **低風險**（RPN = 8）
**Disposition：** 將資料存入 KnowledgeBase → **APPROVE**。
後繼平台的重用決策 → **CONDITIONAL APPROVE**，需正式設計差異及
熱可比性分析完成後方可確認。

---

### Recommendation（建議）

1. JNC1/JNC2 TC 壓力測試條件（上電、溫度上限 100 °C、300 及 525 cycles
   建議值）已記錄於
   `KnowledgeBase/platform/jnc_reliability_stress.md`。
2. 後續 PQRE 審查詢問「能否為 X 平台重用 JNC TC 資料」時，**必須先
   擷取此文件**並套用其中的重用指引，再發出 disposition。
3. 後繼平台程式應以這些 cycle count 作為 TC 資格確認基線，如有偏差，
   須以正式可比性分析予以佐證。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-23. Closes #163.*
