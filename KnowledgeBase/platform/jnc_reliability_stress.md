# JNC Reliability Stress — Temperature Cycle Test Data

This note captures confirmed reliability stress conditions for the Johnson City
(JNC1 / JNC2) DMR AP Reference Platform, based on the Reliability Stress
Summary reports submitted in issue #163.

---

## Temperature Cycle (TC) Stress — Confirmed Conditions

| Parameter | Value | Notes |
|-----------|-------|-------|
| Test type | Temperature Cycle (TC) | Board-level solder joint fatigue assessment |
| Power state | **Unpowered** | No power applied during temperature cycling |
| Max temperature | **100 °C** | Upper dwell temperature |
| Primary purpose | CPU socket solder joint accelerated life testing | Covers BGA/LGA solder fatigue failure modes |
| Platform | JNC1 / JNC2 (DMR AP Reference Platform) | Johnson City RP |

---

## Reference Platform Recommended Cycle Counts

| Cycle Count | Lifetime Coverage | Notes |
|-------------|------------------|-------|
| **325 cycles** | 3-year field lifetime | Recommended qualification target |
| **525 cycles** | 5-year field lifetime | Recommended for extended life coverage |

> Source: Issue #163 — Reliability stress summary JNC1.pdf / JNC2.pdf
>
> These cycle counts are specific to the JNC reference platform.
> Applicability to successor platforms (for example ANC Pine Stream COR 20CH)
> must be confirmed through a formal design-delta / thermal-comparability
> analysis before data reuse.

---

## TC Profile Classification — Open Item

| Parameter | Status | Notes |
|---|---|---|
| Upper dwell temperature | **100 °C** — Confirmed | Consistent with TC-T upper limit |
| Lower dwell temperature | **Not confirmed** | TC-T = −40 °C (ΔT 140 °C); TC-K = 0 °C (ΔT 100 °C) |
| JEDEC profile classification | **Not confirmed** | TC-T or TC-K status requires JNC TC test report |

> **Action**: Retrieve JNC1/JNC2 TC test reports from Shou-chin or APTM QRE team
> to confirm the lower dwell temperature and JEDEC TC profile classification
> (TC-T vs. TC-K). See Issue #161 for context.

---

## Comparison with Navarre City RP (Issue #161)

Navarre City RP (DMR-RS, Reference Design qualification tier) uses a different
TC profile and cycle count than JNC:

| Parameter | JNC (DMR AP RP) | Navarre City RP |
|---|---|---|
| TC profile | Upper 100 °C; lower dwell TBC | TC-K (0 °C to 125 °C) |
| Cycle count milestones | 325 cycles (3 yr), 525 cycles (5 yr) | 1000 cycles |
| Power state | Unpowered | Unpowered (assumed) |
| DMR-RS attachment | Socketed (LGA) | Not soldered down (ETB data leveraged) |

> **Comparability rule**: JNC TC data cannot be directly reused for Navarre City
> without a formal design-delta and TC profile comparability assessment. Key
> factors to confirm: lower dwell temperature equivalence, solder alloy,
> PCB stack-up, and component placement delta.

---

## Engineering Context

- Temperature Cycle (TC/TCT) stress is performed under **unpowered conditions**.
  No electrical power is applied to the CPU or platform during cycling. The
  objective is to accelerate thermo-mechanical fatigue in solder joints caused
  by repeated temperature excursions.

- Elevating the upper dwell temperature to **100 °C** increases the thermal
  excursion (ΔT) and accelerates solder fatigue per Coffin-Manson /
  modified Engelmaier models, shortening the time required to accumulate
  equivalent field-life damage.

- The **325-cycle milestone** is commonly used to support a **3-year product
  life** requirement for the JNC reference platform.

- The **525-cycle milestone** is commonly used to support a **5-year product
  life** requirement and provides additional confidence margin for long-life
  datacenter deployments.

- For comparison: Navarre City RP uses **TC-K (0 °C to 125 °C, 1000 cycles)**,
  which is the same TC profile used for DMR-RS aligned to the Nimbus
  qualification baseline (per Issue #161, Juan Zermeno's email July 2026).

---
