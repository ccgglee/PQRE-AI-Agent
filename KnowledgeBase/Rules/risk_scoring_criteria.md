# Risk Scoring Criteria

This document defines the RPN (Risk Priority Number) calculation rules and
tier definitions used by the PQRE Risk Review Agent.

---

## RPN Calculation

```
RPN = Severity (S) × Occurrence (O) × Detection (D)
```

RPN range: **1 – 125** (5×5×5 scale)

---

## Severity Scale (S)

| Score | Definition |
|-------|------------|
| 1 | No impact — change is cosmetic or documentation only |
| 2 | Minor — marginal performance change, no functional impact |
| 3 | Moderate — functional impact, workaround available |
| 4 | Significant — system failure under specific conditions |
| 5 | Critical — system failure, safety risk, or regulatory non-compliance |

---

## Occurrence Scale (O)

| Score | Definition |
|-------|------------|
| 1 | Remote — failure extremely unlikely; well-established design, >5 years field data |
| 2 | Low — isolated failures; similar design with minor delta |
| 3 | Moderate — occasional failures; new design or significant parameter change |
| 4 | High — repeated failures expected; limited characterisation data |
| 5 | Very High — failure almost certain; no prior validation at these conditions |

---

## Detection Scale (D)

| Score | Definition |
|-------|------------|
| 1 | Almost certain detection — automated monitoring or 100% test coverage |
| 2 | High detection — functional test catches failure reliably |
| 3 | Moderate detection — inspection or sample testing used |
| 4 | Low detection — failure mode difficult to detect in production |
| 5 | Undetectable — no current test or inspection method can catch failure |

---

## Risk Tier Definitions

| Tier | RPN Range | Action Required |
|------|-----------|-----------------|
| **Low Risk** | RPN ≤ 20 | Standard review; no escalation required |
| **Medium Risk** | RPN 21–50 | Engineering review required; owner assigned |
| **High Risk** | RPN ≥ 51 | Escalation to PQRE Manager + Business Owner required; HOLD until resolved |

---

## Data Confidence Scale

Data Confidence measures how reliable the input data is for a given domain.
It is assessed independently of RPN.

| Score | Definition |
|-------|------------|
| 1 | No data — assumption only; no measurement or simulation exists |
| 2 | Very low — informal estimate or outdated data (>2 product generations old) |
| 3 | Low — single data point or extrapolated from different platform |
| 4 | Moderate — multiple data points, same platform family |
| 5 | High — full characterisation data on the same component and board |

> **Low Confidence flag** is triggered when Data Confidence ≤ 2 for any
> in-scope domain. This flag must be added to the GitHub issue label and
> elevates the minimum review level to Engineering Manager.

---

## Risk Tier Escalation Rules

| Condition | Escalation Action |
|-----------|-------------------|
| Any domain RPN ≥ 51 | Add `high-risk` label; tag PQRE Manager; block sign-off |
| Any domain Data Confidence ≤ 2 | Add `low-confidence` label; request additional data before review |
| Two or more domains at Medium Risk | Aggregate risk treated as High Risk |
| Any Severity = 5 | Auto-escalate regardless of RPN |

---

## Example RPN Calculation

**Scenario**: COR CPU TDP increase from 650 W to 900 W — Thermal domain

| Parameter | Score | Rationale |
|-----------|-------|-----------|
| Severity | 4 | System thermal failure possible at 900 W if cooling solution not re-validated |
| Occurrence | 4 | 38% TDP increase with no new thermal test data provided |
| Detection | 3 | Thermal monitoring exists but may not catch margin erosion before damage |
| **RPN** | **48** | Medium Risk — engineering review required |
| Data Confidence | 1 | No thermal simulation or test data at 900 W provided in issue |

Because Data Confidence = 1 (≤ 2), the **Low Confidence** flag is also triggered
and the domain is treated as High Risk pending data submission.
