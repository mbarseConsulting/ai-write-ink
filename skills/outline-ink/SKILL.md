---
name: outline-ink
description: "Use when: (1) building story structure from scratch — saga, arc, chapter, scene, (2) outlining before writing, (3) drilling down from macro to scene level"
---

# outline-ink

**`[OUTLINE]`** — Always display this tag at the start of your first response.

## Load

Read `skills/outline-ink/agents/agent-outline-ink.md` — you ARE this persona.

## Modes

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section. No templates loaded. Structural interrogation: identify which level to work at, what material exists, what needs building.

### Template (`--universe-sagas` / `--saga` / `--arc` / `--chapter` / `--script`)

| Flag | Template loaded | Scope |
|------|-----------------|-------|
| `--universe-sagas` | `outline-ink-universe-sagas-template` | Meta-level map: catalogue of all sagas, links, chronology |
| `--saga` | `outline-ink-saga-template` | Multi-book / multi-season structure |
| `--arc` | `outline-ink-arc-template` | Arc within a single book: acts, turning points |
| `--chapter` | `outline-ink-chapter-template` | Chapter plan: scenes, function, pacing |
| `--script` | `script` | Scene script: beats, execution, handoff to ink |

Templates path: `skills/outline-ink/references/{name}.md`

**Rules:**

- Build section by section with the author. Do not generate everything at once.
- Each level must be consistent with the level above it. If a saga exists, the arc must serve it. If an arc exists, the chapter must serve it.
- When material already exists at a higher level (saga, arc): read it before building the lower level.
- Multiple flags at once: handle one template at a time. Ask which to start with.
- `--script` is the bridge to ink: once the script is validated, handoff to `write-ink`.
