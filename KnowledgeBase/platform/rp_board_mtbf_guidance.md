# RP Board MTBF Guidance

This note captures the current repository guidance for answering MTBF
calculation questions on Intel RP boards.

## Confirmed repository evidence

- `KnowledgeBase/Rules/pqre_signoff_criteria.md` requires **Component FIT rate or
  MTBF at new operating conditions** for reliability sign-off.
- `KnowledgeBase/Rules/Intel Rules/source_catalog.yaml` identifies the Intel Rule
  SharePoint source for reliability reference data and includes:
  - `FOQM`
  - `Lab and ODM requirement`
- `KnowledgeBase/Rules/Intel Rules/intel_rule_catalog.yaml` contains the
  following MTBF-adjacent retrieval paths:
  - `FOQM/For PVC product`
  - `Lab and ODM requirement`
- `reviews/issue-80-pqre-review.md` states that predecessor RP reliability data
  reuse requires a **formal design-delta / comparability assessment** before the
  data can be re-used for a new RP.

## Confirmed issue-specific input paths

Issue #152 explicitly lists these MTBF input paths:

1. **ODM RD (PVC)**
2. **Real RMA data (JNC RP)**
3. **Reliability data**
4. **DPPM data of BOM (Dunlow RP)**

> Note: the issue title says "5 ways to get MTBF", but the visible issue body
> provides four explicit paths. Do not invent a fifth path unless additional
> evidence is attached.

## Working guidance

### 1. How to point someone to a BKM

The repository currently points to **reference folders**, not to a single local
standalone MTBF-calculation procedure. The best available BKM starting points
are:

- `FOQM/For PVC product`
- `Lab and ODM requirement`

Both paths are recorded in
`KnowledgeBase/Rules/Intel Rules/intel_rule_catalog.yaml`.

### 2. How to describe the MTBF calculation basis

For RP boards, MTBF should be described as a **package of evidence** rather than
as one formula:

- ODM reliability prediction / RD estimate
- predecessor RP field-return / RMA experience
- qualification / reliability stress data
- BOM-based DPPM prediction

### 3. How to describe ownership

[CONFIRMED]

- The issue itself shows that at least some MTBF inputs come from the ODM side
  (`ODM RD (PVC)` and `DPPM data of BOM`).
- The repository also treats MTBF/FIT as a PQRE sign-off input that must be
  reviewed before reliability approval.

[ASSUMPTION]

- The practical operating model is usually **ODM-prepared calculation package +
  Intel board design / PQRE review and acceptance**, not Intel board design
  acting alone.
- Intel should own the **approval / reuse decision**, especially when older RP
  data (for example JNC1/JNC2) is being cited for a newer RP.

## Draft reply template

> Yes — there is BKM/reference material for MTBF work, but in the current
> repository it is represented as source folders rather than one standalone local
> MTBF procedure. The best starting points are the Intel Rule references
> `FOQM/For PVC product` and `Lab and ODM requirement`.
>
> For RP boards, MTBF is normally built from several evidence paths: ODM RD
> prediction, real RMA data from earlier RP boards such as JNC, qualification /
> reliability data, and BOM-based DPPM prediction such as the Dunlow RP example.
>
> Based on the issue evidence, this is not purely an Intel board design team
> deliverable. The ODM typically prepares the prediction inputs / first-pass
> calculation, while Intel board design and PQRE review the assumptions, decide
> whether older RP data is reusable, and accept the final basis for sign-off.
