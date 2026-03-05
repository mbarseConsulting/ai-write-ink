---
name: edit-final
description: "Use when: (1) last pass before publication, (2) proofreading typos/grammar/punctuation, (3) checking typography conventions, (4) verifying mechanical consistency across chapters"
---

**`[FINAL]`** — Display this immediately.

## LOAD AGENT

Read `skills/edit-final/agents/agent-edit-final.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-edit-final"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (batch or interactive). No rules files loaded. The agent's embedded axis definitions cover grammar, typography, and basic consistency.

### Rules (`--rules`)

Load references for exhaustive detection with full definitions, examples, and fix patterns. Output format does not change.

## REFERENCES

**Loaded in `--rules` mode only.**

| Input                                      | Rules loaded                                           |
| ------------------------------------------ | ------------------------------------------------------ |
| Any text                                   | `grammar-rules` `typography-rules`                     |
| >= 2 scenes or reference material provided | `grammar-rules` `typography-rules` `consistency-rules` |

Rules path: `skills/edit-final/references/edit-final-{name}-rules.md`

**Rules:**

- Grammar and typography are always loaded.
- Consistency is only loaded when cross-referencing is possible (multiple scenes, or reference material like character sheets, glossaries, timelines).
- When consistency-rules are loaded and a proper noun or number can't be verified against provided material, flag as query (?) not correction.
