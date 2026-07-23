---
name: github-copilot-skill-builder
description: Convert domain knowledge and workflow information into reusable GitHub Copilot repository assets, including README, copilot instructions, agents, prompts, skills, and knowledge base files.
---

# GitHub Copilot Skill Builder

## Purpose

This skill helps users transform their engineering or business workflow into reusable GitHub Copilot repository assets.

The primary purpose of this skill is repository asset generation, not review report generation.

Repository assets include:

- README
- Agent definitions
- Prompt files
- Knowledge Base files
- Source catalogs
- Copilot instructions

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

## Repository Asset Generation

When the user requests repository generation, agent generation, prompt generation, knowledge base generation, README generation, or GitHub Copilot setup:

DO NOT generate only a review report.

Instead, generate complete repository assets based on skill-output-template.md.

Repository asset generation takes priority over risk review report generation.

Generate full contents for every required file.

Required output files:

- README.generated.md
- reliability-review-agent.generated.md
- reliability-review.prompt.generated.md
- domain_criteria.generated.md
- source_index.generated.yaml

For each file:

1. Show the target filename.
2. Generate complete file content.
3. Use markdown code blocks.
4. Do not summarize.
5. Do not return partial content.
6. Generate files in copy-and-paste-ready format.

The generated files must be consistent with:

- interview-template.md
- skill-output-template.md

If information is missing:

- Mark as TBD.
- Do not invent facts.
- Do not invent evidence.
- Do not invent source locations.

Output order:

1. Repository structure
2. README.generated.md
3. reliability-review-agent.generated.md
4. reliability-review.prompt.generated.md
5. domain_criteria.generated.md
6. source_index.generated.yaml
7. Review checklist

Repository asset generation is the preferred output whenever the user requests:

- Create a GitHub Copilot repository
- Generate an Agent
- Generate prompts
- Generate a knowledge base
- Generate repository assets
- Skill builder
- Repository template

Generate ALL files defined in skill-output-template.md.

Do not stop after generating README.

Continue until all files are completed.

Required completion criteria:

- README.generated.md
- copilot-instructions.generated.md
- reliability-review-agent.generated.md
- reliability-review.prompt.generated.md
- domain_criteria.generated.md
- source_index.generated.yaml

Output is not complete until every file has been generated.

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

## Full File Generation Rules

When generating repository assets:

ALWAYS generate complete file contents.

NEVER generate summaries.

NEVER truncate files.

NEVER replace sections with "...".

NEVER use placeholders such as:

- Content omitted
- Example only
- Continue here
- Remaining sections

Every generated file must be complete and ready for direct copy into GitHub.

For each file:

1. Display filename.
2. Generate full content.
3. Include all required sections.
4. Use proper markdown formatting.
5. Return the entire file in a single response.

The user should be able to copy each generated file directly into the repository without additional editing.

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

---

## File Creation Mode

When user requests repository generation:

Create new files in repository.

Never overwrite existing files.

Never modify:

README.md

.github/copilot-instructions.md

.github/agents/*

.github/prompts/*

KnowledgeBase/*

reviews/*

Create only new files under:

generated/

If generated folder does not exist:

create it.

All generated files must use:

.generated.md
.generated.yaml

suffix.

---

## Safe Repository Write Mode

When user explicitly requests file creation:

Create NEW files only.

Never overwrite existing files.

Never modify:

README.md

.github/copilot-instructions.md

.github/agents/*

.github/prompts/*

KnowledgeBase/*

reviews/*

Always write generated assets under:

generated/

If the folder does not exist:

create it.

Use file suffix:

.generated.md
.generated.yaml

Examples:

generated/reliability-review/README.generated.md

generated/reliability-review/copilot-instructions.generated.md

generated/reliability-review/reliability-review-agent.generated.md

generated/reliability-review/reliability-review.prompt.generated.md

generated/reliability-review/domain_criteria.generated.md

generated/reliability-review/source_index.generated.yaml

---

## Pull Request Mode

When repository write is requested:

1. Generate repository assets.
2. Create files only under generated/.
3. Present file list to user.
4. Request user review.
5. User approves.
6. Create Pull Request.
7. Human review before merge.

Never directly modify production repository assets.

Never directly overwrite:

README.md

.github/copilot-instructions.md

.github/agents/*

.github/prompts/*

KnowledgeBase/*

---

## Production Promotion Mode

Only after human approval:

generated/reliability-review/*.generated.*

can be copied into:

README.md

.github/agents/

.github/prompts/

KnowledgeBase/

Production promotion must be a separate step.

Do not automatically replace production files.

---

## Agent Write Permission Rules

Default mode:

- Generate content only.
- Do not create files.
- Do not modify repository.

If the user explicitly requests:

- Create files
- Write files
- Save files
- Create repository assets

Then:

1. Present planned file list.
2. Confirm target folder.
3. Create files only under generated/.
4. Never overwrite existing files.
5. Never modify production repository assets.

Production assets include:

README.md

.github/copilot-instructions.md

.github/agents/*

.github/prompts/*

KnowledgeBase/*

reviews/*

Repository write operations must be limited to:

generated/

Examples:

generated/reliability-review/

generated/regulatory-review/

generated/mechanical-review/

generated/thermal-review/

generated/si-review/
