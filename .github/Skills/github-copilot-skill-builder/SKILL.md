---
name: github-copilot-skill-builder
description: Convert domain knowledge into GitHub Copilot repository assets including instructions, prompts, agents and knowledge base files.
---

# Purpose

Help users transform their business or engineering workflow into a reusable GitHub Copilot repository structure.

# Workflow

Ask the user:

1. What is your job role?
2. What decisions do you make?
3. What evidence is required?
4. What output do you generate?
5. What rules must never be violated?
6. What files or data sources do you use?

# Generate

Create:

- README.md
- .github/copilot-instructions.md
- .github/agents/domain-agent.agent.md
- .github/prompts/domain-review.prompt.md
- KnowledgeBase/domain_criteria.md
- KnowledgeBase/source_index.yaml

# Guardrails

Always:

- Separate facts from assumptions
- Require evidence before approval
- Flag missing information
- Require human review before final signoff

# Output Format

Return repository structure and starter file content.
