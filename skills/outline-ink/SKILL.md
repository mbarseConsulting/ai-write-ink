---
name: outline-ink
description: "Use when: (1) building story structure from scratch — saga, arc, chapter, scene, (2) outlining before writing, (3) drilling down from macro to scene level"
---

## LOAD AGENT

Read `skills/outline-ink/agents/agent-outline-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-outline-ink"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section. No templates loaded. Structural interrogation: identify which level to work at, what material exists, what needs building.

### Template (`--universe-sagas` / `--saga` / `--arc` / `--chapter` / `--script`)

Loads the matching structural template. Build section by section with the author.

## SUPPORTING FILES

### References

**Loaded when a template flag is provided.**

| Flag | Template loaded | Scope |
|------|-----------------|-------|
| `--universe-sagas` | `outline-ink-universe-sagas-template` | Meta-level map: catalogue of all sagas, links, chronology |
| `--saga` | `outline-ink-saga-template` | Multi-book / multi-season structure |
| `--arc` | `outline-ink-arc-template` | Arc within a single book: acts, turning points |
| `--chapter` | `outline-ink-chapter-template` | Chapter plan: scenes, function, pacing |
| `--script` | `script` | Scene script: beats, execution, handoff to ink |

Templates path: `skills/outline-ink/references/{name}.md`

Multiple flags at once: handle one template at a time. Ask which to start with.

## ACTIVATION - DEACTIVATION - HANDOFF

**`[OUTLINE]`** — Display this immediately.

**Applies to this response only. Auto-resets after.**
