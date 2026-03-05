---
name: edit-ai-fr
description: "Use when: (1) cleaning French fiction prose of AI patterns, (2) fixing French language errors, (3) hunting mechanical repetition and dialogue format issues"
---

**`[AI-FR]`** — Display this immediately.

## LOAD AGENT

Read `skills/edit-ai-fr/agents/agent-edit-ai-fr.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-edit-ai-fr"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (batch or interactive). No rules files loaded. The agent's embedded axis definitions are sufficient for standard correction.

### Rules (`--rules`)

Load references for exhaustive detection with full definitions, examples, and fix patterns. Output format does not change.

## REFERENCES

**Loaded in `--rules` mode only.**

| Input    | Rules loaded                      |
| -------- | --------------------------------- |
| Any text | `patterns-rules` `language-rules` |

Rules path: `skills/edit-ai-fr/references/edit-ai-fr-{name}-rules.md`

All rules files are always loaded. No conditional logic — edit-ai-fr operates at one scope (micro, inline).
