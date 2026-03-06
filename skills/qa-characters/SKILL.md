---
name: qa-characters
description: "Use when: (1) evaluating character psychology and credibility, (2) assessing character arcs and transformation, (3) analyzing cast dynamics and relationships, (4) checking if a character knows/reacts to things they shouldn't"
---

## LOAD AGENT

Read `skills/qa-characters/agents/agent-qa-characters.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-characters"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict per character). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic/assessment)

Activates full diagnostic mode. Loads references and report template.

## SUPPORTING FILES

### References

**Loaded in `--report` mode only:**

| Input                                     | Rules loaded                                     |
| ----------------------------------------- | ------------------------------------------------ |
| Single character (sheet + text)           | `depth-rules`                                    |
| Character across multiple scenes/chapters | `depth-rules` `evolution-rules`                  |
| Multiple characters interacting           | `depth-rules` `dynamics-rules`                   |
| Full cast analysis                        | `depth-rules` `evolution-rules` `dynamics-rules` |

Rules path: `skills/qa-characters/references/qa-characters-{name}-rules.md`

**Report format:** `skills/qa-characters/references/qa-characters-report.md` + `references/qa-report-template.md`

Depth-rules is always loaded in report mode. Evolution and dynamics depend on material.

## OUTPUT

**In `--report` mode, output MUST follow the report template.** This is non-negotiable.

| Input                                                         | Default format |
| ------------------------------------------------------------- | -------------- |
| Character + text for evaluation                               | Diagnostic     |
| Specific question ("is this arc earned?", "is she credible?") | Assessment     |
| User says "inline"                                            | Inline         |

## ACTIVATION - DEACTIVATION - HANDOFF

**`[CHARACTERS]`** — Display this immediately.

**Applies to this response only. Auto-resets after.**
