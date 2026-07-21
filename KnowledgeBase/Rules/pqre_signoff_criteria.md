# PQRE Sign-Off Criteria

This document defines the minimum evidence requirements that must be present
before a PQRE review can be closed with an **APPROVE** or **CONDITIONAL APPROVE**
recommendation. Any item marked **Blocking** must be resolved before sign-off.

---

## 1. Thermal

| Evidence Item | Blocking |
|---------------|----------|
| Component TDP (Thermal Design Power) — current and new value | Yes |
| Junction temperature (Tj_max) from component datasheet | Yes |
| Thermal resistance (θja or θjb) — board-level or system-level | Yes |
| Cooling solution thermal specification (heatsink, airflow, TIM) | Yes |
| Thermal simulation or test data at new TDP | Yes |
| System inlet temperature specification | No |
| Altitude derating applied if applicable | No |

---

## 2. Derating

| Evidence Item | Blocking |
|---------------|----------|
| Component maximum voltage / current / power ratings (datasheet) | Yes |
| Applied voltage / current / power at operating conditions | Yes |
| Derating factor per Intel / JEDEC / IPC derating guidelines | Yes |
| Evidence that all parameters remain within derated limits | Yes |
| Derating table or calculation workbook | No |

---

## 3. SI / PI / PDN(Power Delivery Network)

| Evidence Item | Blocking |
|---------------|----------|
| PDN target impedance specification | Yes |
| PDN simulation or measurement at new power level | Yes |
| VR (Voltage Regulator) load line specification | Yes |
| Eye diagram or S-parameter data for critical interfaces | No |
| Power sequencing diagram (if power change affects sequencing) | No |
| Decoupling capacitor placement and value BOM | No |

---

## 4. Mechanical

| Evidence Item | Blocking |
|---------------|----------|
| Component weight and CG data (if changed) | No |
| Board flex / stress simulation at new thermal load | Yes |
| Shock and vibration compliance (MIL-STD-810 or equivalent) | No |
| Connector and socket retention force data | No |
| Chassis airflow path verification | No |

---

## 5. Reliability

| Evidence Item | Blocking |
|---------------|----------|
| Component FIT rate or MTBF at new operating conditions | Yes |
| HTOL (High Temperature Operating Life) test data or extrapolation | No |
| ELFR (Early Life Failure Rate) data if new component stepping | No |
| Qualification report from component supplier | No |
| System-level reliability prediction (RBD or FMEA) | No |

---

## 6. Manufacturing

| Evidence Item | Blocking |
|---------------|----------|
| DFM review sign-off from manufacturing engineering | No |
| Component placement rule check (IPC-7351 or equivalent) | No |
| Solder joint reliability data (thermal cycling test) | Yes |
| Process capability index (Cpk) for critical dimensions | No |
| AOI / X-ray inspection criteria defined | No |

---

## 7. Supplier Readiness

| Evidence Item | Blocking |
|---------------|----------|
| Component availability / lead time confirmation | Yes |
| EOL (End-of-Life) notice status — no active EOL | Yes |
| Supplier qualification certificate (AEC-Q100 or equivalent) | Yes |
| Multi-source availability or single-source risk documented | No |
| Component change notice (CCN / PCN) review | No |

---

## 8. Regulatory

| Evidence Item | Blocking |
|---------------|----------|
| RoHS compliance declaration | Yes |
| REACH SVHC declaration | Yes |
| CE / FCC / UL marks — applicable certifications confirmed | No |
| Export classification (ECCN) — no change or re-classification completed | No |
| Battery / chemical substance declaration (if applicable) | No |
| OxM regulatory execution plan and schedule (when SOW-based OxM engagement applies) | Yes |
| OxM preliminary EMC test results or engineering compliance assessment (when SOW-based OxM engagement applies) | No |

---

## 8a. SOW-Based OxM Regulatory Ownership Rule

When a Statement of Work (SOW) governs the manufacturing engagement, the regulatory
ownership assignment **must be derived from the SOW contract language**, not assumed
from the absence of a named individual in the issue body.

**Default SOW ownership pattern (Intel OxM SOW, Section 4.1):**

| Activity | Owner | Intel Role |
|----------|-------|------------|
| Regulatory program execution plan and schedule | **OxM** | Review and Approve |
| EMC testing (radiated, conducted, immunity) at accredited lab | **OxM** | Review test report |
| Preliminary EMC test results or engineering compliance assessment | **OxM** | Accept / request re-test |
| RoHS / REACH SVHC compliance declarations for BOM | **OxM** | Review |
| Identification of design changes with compliance impact | **OxM** | Joint impact assessment |
| Final regulatory sign-off and market-entry approval | Intel | Sign-off owner |

> **IMPORTANT — AI Agent Rule:**  
> When SOW Section 4 or equivalent contract language is present, the AI agent
> **must not** conclude "no obvious responsible party" for regulatory activities.
> OxM is the contractually-designated primary owner. If the SOW is not available,
> the AI agent must explicitly flag this as an information gap and request the SOW
> rather than defaulting to "no owner assigned."

---

## Sign-Off Override Policy

If a blocking evidence item cannot be obtained before the project milestone,
a **Risk Acceptance** signed by the PQRE Manager and the Business Owner is
required. The waiver must be attached to the GitHub issue before the
recommendation is changed from HOLD to CONDITIONAL APPROVE.
