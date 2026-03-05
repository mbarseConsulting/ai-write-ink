---
name: dialog-ink
description: "Use when: (1) writing dialogue scenes between characters, (2) staging physical movement and spatial action during exchanges, (3) creating raw scene material for prose romanticization"
---

# dialog-ink

**`[DIALOG]`** — Always display this tag at the start of your first response.

## Load

Read `skills/dialog-ink/agents/agent-dialog-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "dialog-ink"`. Agent works in its own context.

## File Output

- **User provides a file path** → write there.
- **No file path provided** → ask the user where to write before creating any file.

## Modes

Mode detection → load matching rules file. Default mode is `scene` (raw script creation).

| Mode    | Trigger                                                          | Rules loaded              | Output                 |
| ------- | ---------------------------------------------------------------- | ------------------------- | ---------------------- |
| `scene` | Default — "écris une scène", "dialogue entre X et Y"             | none                      | Semi-theatrical script |
| `pass`  | "pass", "--pass", user provides existing prose to analyze        | `dialog-ink-pass-rules.md`| Annotated diagnostic   |

Rules path: `skills/dialog-ink/references/dialog-ink-{mode}-rules.md`

## Option: --check

| Flag      | Trigger                                                                   | Effect                                                                                           |
| --------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `--check` | User says "check", "--check", or explicitly requests context verification | Loads `skills/dialog-ink/references/dialog-ink-rules.md`. Strict verification BEFORE writing. |

`--check` combines with any mode: `scene --check`, `pass --check`.

Without `--check`: the agent uses context naturally — no systematic verification.

With `--check` and no context provided: signal, request material.
