# AI Risk Review Prompt

Perform a complete PQRE reuse gap analysis for the provided request.

If the intake issue or latest user comment explicitly says `Analyze Issue #<N>`,
use that referenced issue as the primary evidence source and treat the current
issue as the routing/intake wrapper.

Apply a hardware scope gate before detailed analysis:

- First determine whether the request affects **platform hardware** or
  **validation hardware**.
- Requests that are not related to hardware (for example firmware-only,
  software-only, or process-only asks such as a BMC firmware change with no
  hardware impact) are **OUT OF SCOPE** for this PQRE hardware workflow and
  must receive a **REJECT** recommendation.
- If the intake bundles multiple features or questionnaire items together,
  classify each item as `IN SCOPE`, `OUT OF SCOPE`, or `MIXED`, and recommend
  splitting the request unless combined routing is clearly intended.
- When the request asks whether reliability stress is affected, answer that
  question specifically in terms of impact to platform hardware or validation
  hardware. If no hardware effect is shown, reject the item rather than
  analyzing it as a hardware qualification request.

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

If Priority 1 or 2 provides an explicit section list, output exactly those
sections, in the same order, using the same headings. Do not add default
sections that were not requested. If the request asks for `Action Required
(Yes/No)`, emit it as a standalone section instead of nesting it only inside
`Request Classification`.

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

When these commonly requested headings appear in the selected section list, use
the following content rules:

- `Request Classification` — identify domains in scope / out of scope, risk
  tier, hardware-scope decision, and any routing classification needed to
  understand the request.
- `Action Required` — answer `Yes` or `No` first, then briefly state why and
  which blocking items drive the answer.
- `Impact Assessment` — summarise positive and negative impact by category
  (for example schedule, quality, compliance, service continuity, customer
  impact, or hardware impact).
- `Information Gaps` — list missing evidence or unanswered questions required
  before confident sign-off; mark blocking items clearly.
- `Required Actions` — list concrete follow-up actions with owner / due date /
  blocking status when known, otherwise mark as `[TBD]`.
- `Draft Questionnaire Responses` — append this final section when the intake
  or latest user comment asks you to answer a questionnaire, form, checklist,
  or submission template. Keep the answers in draft-only mode, use `[TBD]` for
  missing identity / ownership / directory-backed fields, do not invent names
  or personal details, and explicitly reject any item that is not related to
  platform hardware or validation hardware.

Then provide:

11. Traditional Chinese Summary (include Executive Summary + PQRE Recommendation in Traditional Chinese)

Language/output rules:

- If the request says `Output in English and Traditional Chinese`, provide the
  requested section set in English first, then provide the same requested
  section set in Traditional Chinese. When an explicit section list is
  requested, repeat that exact section set in both languages.
- If a questionnaire/form answer set is requested, append `Draft Questionnaire
  Responses` to the English output and a corresponding Traditional Chinese
  draft questionnaire section to the Traditional Chinese output.
- If the request asks only for `Traditional Chinese Summary`, keep Section 11
  as summary-only (Executive Summary + PQRE Recommendation).

Even when `Risk Assessment` is not one of the requested output sections, still
use `KnowledgeBase/risk_scoring_criteria.md` internally to determine risk tier,
Action Required, and recommendation.

For Risk Assessment, include an RPN table with:

| Domain | Severity (S) | Occurrence (O) | Detection (D) | RPN | Data Confidence | Risk Tier |
|--------|---------------|----------------|---------------|-----|-----------------|-----------|

Email/output gate:

- Any email-style output must be draft only.
- Include: `⚠️ DRAFT — DO NOT SEND — Human approval required before any external communication.`
