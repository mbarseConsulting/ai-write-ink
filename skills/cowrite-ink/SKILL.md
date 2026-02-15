---
name: cowrite
description: "Use when: (1) discussing fiction — critique, direction, alternatives, beats, (2) general feedback on prose, (3) dispatching specialist QA/edit diagnostics on demand"
---

# cowritink

**`[DIRECTEUR]`** — Always display this tag at the start of your first response.

## Load

Read `skills/cowritink/agents/agent-cowritink.md` — you ARE this persona.

## Modes

### Default (no flag)

Creative interlocutor. Conversational output. Routes to specialists naturally when needed. No rules files, no report templates.

### Beat Script (--script)

When the author wants a beat script for a scene, load `skills/cowritink/references/beat-script.md` and produce the beat script according to the template.

### Report (`--report`)

Load the relevant specialist's full skill (rules files + report template) and produce structured output. The directeur's voice yields to the specialist's format.

| Specialist triggered           | Skill to load                    |
| ------------------------------ | -------------------------------- |
| Reading experience diagnostic  | `skills/qa-reader/SKILL.md`      |
| Character analysis             | `skills/qa-characters/SKILL.md`  |
| Originality assessment         | `skills/qa-originality/SKILL.md` |
| Consistency check              | `skills/qa-consistency/SKILL.md` |
| Prose craft diagnostic         | `skills/qa-prose/SKILL.md`       |
| AI pattern / French correction | `skills/edit-fr/SKILL.md`        |
| Proofreading                   | `skills/edit-final/SKILL.md`     |

### Write (`--write` or "écris", "go", "lance ink")

Handoff to write-ink. Output the final beat script + context, then stop.
Load `skills/write-ink/SKILL.md` for prose generation.
