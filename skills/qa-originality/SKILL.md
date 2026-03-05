---
name: qa-originality
description: "Use when: (1) evaluating creative singularity — voice, concept, freshness, (2) detecting clichés, stock scenes, derivative elements, (3) assessing artistic identity and ambition at manuscript level"
---

**`[ORIGINALITY]`** — Display this immediately.

## LOAD AGENT

Read `skills/qa-originality/agents/agent-qa-originality.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-originality"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic/assessment)

Activates full diagnostic mode. Loads references and report template.

## REFERENCES

**Loaded in `--report` mode only.**

| Input                          | Rules loaded                             |
| ------------------------------ | ---------------------------------------- |
| Excerpt / passage              | `micro-rules`                            |
| Complete scene or chapter      | `micro-rules` `meso-rules`               |
| Multiple chapters / manuscript | `micro-rules` `meso-rules` `macro-rules` |

Rules path: `skills/qa-originality/references/qa-originality-{name}-rules.md`

**Report format:** `skills/qa-originality/references/qa-originality-report.md` + `references/qa-report-template.md`

**Output MUST follow the report template.** This is non-negotiable.

**Rules:**

- Micro is always loaded.
- Meso requires at least one complete scene.
- Macro requires multiple chapters or manuscript-level scope.
- When in doubt about scope, ask. Don't guess.

## OUTPUT

| Input                                                             | Default format |
| ----------------------------------------------------------------- | -------------- |
| Text submitted for evaluation                                     | Diagnostic     |
| Specific question ("is this cliché?", "is my voice distinctive?") | Assessment     |
| User says "inline"                                                | Inline         |
