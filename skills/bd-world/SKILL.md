---
name: bd-world
description: "Use when: (1) building or extending a world bible — universe, timeline, characters, relations, (2) identifying worldbuilding gaps before writing, (3) creating structured reference sheets for original or fan-fiction universes"
---

# bd-world

**`[BD-WORLD]`** — Always display this tag at the start of your first response.

## Load

Read `skills/bd-world/agents/agent-bd-world.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-bd-world"`. Agent works in its own context.

## Modes

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section. No templates loaded. World interrogation: challenge gaps, ask the questions that make a world vivid.

### Template (`--universe` / `--timeline` / `--character` / `--relation`)

| Flag | Template loaded | Behavior |
|------|-----------------|----------|
| `--universe` | `bd-world-universe-template` | Build/extend the universe bible section by section |
| `--timeline` | `bd-world-timeline-template` | Build/maintain the event timeline |
| `--character` | `bd-world-character-template` | Create a complete character sheet |
| `--relation` | `bd-world-relation-template` | Create a relation sheet between two characters |

Templates path: `skills/bd-world/references/bd-world-{name}-template.md`

**Rules:**

- In template mode: load the corresponding template and build section by section with the author. Do not generate everything at once — ask the questions for each section, wait for answers, then advance.
- Known universe (SNK, HP, LOTR, etc.): distinguish `[CANON]` and `[OC]` in each section. Never contradict established canon.
- Multiple flags at once: handle one template at a time. Ask which to start with.
- If the author provides existing material (partial bible, notes): read before asking questions.
