# Project Guidelines

## Repo Shape

- This repository is a prompt-and-reference workspace, not an application codebase.
- The primary deliverable is [SKILL.md](./SKILL.md); the framework details live in [references/framework.md](./references/framework.md).
- Prefer updating existing prompt docs over adding new files unless the guidance is clearly reusable and too detailed for [SKILL.md](./SKILL.md).

## Editing Priorities

- Preserve the YAML frontmatter at the top of [SKILL.md](./SKILL.md); keep `name`, `description`, and trigger phrases aligned with the skill's purpose.
- Follow the link-don't-embed rule: if theory or detailed definitions already exist in [references/framework.md](./references/framework.md), reference that file instead of duplicating long explanations.
- Keep [SKILL.md](./SKILL.md) focused on invocation cues, workflow steps, and non-negotiable constraints.
- Keep reusable subagent rules in [references/subagent-contract.md](./references/subagent-contract.md); use [SKILL.md](./SKILL.md) only to state where that contract is mandatory in the workflow.
- Preserve the distinction between de Bono's original Six Thinking Hats theory and this repository's default execution model; do not rewrite the repo's default orchestration as if it were the theory's only valid sequence.

## Workflow Constraints

- If the user has not stated the decision they need help with, the skill must ask for that input before any analysis starts.
- Before asking follow-up questions, the agent must perform the internal "场景深度思考" step to identify scenario-specific variables and avoid template-driven prompts.
- This skill uses a parent-agent orchestration model as its default execution pattern: only the parent agent talks to the user; cat subagents do analysis only.
- Ask at most two user-facing questions at a time.
- When asking the user, prefer the runtime's built-in user-input tool if one exists; only fall back to numbered plain text when no such tool is available.
- If the user-input tool supports batching, combine all applicable questions from the current round into one call; if it only supports single-question mode, ask them one at a time in priority order.
- If the user-input tool uses structured options, only provide `options` when a question truly has at least two valid choices; otherwise omit `options` and ask for freeform input or put the suggestion in the helper text.
- If a turn contains direct user-facing question(s), the parent agent must end that turn after the question(s) and wait for the user's real reply; never self-answer, simulate a reply, or continue analysis in the same turn.
- Prefer choice-based prompts over open text when practical.
- Treat the "信息质量三原则" as hard requirements: push for specifics, separate facts from assumptions, and call out unknown-but-important gaps.
- Before launching any cat subagent, collect all necessary information and package it into a shared brief used by every cat.
- Every subagent must use the same model as the parent agent; do not silently switch to a weaker or different model for any cat stage.
- If the decision depends on latest public facts such as policy, school admission rules, prices, regulation, or market statistics, the white-cat stage must use runtime-available research tools to verify them, or explicitly report that the runtime lacks this capability.
- Only the white-cat stage may do limited runtime verification of public facts; the other cats must still operate only on the shared brief.
- The red-cat stage must still include one explicit user-facing question about feelings, intuition, or hidden concerns, but it must be asked by the parent agent before subagents start.
- White, yellow, black, red, and green cats should run in separate subagents in parallel once the shared brief is complete.
- Cat subagents must not ask the user follow-up questions or wait for additional user input.
- In this repository's default workflow, the final blue-cat stage is where outputs across cats are integrated and organized; do not describe blue-cat as an extra truth source or final arbiter standing above the other hats.
- The final deliverable must include a Mermaid decision tree derived from the analysis rather than a generic flowchart.

## Validation

- There is no build, test, or lint pipeline in this repo.
- After editing prompt files, validate by checking that frontmatter is still valid Markdown YAML, required referenced files still exist, and the mandatory workflow stages remain intact.
- If you add or move supporting material, keep it under `references/` and update links from [SKILL.md](./SKILL.md).
