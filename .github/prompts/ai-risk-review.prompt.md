# AI Risk Review Prompt

Perform a complete PQRE reuse gap analysis for the provided request.

If the intake issue or latest user comment explicitly says `Analyze Issue #<N>`,
use that referenced issue as the primary evidence source and treat the current
issue as the routing/intake wrapper.

Focus areas (all in scope unless explicitly excluded):

1. Thermal
2. Derating
3. SI / PI / PDN
4. Mechanical
5. Reliability
6. Manufacturing
7. Supplier Readiness
8. Regulatory

Use repository references:

- `KnowledgeBase/pqre_signoff_criteria.md`
- `KnowledgeBase/risk_scoring_criteria.md`

Rules:

- Missing evidence must be explicitly listed; do not assume evidence exists.
- Clearly distinguish `[CONFIRMED]`, `[MISSING]`, and `[ASSUMPTION]` items.
- RPN >= 51 requires management review (High Risk).
- Data Confidence <= 2 is Low Confidence and must be flagged.
- Recommendation must be exactly one: APPROVE / CONDITIONAL APPROVE / HOLD / REJECT.

Section selection priority (highest first):

1. `Required PQRE Analysis` list in the intake issue body
2. Explicit section list in the latest `@copilot` issue comment
3. Default section set below

Generate these default sections in English:

1. Executive Summary
2. Request Classification
3. Available Evidence
4. Missing Evidence
5. Known Issues
6. Unknown Risks
7. Qualification Gaps
8. Risk Assessment
9. Required Actions
10. PQRE Recommendation

Then provide:

11. Traditional Chinese Summary (include Executive Summary + PQRE Recommendation in Traditional Chinese)

Language/output rules:

- If the request says `Output in English and Traditional Chinese`, provide the
  requested section set in English first, then provide the same requested
  section set in Traditional Chinese.
- If the request asks only for `Traditional Chinese Summary`, keep Section 11
  as summary-only (Executive Summary + PQRE Recommendation).

For Risk Assessment, include an RPN table with:

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|--------|---------------|----------------|---------------|-----|-----------------|-----------|

Custom section content guidance (used when `Required PQRE Analysis` overrides the default):

- **Action Required (Yes/No)**: Standalone section. State Yes or No, then provide
  one or two sentences explaining why action is or is not required.
- **Impact Assessment**: Provide a qualitative impact summary table (Category /
  Impact Description / Severity), followed by the full RPN table. Include scoring
  rationale for each in-scope domain. This section replaces "Risk Assessment" when
  the custom section list does not include a separate "Risk Assessment" section.
- **Information Gaps**: Provide a numbered table of missing evidence items
  (# / Missing Item / Domain / Blocking). This section replaces "Missing Evidence"
  and "Qualification Gaps" when those sections are not in the custom section list.

Email/output gate:

- Any email-style output must be draft only.
- Include: `⚠️ DRAFT — DO NOT SEND — Human approval required before any external communication.`
