# PQRE Risk Review — Issue #139

**Issue:** The package S&V test is pending due to lacking GenZ cables, so we are unable to support the OCP card.
**URL:** https://github.com/ccgglee/PQRE-AI-Agent/issues/139
**Reviewed by:** pqre-risk-review-agent v1.0.0
**Review Date:** 2026-07-21
**Requestor:** ccgglee
**Platform:** Aivres ABC
**Scope:** Packaging ISTA 3A readiness, OCP card outgoing quality readiness, GenZ cable shortage mitigation

---

## English

### Executive Summary

The current shipment-readiness blocker is a **test fixture/material gap** (missing GenZ cables), not a confirmed product design defect. The key decision is whether the OCP card is part of the shipment configuration and therefore a mandatory production-test item.

- If **OCP card is required in shipped configuration**, then OCP functional verification before shipment is mandatory. Shipment should be **HOLD** until an approved alternate verification path is completed.
- If **OCP card is not required in shipped configuration**, then shipment may proceed only after documented outgoing quality controls confirm OCP card quality through alternate evidence (lot sampling, bench validation, or supplier CoC + incoming inspection), and with clear customer communication.

The recommended near-term path is:
1. Execute an immediate containment plan for cable shortage.
2. Approve a temporary alternate test path with explicit exit criteria.
3. Keep ISTA 3A packaging S&V and OCP quality evidence traceable under controlled release gating.

---

### Known Issues

1. **GenZ cable shortage** prevents normal OCP-card-enabled validation flow.
2. **Package S&V timing risk** for ISTA 3A due to unavailable full system test condition.
3. **Production test definition ambiguity** (whether OCP is mandatory pre-shipment) is not formally closed.
4. **Outgoing quality evidence completeness** for OCP card may be insufficient if standard flow is bypassed.

---

### Gap Analysis

| Domain | Current Gap | Evidence Missing | Impact |
|---|---|---|---|
| Thermal | OCP-on thermal corner not rechecked under alternate setup | OCP-enabled thermal margin logs | Medium |
| SI | GenZ signal path cannot be validated with normal cable | BER/eye/jitter evidence under substitute method | High |
| PDN | OCP load-transient behavior under real link not fully exercised | Rail droop/transient captures with OCP scenario | Medium |
| Mechanical | ISTA 3A execution status pending | Full ISTA 3A report, failure analysis (if any) | High |
| DFM | Test station flow depends on constrained material | Updated temporary WI/SOP and operator training record | Medium |
| DFT | Production test coverage reduced without GenZ cable path | Coverage delta and compensating controls | High |
| Material | Single-source/low-buffer cable supply risk | AVL/second-source qualification status | High |
| Regulatory | No direct non-compliance seen, but release evidence chain incomplete | Release checklist sign-off with deviation approval | Low |
| Reliability | OCP outgoing quality confidence reduced if standard test skipped | Sample stress/functional revalidation data | Medium |

---

### Action Items

1. **Decision Gate (within 24h):** Confirm and document whether OCP card is required in ABC pre-shipment production test.
2. **If OCP is required:**  
   - Set disposition to **HOLD** for affected lots.  
   - Use temporary alternatives only if validated, for example: borrowed qualified GenZ cables from shared lab pool, approved adapter harness, or bench-level OCP functional test fixture reproducing critical link conditions.  
   - Define pass/fail equivalence criteria against normal production test.
3. **If OCP is not required:**  
   - Keep shipment as **CONDITIONAL APPROVE** only after compensating quality controls are active: supplier CoC review, incoming inspection, lot-based OCP functional sampling, and traceability to serial/lot records.  
   - Communicate limitations and residual risk in outgoing release notes.
4. **Packaging track:** Complete ISTA 3A testing and attach report to release package before final sign-off.
5. **Material risk reduction:** Launch GenZ cable dual-source or safety-stock plan with owner/date.

---

### Risk Assessment

#### Primary Risk Scoring (GenZ cable shortage impact on OCP shipment readiness)

| Parameter | Score | Rationale |
|---|---:|---|
| Severity | 4 | Potential shipment delay or escaped OCP quality risk |
| Occurrence | 4 | Cable shortage already active |
| Detection | 3 | Missing normal path reduces test detectability |
| **RPN** | **48** | **Medium Risk** (by RPN band) |
| Data Confidence | 2 | Key evidence still pending |

**Risk Band:** **Medium Risk** (RPN=48)  
**Disposition:** **HOLD** if OCP is required and no approved equivalent test is available; otherwise **CONDITIONAL APPROVE** with compensating controls and completion dates.

---

### Recommendation

**Direct response to asked questions:**

1. **Any alternative to replace GenZ cables?**  
   Yes, temporarily and under controlled deviation: (a) shared qualified cable pool, (b) approved equivalent harness/adapter, (c) bench fixture that reproduces critical OCP functional coverage. All require equivalence evidence to normal flow.

2. **Is the OCP card required for ABC production test prior to shipment?**  
   - **If Yes:** treat as shipment blocker; use HOLD until equivalent verification is completed and approved.  
   - **If No:** shipment may proceed only with documented compensating outgoing quality controls and a dated closure plan for restoring normal test flow.

3. **How to ensure OCP outgoing quality without GenZ cables (if OCP not mandatory in-line)?**  
   Use risk-based sampling, incoming inspection reinforcement, supplier CoC review, bench functional checks, and strict lot traceability; keep deviation temporary with formal exit criteria.

---

## 繁體中文（Traditional Chinese）

### Executive Summary（執行摘要）

目前出貨準備的主要阻礙是**測試治具/物料缺口**（缺 GenZ 線材），而非已確認的產品設計失效。關鍵決策點是：OCP 卡是否屬於出貨配置中的必要生產測試項目。

- 若 **OCP 卡屬於出貨必要配置**，則出貨前必須完成 OCP 功能驗證；在無替代驗證路徑前，建議 **HOLD**。
- 若 **OCP 卡不屬於出貨必要配置**，可在補強出貨品質證據（抽樣、治具驗證、供應商 CoC + 進料檢驗）後條件放行，並需對客戶清楚揭露限制。

建議短期執行路徑：
1. 立即執行線材短缺遏制方案。
2. 核准暫時替代測試路徑並定義退出條件。
3. 維持 ISTA 3A 與 OCP 品質證據的可追溯放行關卡。

---

### Known Issues（已知問題）

1. **GenZ 線材短缺**，導致既有 OCP 驗證流程無法執行。
2. **ISTA 3A 包裝 S&V 時程風險**，因缺乏完整系統測試條件。
3. **生產測試定義未閉環**（OCP 是否為出貨前必要項）尚未文件化確認。
4. **OCP 出貨品質證據完整性不足**，若跳過標準流程可能造成覆蓋率缺口。

---

### Gap Analysis（缺口分析）

| 領域 | 目前缺口 | 缺失證據 | 影響 |
|---|---|---|---|
| Thermal | 替代設定下未重查 OCP 開啟時熱角落 | OCP 開啟熱餘裕紀錄 | 中 |
| SI | 無法走標準 GenZ 路徑驗證 | 替代方案 BER/eye/jitter 證據 | 高 |
| PDN | 真實連線情境下 OCP 瞬態負載覆蓋不足 | OCP 情境 rail droop/瞬態量測 | 中 |
| Mechanical | ISTA 3A 尚未完成 | 完整 ISTA 3A 報告與失效分析 | 高 |
| DFM | 測站流程依賴短缺物料 | 暫行 WI/SOP 與訓練紀錄 | 中 |
| DFT | 缺線材導致生產測試覆蓋下降 | 覆蓋率差異與補償控制 | 高 |
| Material | 線材單一來源/安全庫存不足 | AVL/第二來源資格進度 | 高 |
| Regulatory | 未見直接法規不符，但放行證據鏈不完整 | 偏差放行簽核紀錄 | 低 |
| Reliability | 略過標準流程時 OCP 品質信心下降 | 抽樣壓測/功能重驗資料 | 中 |

---

### Action Items（行動項目）

1. **決策關卡（24 小時內）：** 文件化確認 OCP 是否為 ABC 出貨前必要生產測試。
2. **若 OCP 必要：**  
   - 受影響批次設為 **HOLD**。  
   - 僅可使用已驗證之暫時替代方案（如共用合格線材池、核准等效轉接、可重現關鍵覆蓋之治具）。  
   - 明確定義與標準流程等效的判定準則。
3. **若 OCP 非必要：**  
   - 僅在補償品質控制上線後給予 **CONDITIONAL APPROVE**（CoC、進料檢、批次抽驗、序號追溯）。  
   - 在出貨文件中揭露限制與殘餘風險。
4. **包裝路徑：** 完成 ISTA 3A 並納入放行證據包。
5. **物料風險下降：** 啟動 GenZ 線材第二來源或安全庫存計畫（含 owner/日期）。

---

### Risk Assessment（風險評估）

#### 主要風險評分（GenZ 線材短缺對 OCP 出貨準備之影響）

| 參數 | 分數 | 說明 |
|---|---:|---|
| Severity | 4 | 可能造成出貨延誤或 OCP 品質逸失風險 |
| Occurrence | 4 | 線材短缺已發生 |
| Detection | 3 | 標準路徑缺失降低偵測能力 |
| **RPN** | **48** | **中風險**（依 RPN 分級） |
| Data Confidence | 2 | 關鍵證據尚未齊備 |

**Risk Band：** **中風險**（RPN=48）  
**Disposition：** 若 OCP 必要且無等效驗證，為 **HOLD**；若 OCP 非必要，且補償控制到位則可 **CONDITIONAL APPROVE**。

---

### Recommendation（建議）

**針對問題直接回覆：**

1. **是否有替代 GenZ 線材方案？**  
   有，但僅限暫時偏差管控下使用： (a) 共用合格線材池、(b) 核准等效轉接/線束、(c) 可重現關鍵功能覆蓋的 bench 治具。皆需提供與標準流程等效證據。

2. **OCP 卡是否為 ABC 出貨前必要生產測試？**  
   - **若是：** 視為出貨阻擋項，須 HOLD 至等效驗證完成。  
   - **若否：** 可條件放行，但必須有文件化補償品質管制與明確恢復標準流程時程。

3. **若無 GenZ 線材且 OCP 非必要 inline，如何確保 OCP 出貨品質？**  
   以風險式抽樣、進料檢驗強化、供應商 CoC、bench 功能驗證與批次追溯來確保品質，且偏差需有期限與退出條件。

---

> ⚠️ **DRAFT — DO NOT SEND** — Human approval required before any external communication.

---

*Generated by pqre-risk-review-agent v1.0.0 on 2026-07-21.
Closes #139.*
