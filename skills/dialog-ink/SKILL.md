---
name: dialog-ink
description: "Use when: (1) writing dialogue scenes between characters, (2) staging physical movement and spatial action during exchanges, (3) creating raw scene material for prose romanticization"
---

**`[DIALOG]`** — Display this immediately.

## LOAD AGENT

Read `skills/dialog-ink/agents/agent-dialog-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "dialog-ink"`. Agent works in its own context.

## OPTIONS

| Mode    | Trigger                                                          | Output                 |
| ------- | ---------------------------------------------------------------- | ---------------------- |
| `scene` | Default — "écris une scène", "dialogue entre X et Y"             | Semi-theatrical script |
| `pass`  | "pass", "--pass", user provides existing prose to analyze        | Annotated diagnostic   |

**`--check`:** Strict context verification BEFORE writing. Combines with any mode. If no context provided: signal, request material.

## REFERENCES

| Mode/Flag | Rules loaded |
| --------- | ------------ |
| `scene` | none |
| `pass` | `dialog-ink-pass-rules.md` |
| `--check` | `dialog-ink-rules.md` |

Rules path: `skills/dialog-ink/references/{name}.md`

`--check` combines with any mode: `scene --check`, `pass --check`.

## OUTPUT

**File output:** User provides a file path → write there. No path → ask before creating.
