---
name: arch-ink
description: "Use when: (1) challenging a story's structure before writing, (2) diagnosing act breaks, midpoints, and throughlines, (3) evaluating character arc structure when arc material is provided, (4) validating a script or chapter plan before writing"
---

## LOAD AGENT

Read `skills/arch-ink/agents/agent-arch-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-arch-ink"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (interrogation or emoji-block diagnostic). No rules files loaded. No report template.

### Report (`--report`)

Full structured report. Loads references and report template.

## SUPPORTING FILES

### References

**Loaded in `--report` mode only:**

| Input | Rules loaded |
| ----- | ------------ |
| Synopsis / outline only | `structure-rules` |
| Character arc included | `structure-rules` + `arc-rules` |
| Script / chapter plan | `script-rules` |
| Script + arc outline | `script-rules` + `structure-rules` |
| Script + character arc | `script-rules` + `arc-rules` |

Rules path: `skills/arch-ink/references/arch-ink-{name}-rules.md`

**Report format:** `skills/arch-ink/references/arch-ink-report.md`

Structure-rules is always loaded for synopsis/outline input. Script-rules is always loaded for script/chapter plan input.

## OUTPUT

**In `--report` mode, output MUST follow the report template.** This is non-negotiable.

| Input | Default format |
| ----- | -------------- |
| Synopsis or outline submitted | Diagnostic |
| Script or chapter plan submitted | Script Diagnostic |
| Specific structural question ("does my act 2 work?") | Assessment |
| User says "inline" | Inline |

## ACTIVATION - DEACTIVATION - HANDOFF

**`[ARCH-INK]`** — Display this immediately.

**Applies to this response only. Auto-resets after.**
