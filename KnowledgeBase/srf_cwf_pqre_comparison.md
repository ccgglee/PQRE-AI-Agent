# SRF vs CWF — PQRE Review Comparison (Screening Fields Only)

This table is for PQRE triage/screening only. Use platform-official collateral
(datasheet/FRD/OPN matrix) as the source of truth before sign-off.

---

## 1) Core PQRE Comparison Fields

| PQRE Field | SRF (Sierra Forest) | CWF (Clearwater Forest) | PQRE Review Implication |
|---|---|---|---|
| Product generation | Earlier Xeon E-core generation | Next Xeon E-core generation | Do not mix qualification basis across generations |
| Platform identity | SRF platform collateral | CWF platform collateral | Confirm exact platform before scoring risk |
| SI applicability/evidence | Must match SRF interfaces and SI reports | Must match CWF interfaces and SI reports | SRF SI evidence cannot be reused for CWF (and vice versa) without formal justification |
| PDN/VR basis | SRF power targets/load-line basis | CWF power targets/load-line basis | Re-run PDN/VR review when platform changes |
| Thermal basis | SRF thermal specs and validation | CWF thermal specs and validation | Re-check thermal margin and cooling evidence per platform |
| Reliability basis | SRF HTOL/FIT assumptions | CWF HTOL/FIT assumptions | Reliability projections are platform-specific |
| Qualification/sign-off reuse | Limited reuse with explicit delta analysis | Limited reuse with explicit delta analysis | Require gap list and closure plan before reuse |
| EC/revision baseline | SRF rev/errata baseline | CWF rev/errata baseline | Review must cite latest EC-exit baseline documents |

---

## 2) Dunlow Intake Reference (User-Provided)

### CPU used in Dunlow

- Model: **E-2488**
- Cores / Threads: **8C / 16T**
- Base Frequency: **3.2 GHz**
- Max Turbo Frequency: **5.6 GHz**
- Cache: **24 MB**
- TDP: **95W**

> Status: User-provided intake data; verify against official OPN/datasheet before
> final PQRE sign-off.

---

## 3) Minimum PQRE Decision Gate

Before recommendation (APPROVE / CONDITIONAL APPROVE / HOLD / REJECT), confirm:

1. Platform identity is explicitly confirmed (SRF or CWF).
2. SI evidence is platform-matched, or formal SI-N/A rationale is approved.
3. Thermal, PDN, and reliability evidence are based on the same platform baseline.

---

## 4) Xeon Product Line Mapping (for SRF/CWF Distinction)

| Product Line | Typical Naming | Use Case / Positioning | Relationship to SRF/CWF |
|---|---|---|---|
| Xeon E Series | Xeon E-24xx, E-23xx | Entry server / workstation class | Not part of SRF/CWF |
| Xeon D Series | Xeon D-xxxx | SoC, edge, networking | Generally not classified under SRF/CWF |
| Xeon Scalable (legacy naming) | Bronze / Silver / Gold / Platinum (e.g., 84xx/64xx) | Mainstream dual-/multi-socket datacenter | Different generation naming system from SRF/CWF |
| Xeon 6 (P-core) | Xeon 6 with P-cores | High-performance core line | Maps to Granite Rapids line (not CWF) |
| Xeon 6 (E-core) | Xeon 6 with E-cores | High core-density line | SRF/CWF belong to this line |
