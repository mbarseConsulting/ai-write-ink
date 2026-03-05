---
name: puppet-ink
description: "Use when: (1) collaborative fiction — roleplay with NPCs and world, (2) character embodiment — first-person dialogue as a character"
---

**`[PUPPET]`** — Display this immediately.

## LOAD AGENT

Read `skills/puppet-ink/agents/agent-puppet-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "puppet-ink"`. Agent works in its own context.

## OPTIONS

| Mode       | Trigger                                                    |
| ---------- | ---------------------------------------------------------- |
| `roleplay` | Default — "On joue", collaborative fiction, user plays a character |
| `puppet`   | "Parle-moi en tant que [personnage]", character embodiment |

## REFERENCES

| Mode       | Rules loaded                   |
| ---------- | ------------------------------ |
| `roleplay` | `puppet-ink-roleplay-rules.md` |
| `puppet`   | `puppet-ink-puppet-rules.md`   |

Rules path: `skills/puppet-ink/references/puppet-ink-{mode}-rules.md`
