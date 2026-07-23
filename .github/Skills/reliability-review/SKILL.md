---
name: reliability-review
description: Review reliability reports, identify qualification gaps, evaluate risk level, and prepare PQRE executive summary.
---

# Workflow

1. Read reliability report.

2. Load references:

   - ../../KnowledgeBase/Rules/Intel Rules/intel_rule_catalog.yaml
   - ../../KnowledgeBase/Rules/Intel Rules/risk_scoring_criteria.md
   - ../../KnowledgeBase/Rules/Intel Rules/pqre_signoff_criteria.md
   - ../../KnowledgeBase/platform/platform_alias.yaml

3. Identify:
   - Test coverage
   - Qualification status
   - Open gaps
   - Failure mechanisms

4. Evaluate risk according to risk_scoring_criteria.

5. Verify qualification readiness according to pqre_signoff_criteria.

6. Generate:
   - Executive Summary
   - Key Findings
   - Open Actions
   - Recommendation
