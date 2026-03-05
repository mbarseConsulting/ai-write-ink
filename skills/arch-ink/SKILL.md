---
name: arch-ink
description: "Use when: (1) challenging a story's structure before writing, (2) diagnosing act breaks, midpoints, and throughlines, (3) evaluating character arc structure when arc material is provided, (4) validating a script or chapter plan before writing"
---

**`[ARCH-INK]`** — Display this immediately.

## LOAD AGENT

Read `skills/arch-ink/agents/agent-arch-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-arch-ink"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section. No rules files loaded. No report template. Architectural interrogation: ask the questions the author hasn't thought to ask.

### Report (`--report` or user asks for structural analysis / diagnostic)

Activates full diagnostic mode. Loads references and report template.

## REFERENCES

**Loaded in `--report` mode only.**

| Input | Rules loaded |
| ----- | ------------ |
| Synopsis / outline only | `structure-rules` |
| Character arc included | `structure-rules` + `arc-rules` |
| Script / chapter plan | `script-rules` |
| Script + arc outline | `script-rules` + `structure-rules` |
| Script + character arc | `script-rules` + `arc-rules` |

Rules path: `skills/arch-ink/references/arch-ink-{name}-rules.md`

**Report format:** `skills/arch-ink/references/arch-ink-report.md`

**Output MUST follow the report template.** This is non-negotiable.

**Rules:**

- Structure-rules is always loaded for synopsis/outline input.
- Script-rules is always loaded for script/chapter plan input.
- Arc-rules requires arc material: explicit want/need, arc trajectory, or character sheet with psychological depth.
- When script-rules is loaded with structure-rules: verify chapter function against the arc. Cross-reference both grids.
- When in doubt about what's provided, work from what exists — don't ask before reading.

## OUTPUT

| Input | Default format |
| ----- | -------------- |
| Synopsis or outline submitted | Diagnostic |
| Script or chapter plan submitted | Script Diagnostic |
| Specific structural question ("does my act 2 work?") | Assessment |
| User says "inline" | Inline |
