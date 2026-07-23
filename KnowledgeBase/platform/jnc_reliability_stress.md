# JNC Reliability Stress — Temperature Cycle Test Data

This note captures confirmed reliability stress conditions for the Johnson City
(JNC1 / JNC2) DMR AP Reference Platform, based on the Reliability Stress
Summary reports submitted in issue #163.

---

## Temperature Cycle (TC) Stress — Confirmed Conditions

| Parameter | Value | Notes |
|-----------|-------|-------|
| Test type | Temperature Cycle (TC) | Board-level solder joint stress |
| Power state | **Powered on (active)** | CPU and platform components energised during cycling |
| Max temperature | **100 °C** | Upper dwell temperature |
| Primary purpose | CPU socket solder joint accelerated life testing | Covers BGA/LGA solder fatigue failure modes |
| Platform | JNC1 / JNC2 (DMR AP Reference Platform) | Johnson City RP |

---

## Reference Platform Recommended Cycle Counts

| Cycle Count | Lifetime Coverage | Notes |
|-------------|------------------|-------|
| **300 cycles** | > 3 years field lifetime | Minimum recommendation for reference platform qualification |
| **525 cycles** | Extended coverage | Recommended for higher confidence / longer service life assertion |

> Source: Issue #163 — Reliability stress summary JNC1.pdf / JNC2.pdf
>
> These cycle counts are specific to the JNC reference platform.
> Applicability to successor platforms (for example ANC Pine Stream COR 20CH)
> must be confirmed through a formal design-delta / thermal-comparability
> analysis before data reuse.

---

## Engineering Context

- Temperature Cycle stress is run **with power applied** (上電). This is
  intentional: it subjects the CPU socket and BGA solder joints to combined
  thermal cycling and electrical stress, providing a more conservative and
  realistic accelerated aging condition than unpowered cycling.

- Elevating the upper dwell temperature to **100 °C** increases the thermal
  excursion (ΔT) and accelerates solder fatigue per Coffin–Manson / modified
  Engelmaier models, shortening the time needed to accumulate equivalent
  field-life cycles.

- The **300-cycle milestone** maps to a > 3-year field lifetime assertion for a
  typical datacenter reference platform usage profile.

- The **525-cycle milestone** provides the extended confidence margin often
  required for volume production qualification sign-off or longer service life
  claims.

---

## Source Documents

| Document | Issue |
|----------|-------|
| Reliability stress summary JNC1.pdf | #163 |
| Reliability stress summary JNC2.pdf | #163 |

---

## Usage Guidance for Future Reviews

When a subsequent RP program (for example ANC, Sabre) cites JNC TC data:

1. Confirm the new platform's max junction temperature and thermal excursion
   are **within or below** the JNC test envelope (100 °C upper dwell).
2. Confirm the new board's solder material system, PCB layer count, and
   component weight distribution are equivalent to JNC.
3. If both conditions are met → **data reuse may be approved** (subject to
   formal delta analysis sign-off).
4. If either condition is not met → **supplemental TC testing at the
   applicable cycle count (300 or 525) is required** before PQRE sign-off.
