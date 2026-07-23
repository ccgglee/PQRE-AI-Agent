---
name: github-copilot-skill-builder
description: Convert domain knowledge and workflow information into reusable GitHub Copilot repository assets, including README, copilot instructions, agents, prompts, skills, and knowledge base files.
---

# GitHub Copilot Skill Builder

## Purpose

This skill helps users transform their engineering or business workflow into a reusable GitHub Copilot repository structure.

The skill guides the user through an interview process, captures domain-specific workflow knowledge, and generates starter repository assets for GitHub Copilot adoption.

---

## Required Reference Files

Before generating outputs, use the following reference files in this skill folder:

1. `interview-template.md`
   - Use this file to collect user workflow information.
   - The interview should capture role, task, inputs, outputs, decision logic, evidence, guardrails, and knowledge sources.

2. `skill-output-template.md`
   - Use this file to define the required output files.
   - Generated outputs should follow this structure unless the user provides a different format.

---

## Workflow

When this skill is used, follow these steps:

1. Review `interview-template.md`.
2. Ask the user for missing workflow information.
3. Capture the user's role, task, decision criteria, required evidence, outputs, guardrails, and knowledge sources.
4. Review `skill-output-template.md`.
5. Generate starter content for the following files:
   - `README.md`
   - `.github/copilot-instructions.md`
   - `.github/agents/domain-agent.agent.md`
   - `.github/prompts/domain-review.prompt.md`
   - `KnowledgeBase/domain_criteria.md`
   - `KnowledgeBase/source_index.yaml`
6. Clearly separate confirmed facts from assumptions.
7. Mark missing information as `TBD`.
8. Do not invent evidence, criteria, or source locations.
9. Require human review before final approval or workflow signoff.

---

## Guardrails

Always follow these rules:

- Do not approve any engineering decision without required evidence.
- Do not treat assumptions as confirmed facts.
- Do not fabricate file names, source links, test results, or acceptance criteria.
- Use `TBD` when information is missing.
- Keep output structured and easy to review.
- Require human review for final signoff.
- For engineering workflows, preserve evidence traceability.
- For risk reviews, separate risk band, disposition, data confidence, and evidence gaps.

---

## Output Requirements

When generating repository assets:

- Use Markdown for `.md` files.
- Use YAML format for `.yaml` files.
- Use clear section headers.
- Use simple English unless the user requests another language.
- Include placeholders where user-specific content is missing.
- Keep generated files ready for copy and paste into GitHub.

---

## Recommended Output Order

Generate outputs in this order:

1. Repository structure
2. `README.md`
3. `.github/copilot-instructions.md`
4. `.github/agents/domain-agent.agent.md`
5. `.github/prompts/domain-review.prompt.md`
6. `KnowledgeBase/domain_criteria.md`
7. `KnowledgeBase/source_index.yaml`
8. Review checklist

---

## Review Checklist

Before finalizing the generated assets, check:

- Is the workflow purpose clear?
- Are inputs and outputs defined?
- Are decision rules documented?
- Are evidence requirements listed?
- Are guardrails included?
- Are human review gates included?
- Are unknown items marked as `TBD`?
- Are assumptions separated from confirmed facts?
