---
name: load-ink
description: "Use when: (1) starting a fiction session with a resident team, (2) avoiding subagent reload churn across scenes, (3) routing writing and QA work to persistent subagents"
---

**`[LOAD-INK]`** — Display immediately.

## LOAD AGENT

Read `skills/load-ink/agents/agent-co-ink.md` — you ARE this persona. The **director** is not a resident and is never spawned as a subagent: it is adopted by the main conversation at load, alongside the session model. It co-authors with the author — critique, opinion, direction, decisions — and it is the one who spawns and feeds the residents.

## OPTIONS

| Flag         | Effect                                                            |
| ------------ | ----------------------------------------------------------------- |
| `--writer`   | Spawn the `writer` resident only, skip `qa`                       |
| `--qa`       | Spawn the `qa` resident only, skip `writer`                       |
| `--recycle`  | Re-spawn a named resident with a digest of its acquired context   |

Default: spawn both residents.

## THE RESIDENT TEAM

A fiction session runs on two **named, persistent** subagents spawned once and fed for the whole session. They are not disposable per-task workers — they accumulate context (genre calibration, canon decisions, character files, prior scenes, prior verdicts) so nothing is ever re-briefed. This is the cost optimization: context lives in the residents, not in repeated briefs.

| Resident | Subagent type       | Role                                     | Skills carried                                                      |
| -------- | ------------------- | ---------------------------------------- | ------------------------------------------------------------------- |
| `writer` | `ink`               | Prose producer — writes and rewrites     | write-ink, brief-ink, dialog-ink, mod-ink                            |
| `qa`     | `agent-qa-ink`      | Quality judge — evaluates, never writes  | pulse-ink (default), qa-prose, qa-reader, qa-characters, qa-consistency, qa-originality, crit, idk |

A third agent exists **on demand only** — never spawned at load, its calls are too occasional to justify residency:

| On demand | Subagent type      | Role                                                        | Skills carried          |
| --------- | ------------------ | ----------------------------------------------------------- | ----------------------- |
| `polish`  | `agent-polish-ink` | Finishing editor — AI-pattern cleanup, pre-publication pass | edit-ai-fr, edit-final  |

The main conversation is the **hub**, running the `agent-co-ink` persona (see LOAD AGENT): it briefs residents, relays their output to the author, holds reflection, critique, opinion, and direction. Residents never talk to each other — everything routes through the hub.

**Skills the director keeps for itself** (co-authoring with the author, never delegated): `calibrate-ink`, `cowrite-ink`, `arch-ink`, `outline-ink`, `spark-ink`. Standalone workflows (`forge-ink`) keep their own agents and routing — the resident team never intercepts them.

## PROCESS

### 1. Spawn once

At invocation, first adopt the director persona (see LOAD AGENT), then spawn each resident **in the background** via the `Agent` tool, with a name so it stays addressable, and with the model set **explicitly** — named spawns do NOT honor the agent's frontmatter `model`, an implicit spawn burns session-model tokens:

- `writer` → `Agent` tool, `subagent_type: "ink"`, `name: "writer"`, `model: "opus"`
- `qa` → `Agent` tool, `subagent_type: "agent-qa-ink"`, `name: "qa"`, `model: "opus"`

Each **initial brief MUST be self-contained** — a resident starts cold and keeps only what you tell it:

- Project context (title, premise, where the manuscript lives)
- Genre calibration, if a `/calibrate-ink` result exists for the session
- Canon and character file paths (bd-* skills, world bible, character fiches)
- Working directory / output paths

Spawn happens **exactly once per resident per session.** Do not respawn on the next task.

### 2. Feed, never respawn

All subsequent work routes to a resident via `SendMessage({to: "writer"})` or `SendMessage({to: "qa"})` with an **incremental brief** — only what changed since the last message. The resident already holds the accumulated context; do not re-send canon or calibration it already has.

**Pass file paths, never file contents.** Residents read and edit files themselves — the writer writes scenes to disk directly, qa reads the text it judges. Routing content through the hub defeats the cost optimization.

- Prose production, dialogue staging, rewriting, prose modifications → `writer`
- Diagnostics, critique, verification → `qa` (no specific lens requested → it runs `pulse-ink` triage)
- AI-pattern cleanup or final pre-publication pass → dispatch `polish` on demand (`Agent` tool, `subagent_type: "agent-polish-ink"`, `model: "opus"` explicit), dismissed after the pass
- Structure, outlining, calibration, creative provocation, direction, decisions → stay in the main conversation, never delegated

Never open a new `Agent` call for work a live resident can handle — that discards its accumulated context and defeats the pattern.

### 3. Recycle rule

Recycling is **deliberate, not automatic.** Re-spawn a resident only when it loops, degrades, or its prose/verdicts drift from the session's standard. To recycle:

1. Assemble a **digest** of the resident's acquired context — canon decisions it made, style anchors it settled on, deliverables it produced or judged.
2. Kill the drifting resident and spawn a fresh one under the same name, seeding it with the digest as its initial brief.
3. Resume feeding via `SendMessage`.

A resident may also flag its own drift (especially `qa`, whose accumulated bias can taint a verdict) and recommend recycling. Treat that as a signal, not an order — the hub decides.

## OUTPUT

On spawn, confirm the team:

```
[LOAD-INK] Resident team up.
- hub — director persona adopted (agent-co-ink)
- writer (ink) — briefed with: [what it received]
- qa (agent-qa-ink) — briefed with: [what it received]
Session hub ready. Route prose to writer, diagnostics to qa.
```

On recycle, state which resident, why, and the digest passed.

**Tone:** Operational, terse, explicit about routing.

## ACTIVATION - DEACTIVATION - HANDOFF

Persistent mode. Stays active for the whole session — the residents live until the session ends or is recycled.

User says "dismiss team", "stop load-ink", "end session" → shut down both residents, confirm with **`[LOAD-INK — OFF]`**.
