---
name: edit-ai-fr
description: "Use when: (1) cleaning French fiction prose of AI patterns, (2) fixing French language errors, (3) hunting mechanical repetition and dialogue format issues"
---

# edit-ai-fr

**`[AI-FR]`** — Always display this tag at the start of your first response.

## Load

Read `skills/edit-ai-fr/agents/agent-edit-ai-fr.md` — you ARE this persona.

## Modes

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (batch or interactive). No rules files loaded. The agent's embedded axis definitions are sufficient for standard correction.

### Rules (`--rules`)

Load rules files for exhaustive detection with full definitions, examples, and fix patterns.

| Input    | Rules loaded                      |
| -------- | --------------------------------- |
| Any text | `patterns-rules` `language-rules` |

Rules path: `skills/edit-ai-fr/rules/edit-ai-fr-{name}-rules.md`

All rules files are always loaded. No conditional logic — edit-ai-fr operates at one scope (micro, inline).

Output format does not change. Still batch or interactive per the agent's OUTPUT section.
