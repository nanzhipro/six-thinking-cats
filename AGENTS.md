# Project Guidelines

## Repo Shape

- This repository is a prompt-and-reference workspace, not an application codebase.
- The primary deliverable is [SKILL.md](./SKILL.md); the framework details live in [references/framework.md](./references/framework.md).
- Prefer updating existing prompt docs over adding new files unless the guidance is clearly reusable and too detailed for [SKILL.md](./SKILL.md).

## Editing Priorities

- Preserve the YAML frontmatter at the top of [SKILL.md](./SKILL.md); keep `name`, `description`, and trigger phrases aligned with the skill's purpose.
- Follow the link-don't-embed rule: if theory or detailed definitions already exist in [references/framework.md](./references/framework.md), reference that file instead of duplicating long explanations.
- Keep [SKILL.md](./SKILL.md) focused on invocation cues, workflow steps, and non-negotiable constraints.

## Workflow Constraints

- If the user has not stated the decision they need help with, the skill must ask for that input before any analysis starts.
- Before asking follow-up questions, the agent must perform the internal "场景深度思考" step to identify scenario-specific variables and avoid template-driven prompts.
- This skill uses a parent-agent orchestration model: only the parent agent talks to the user; cat subagents do analysis only.
- Ask at most two user-facing questions at a time.
- Prefer choice-based prompts over open text when practical.
- Treat the "信息质量三原则" as hard requirements: push for specifics, separate facts from assumptions, and call out unknown-but-important gaps.
- Before launching any cat subagent, collect all necessary information and package it into a shared brief used by every cat.
- The red-cat stage must still include one explicit user-facing question about feelings, intuition, or hidden concerns, but it must be asked by the parent agent before subagents start.
- White, yellow, black, red, and green cats should run in separate subagents in parallel once the shared brief is complete.
- Cat subagents must not ask the user follow-up questions or wait for additional user input.
- Only the final blue-cat stage may integrate outputs across cats.
- The final deliverable must include a Mermaid decision tree derived from the analysis rather than a generic flowchart.

## Validation

- There is no build, test, or lint pipeline in this repo.
- After editing prompt files, validate by checking that frontmatter is still valid Markdown YAML, required referenced files still exist, and the mandatory workflow stages remain intact.
- If you add or move supporting material, keep it under `references/` and update links from [SKILL.md](./SKILL.md).
