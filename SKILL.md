---
name: writing-for-agents
description: Write or revise skills and AGENTS.md/CLAUDE.md instructions with clear triggers, executable steps and scoped reference loading.
---

# Write instructions an agent can execute
1. Define the real request, required inputs, allowed effects, output and a checkable completion condition. Preserve the user’s scope and existing capabilities.
2. Make discovery specific: a short description names the capability and real triggers. Avoid catchalls that load the skill for unrelated work.
3. Use plain sentences and concrete verbs. Put actions in order. State each branch as **when X, read/do Y**; do not hide required gates behind vague references.
4. Keep universally needed constraints and high-consequence stop conditions in the entrypoint. Move substantial branch-only recipes/templates to linked references. Do not create a router for a short standalone skill.
5. Give runnable commands with quoted paths. Define variables in the same shell or use literal paths. Distinguish illustrative placeholders from commands to run. Name only available tools; define a missing-tool fallback.
6. Keep each rule/fact in one authoritative place. Link it where needed; avoid repeated policy, history, persona text and speculative edge cases. Shortening must preserve units, negation, validation and user-selected behavior.
7. For invocation/frontmatter/router changes, read [host mechanics](SKILL-MECHANICS.md). Preserve automatic discovery unless the user explicitly requests otherwise; Claude/Codex/AGY settings differ.
8. Read back the actual files. Validate metadata/links and exercise representative normal/failure cases. For complex/risky workflows, use an independent test with only the request, skill and raw fixture; do not give the expected answer. Respect current delegation permissions.

For small models, prefer one action per step, explicit inputs and outputs, short branches and literal commands over metaphors or implicit context. Do not compress into broken grammar or abbreviations the model must decode. Reuse unchanged instructions already in context; load only references needed by the current branch.
