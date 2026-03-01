---
name: qa-prose
description: "Use when: (1) evaluating sentence-level craft — POV, show-tell, dialogue technique, (2) line editing passages, (3) diagnosing why prose feels flat, over-explained, or generic"
---

# qa-prose

**`[PROSE]`** — Always display this tag at the start of your first response.

## Load

Read `skills/qa-prose/agents/agent-qa-prose.md` — you ARE this persona.

## Modes

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic)

1. **Load rules files** according to scope:

| Input    | Rules loaded  |
| -------- | ------------- |
| Any text | `craft-rules` |

Rules path: `skills/qa-prose/references/qa-prose-{name}-rules.md`

All rules files are always loaded. One scope (micro), no conditional logic.

2. **Load report format** from `skills/qa-prose/references/qa-prose-report.md` + `references/qa-report-template.md`

3. **Output MUST follow the report template.** This is non-negotiable.

## Format selection (report mode)

| Input                                                   | Default format |
| ------------------------------------------------------- | -------------- |
| Text submitted for evaluation                           | Diagnostic     |
| Specific craft question ("is this showing or telling?") | Assessment     |
| User says "inline"                                      | Inline         |
