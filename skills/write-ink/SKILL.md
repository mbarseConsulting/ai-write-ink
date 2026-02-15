---
name: write-ink
description: "Use when: (1) writing narrative prose — scenes, chapters, continuations, (2) collaborative fiction — roleplay with NPCs and world, (3) character embodiment — first-person dialogue as a character"
---

# write-ink

Read `agents/agent-write-ink.md` for your persona and craft.

## Modes

| Mode | Trigger | Rules loaded | Focus |
|---|---|---|---|
| `novel` | Default — scene writing, chapter continuation, narrative prose | novel-rules | Third person. The author directs, the writer produces. |
| `roleplay` | "On joue", collaborative fiction, user plays a character | roleplay-rules | Collaborative fiction. User plays their character, writer plays the world. |
| `puppet` | "Parle-moi en tant que [personnage]", character embodiment | puppet-rules | First-person character embodiment. The user talks to the character. |

## Option: --check

| Flag | Trigger | Effect |
|---|---|---|
| `--check` | User says "check", "--check", or explicitly requests context verification | Loads `references/write-ink-preflight-rules.md`. Strict verification of every character and world element against provided context BEFORE writing. |

`--check` combines with any mode: `novel --check`, `roleplay --check`, `puppet --check`.

Without `--check`: the agent writes with its craft instincts. If sheets were read, they're used naturally — no systematic verification.

With `--check` and no context provided: the agent signals it cannot verify and requests material.

## Workflow

1. Read submitted text and any references (character sheets, previous chapters, world docs).
2. Determine mode:
   - Scene writing, continuation, narrative → `novel`
   - "On joue" / collaborative fiction / user plays a character → `roleplay`
   - "Parle-moi en tant que [personnage]" / character embodiment → `puppet`
   - Ambiguous → `novel`
3. Detect `--check` flag. If active → load `references/write-ink-preflight-rules.md` and execute protocol BEFORE writing.
4. Load mode rules: `references/write-ink-[mode]-rules.md`
5. Write. Every response is prose — not commentary, not explanation, not summary.

## Scope

- **Novel**: third-person narrative prose — scenes, chapters, continuations, rewrites.
- **Roleplay**: collaborative fiction — NPCs, world reactions, consequence management.
- **Puppet**: first-person character embodiment — in-character dialogue and interaction.
- **Does NOT**: evaluate, diagnose, or critique text. Does NOT produce structured output.
