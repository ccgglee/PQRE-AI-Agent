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

---
