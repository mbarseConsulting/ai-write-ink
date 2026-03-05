---
name: qa-consistency
description: "Use when: (1) verifying continuity — objects, injuries, timeline, locations, (2) checking lore and worldbuilding coherence, (3) tracking narrative arcs for abandoned threads, (4) fact-checking historical or procedural accuracy"
---

**`[CONSISTENCY]`** — Display this immediately.

## LOAD AGENT

Read `skills/qa-consistency/agents/agent-qa-consistency.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-consistency"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (dual-cite findings, queries, triage, verdict). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic)

Activates full diagnostic mode. Loads references and report template.

## REFERENCES

**Loaded in `--report` mode only.**

| Input                          | Rules loaded                             |
| ------------------------------ | ---------------------------------------- |
| Single scene                   | `micro-rules`                            |
| 2+ scenes / chapter            | `micro-rules` `meso-rules`               |
| Multiple chapters / manuscript | `micro-rules` `meso-rules` `macro-rules` |

Rules path: `skills/qa-consistency/references/qa-consistency-{name}-rules.md`

**Report format:** `skills/qa-consistency/references/qa-consistency-report.md` + `references/qa-report-template.md`

**Output MUST follow the report template.** This is non-negotiable.

**Rules:**

- Micro is always loaded.
- Meso requires at least 2 scenes.
- Macro requires multiple chapters or manuscript-level scope.
- When reference material exists (character sheets, timeline docs, lore docs, maps), read them BEFORE the text.
- When in doubt about scope, ask. Don't guess.

## OUTPUT

| Input                                                                     | Default format |
| ------------------------------------------------------------------------- | -------------- |
| Text submitted for continuity check                                       | Diagnostic     |
| Specific question ("does the timeline hold?", "is anyone in two places?") | Assessment     |
| User says "inline"                                                        | Inline         |

Default is Diagnostic (not Assessment) because consistency work is finding-driven — the editor needs to show every violation with dual citations.
