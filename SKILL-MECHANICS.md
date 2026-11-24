# Skill mechanics

The skill-specific branch of [`writing-for-agents`](SKILL.md): what changes when the document is a skill (frontmatter, the invocation choice, and router skills). Everything else about writing it is the universal reference in `SKILL.md`.

## Invocation

Keep normal automatic discovery enabled unless the user explicitly requests an explicit-only skill. A description should explain the capability and triggers; it is not a mechanism for imposing a workflow on unrelated requests.

Invocation controls belong to the host, not to the shared Markdown format:

| Host | Explicit-only setting | Meaning and limits |
|------|-----------------------|--------------------|
| Claude Code | `disable-model-invocation: true` in SKILL.md frontmatter, when supported by the installed host | Suppresses automatic skill invocation; preserve the existing setting unless the user requests a change |
| Codex | `policy.allow_implicit_invocation: false` in `agents/openai.yaml` | Use only at the user’s explicit request; preserve unrelated UI/dependency fields |
| AGY or another host | Inspect its actual supported metadata and tools | Do not assume Claude or Codex flags work; preserve automatic discovery if support is unknown |

A user can still request a discoverable skill explicitly. Do not remove its description or disable automatic discovery merely because it is specialized, sensitive or usually called by name. Permission for external side effects belongs in the workflow at the relevant action, independently of invocation metadata.

For a shared skill, retain compatible metadata that another host needs and distinguish unknown host extensions from malformed YAML. Check how the current host loads the skill; one validator is not proof of behavior in all hosts. Refer to your agent runtime's guidance for tool selection.

A skill may point to another skill’s instructions or to a plain reference. Directly reading a reference is different from invoking a disabled skill through a host tool; do not claim invocation controls make files inaccessible.

## Splitting by invocation

The invocation cut of splitting (the sequence cut lives in `SKILL.md`): split off a separately discoverable skill when you have a distinct leading word that should trigger it on its own (a trigger word you actually use in your prompts), or another skill must reach it. You pay context load for the new always-loaded description, so that independent reach has to be worth it.

## Router skills

Use a router only when multiple substantial workflows need an entrypoint and it makes selection easier. Name each branch and the condition for loading it; read only the relevant material. Check the current host’s actual invocation controls before invoking another skill. A short standalone skill needs no extra router layer.
