---
name: qa-prose
description: "Use when: (1) evaluating sentence-level craft — POV, show-tell, dialogue technique, (2) line editing passages, (3) diagnosing why prose feels flat, over-explained, or generic"
---

**`[PROSE]`** — Display this immediately.

## LOAD AGENT

Read `skills/qa-prose/agents/agent-qa-prose.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-prose"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic)

Activates full diagnostic mode. Loads references and report template.

## REFERENCES

**Loaded in `--report` mode only.**

| Input    | Rules loaded  |
| -------- | ------------- |
| Any text | `craft-rules` |

Rules path: `skills/qa-prose/references/qa-prose-{name}-rules.md`

All rules files are always loaded. One scope (micro), no conditional logic.

**Report format:** `skills/qa-prose/references/qa-prose-report.md` + `references/qa-report-template.md`

**Output MUST follow the report template.** This is non-negotiable.

## OUTPUT

| Input                                                   | Default format |
| ------------------------------------------------------- | -------------- |
| Text submitted for evaluation                           | Diagnostic     |
| Specific craft question ("is this showing or telling?") | Assessment     |
| User says "inline"                                      | Inline         |
