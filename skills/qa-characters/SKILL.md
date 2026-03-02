---
name: qa-characters
description: "Use when: (1) evaluating character psychology and credibility, (2) assessing character arcs and transformation, (3) analyzing cast dynamics and relationships, (4) checking if a character knows/reacts to things they shouldn't"
---

# qa-characters

**`[CHARACTERS]`** — Always display this tag at the start of your first response.

## Load

Read `skills/qa-characters/agents/agent-qa-characters.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-characters"`. Agent works in its own context.

## Modes

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict per character). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic/assessment)

1. **Load rules files** according to material provided:

| Input                                     | Rules loaded                                     |
| ----------------------------------------- | ------------------------------------------------ |
| Single character (sheet + text)           | `depth-rules`                                    |
| Character across multiple scenes/chapters | `depth-rules` `evolution-rules`                  |
| Multiple characters interacting           | `depth-rules` `dynamics-rules`                   |
| Full cast analysis                        | `depth-rules` `evolution-rules` `dynamics-rules` |

Rules path: `skills/qa-characters/references/qa-characters-{name}-rules.md`

2. **Load report format** from `skills/qa-characters/references/qa-characters-report.md` + `references/qa-report-template.md`

3. **Output MUST follow the report template.** This is non-negotiable.

**Rules:**

- Always read the character sheet BEFORE the text. If no sheet provided, ask — or work from text alone and flag limitations.
- Depth-rules is always loaded in report mode. Evolution and dynamics depend on material.
- When evaluating arc: check multiple scenes before flagging inconsistency as error. Growth looks like inconsistency.
- When in doubt about scope, ask. Don't guess.

## Format selection (report mode)

| Input                                                         | Default format |
| ------------------------------------------------------------- | -------------- |
| Character + text for evaluation                               | Diagnostic     |
| Specific question ("is this arc earned?", "is she credible?") | Assessment     |
| User says "inline"                                            | Inline         |
