---
name: ink
description: "Use when: (1) writing narrative prose — scenes, chapters, continuations, (2) collaborative fiction — roleplay with NPCs and world, (3) character embodiment — first-person dialogue as a character"
---

# write-ink

**`[INK]`** — Always display this tag at the start of your first response.

## Load

Read `skills/write-ink/agents/agent-write-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "ink"`. Agent works in its own context.

## File Output

- **User provides a file path** → write there.
- **No file path provided** → ask the user where to write before creating any file.


## Modes

Mode detection → load matching rules file. Novel is the default and needs no additional rules.

| Mode       | Trigger                                                        | Rules loaded                  |
| ---------- | -------------------------------------------------------------- | ----------------------------- |
| `novel`    | Default — scene writing, chapter continuation, narrative prose | none                          |
| `roleplay` | "On joue", collaborative fiction, user plays a character       | `write-ink-roleplay-rules.md` |
| `puppet`   | "Parle-moi en tant que [personnage]", character embodiment     | `write-ink-puppet-rules.md`   |

Rules path: `skills/write-ink/references/write-ink-{mode}-rules.md`

## Option: --check

| Flag      | Trigger                                                                   | Effect                                                                                           |
| --------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `--check` | User says "check", "--check", or explicitly requests context verification | Loads `skills/write-ink/references/write-ink-preflight-rules.md`. Strict verification BEFORE writing. |

`--check` combines with any mode: `novel --check`, `roleplay --check`, `puppet --check`.

Without `--check`: the agent uses context naturally — no systematic verification.

With `--check` and no context provided: signal, request material.
