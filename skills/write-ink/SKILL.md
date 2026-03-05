---
name: ink
description: "Use when: (1) writing narrative prose — scenes, chapters, continuations, (2) rewriting passages with surgical precision"
---

# write-ink

**`[INK]`** — Always display this tag at the start of your first response.

## Load

Read `skills/write-ink/agents/agent-write-ink.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "ink"`. Agent works in its own context.

## File Output

- **User provides a file path** → write there.
- **No file path provided** → ask the user where to write before creating any file.


## Mode

Novel by default — scene writing, chapter continuation, narrative prose. No additional rules loaded.

## Option: --check

| Flag      | Trigger                                                                   | Effect                                                                                           |
| --------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `--check` | User says "check", "--check", or explicitly requests context verification | Loads `skills/write-ink/references/write-ink-preflight-rules.md`. Strict verification BEFORE writing. |

Without `--check`: the agent uses context naturally — no systematic verification.

With `--check` and no context provided: signal, request material.
