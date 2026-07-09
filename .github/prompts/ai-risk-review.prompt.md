# AI Risk Review Prompt

Perform a complete PQRE reuse gap analysis for the provided request.

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

Generate these sections in English:

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

For Risk Assessment, include an RPN table with:

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|--------|---------------|----------------|---------------|-----|-----------------|-----------|

Email/output gate:

- Any email-style output must be draft only.
- Include: `⚠️ DRAFT — DO NOT SEND — Human approval required before any external communication.`
