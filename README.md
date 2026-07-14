# 🖋️ AI Write Ink

_AI artifacts for writing and editing literary fiction — from structure to final polish._

## Description

A full creative writing pipeline: calibrate your genre, architect your story, outline from saga to scene, write prose, stage dialogue, forge competitive drafts, run QA diagnostics, and edit to publication-ready. 19 specialized skills that cover every stage of the fiction craft.

## Overview

| Skill            | Role                                                                                                                    |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `load`           | Session loader — spawns a resident team (writer + qa) once at session start, then feeds it incrementally to avoid reload churn |
| `calibrate-ink`  | Genre calibrator — sets genre conventions for the session: tone, style expectations, failure modes                      |
| `arch-ink`       | Story architect — structural editor upstream: acts, arcs, throughlines, promise/delivery, want/need                     |
| `outline-ink`    | Story outliner — builds narrative structure macro to micro: saga → arc → chapter → scene script                         |
| `cowrite-ink`    | Literary & creative director — brainstorms ideas, steers direction, critiques on demand, hands off for prose            |
| `brief-ink`      | Scene dramaturg — extracts intentions from prompts, classifies by treatment (GOLD/SHOW/SCENE/ATMOSPHERE/SUBTEXT)       |
| `spark-ink`      | Creative detonator — generates unexpected narrative angles via kill protocol and disruption vectors                     |
| `dialog-ink`     | Stage director — blocks dialogue scenes with physical movement, staging, entrances/exits, semi-theatrical script output |
| `write-ink`      | Fiction writer — narrative prose: scenes, chapters, continuations, surgical rewrites                                    |
| `mod-ink`        | Prose modifier — applies editorial direction with voice lock, propagation, and seam checking                           |
| `forge-ink`      | Competitive prose forge — cadrage → dual-agent craft → QA evaluation loop → verdict                                    |
| `pulse-ink`      | Quick triage — flags stock patterns, engagement drops, and craft failures in one spammable pass                        |
| `qa-prose`       | Line editor — hunts craft weaknesses at sentence level: POV, show-tell, dialogue, description, exposition              |
| `qa-reader`      | Reading experience critic — diagnoses hooks, pacing, tension, engagement                                               |
| `qa-characters`  | Character psychologist — evaluates human truth: psychology, relational dynamics, credibility                            |
| `qa-consistency` | Continuity editor — verifies factual coherence: objects, timeline, lore, arcs, OOC behavior                            |
| `qa-originality` | Editorial scout — evaluates creative singularity and, in editorial register, market positioning                        |
| `edit-ai-fr`     | French prose cleaner — removes AI patterns, fixes language errors, repairs mechanical repetition and dialogue format    |
| `edit-final`     | Copyeditor — last pass: typos, typography, mechanical consistency, AI safety net                                       |

**19 skills** — 1 session loader, 1 calibrator, 1 upstream (structure), 1 outliner, 1 director, 1 dramaturg, 1 creative detonator, 1 stage director, 1 writer, 1 modifier, 1 forge, 1 triage, 5 QA diagnostics, 2 editors

## Session start

A writing session starts with `/load-ink`, which spawns the **resident team** — `writer` (prose) and `qa` (quality judge) — as two named, persistent subagents. The whole session then feeds this team incrementally instead of respawning subagents per scene, so residents accumulate calibration, canon, and prior work rather than being re-briefed every time. A third agent, `polish` (finishing editor — edit-ai-fr, edit-final), is dispatched on demand only, never at load.

## Usage

### `/load-ink`

Spawn the resident team once at session start, then feed it for the whole session.

- **`--writer`** — spawn the `writer` resident only
- **`--qa`** — spawn the `qa` resident only
- **`--recycle`** — re-spawn a resident with a digest of its acquired context
- **default** — spawn both residents (writer + qa), hub routes work to them

---

### `/calibrate-ink`

Set genre conventions for the session. Call at session start or after context loss.

→ Output: `[GENRE: {name}]` + key conventions + failure mode.

---

### `/cowrite-ink`

Discuss fiction — critique, direction, alternatives, beats. Brainstorm or unblock.

- **`-w` / `--write`** — handoff to prose: outputs context for ink, then stops
- **default** — creative interlocutor, adapts to what you bring

---

### `/outline-ink`

Build story structure from macro to micro.

- **`--universe-sagas`** / **`--saga`** / **`--arc`** / **`--chapter`** / **`--script`** — loads matching template, builds section by section
- **`-i` / `--inline`** — write output inline instead of file
- **default** — structural interrogation: what level, what exists, what needs building

---

### `/arch-ink`

Challenge story structure before writing. Diagnose acts, arcs, throughlines.

- **`-r` / `--report`** — full structural diagnostic with rules loaded
- **`-i` / `--inline`** — write output inline instead of file
- **default** — interrogation: one question at a time on the weakest structural element

---

### `/brief-ink`

Extract scene intentions from a prompt. Produce a structured brief classified by treatment.

- **`--gold-dial`** — keep dialogue lines as GOLD (verbatim)
- **`--no-gold`** — skip Phase 0, full reconstruction
- **`-s` / `--show`** — display analysis, wait for go-ahead before delivering
- **`-b` / `--blacklist`** — brief must use zero content words from the prompt
- **`-f` / `--force-only`** — header + classified intentions only (fast mode)
- **`-d` / `--debug`** — coverage matrix after the brief

---

### `/spark-ink`

Generate unexpected narrative angles. Kill protocol + disruption vectors.

- **`--kill`** — aggressive filtration, 3 layers deep
- **`--raw`** — skip kill protocol, pure divergence
- **`--vector <name>`** — force a specific vector (`collision`, `hijack`, `sabotage`, `defamiliarization`, `prism`, `absence`)
- **default** — full pipeline: terrain → kill protocol → mixed vectors → chimera

---

### `/write-ink`

Write narrative prose — scenes, chapters, continuations, surgical rewrites.

- **`-c` / `--check`** — strict context verification before writing
- **`-v` / `--verbatim`** — treat prompt as draft, not intent: skip triage and anti-parroting
- **`-i` / `--inline`** — write prose inline instead of file
- **default** — writes in the fiction's register, output to file

---

### `/dialog-ink`

Stage dialogue scenes with physical movement and spoken language.

- **`-p` / `--pass`** — annotated diagnostic of existing prose
- **`--check`** — context verification, combines with any mode
- **`-i` / `--inline`** — write output inline instead of file
- **default** — scene mode, semi-theatrical script output to file

---

### `/mod-ink`

Apply modifications to existing prose with voice lock and propagation.

- **`--inline`** — line-level edits allowed
- **`--dry`** — show change plan only, don't execute
- **`--verbose`** — append per-passage diff contract after output

---

### `/forge-ink`

Competitive prose production: cadrage → agent craft → QA evaluation loop → verdict.

- **`--dry`** — cadrage only, no craft
- **`--spark`** — enable dual-agent mode with challenger
- **`--scene` / `--chapter` / `--sequence`** — force scope
- **`--no-spark-gen`** — with `--spark`: skip `/spark-ink` generation, user provides brief
- **default** — single agent, full pipeline

---

### `/pulse-ink`

Quick triage diagnostic on fiction prose — stock patterns, engagement drops, craft failures.

- **default** — scan in thirds, severity-sorted one-liners, max 25 lines

---

### `/qa-reader`

Evaluate reading experience — hooks, pacing, tension, engagement.

- **`-r` / `--report`** — full report with rules loaded
- **`-b` / `--bookends`** — focused on opening/closing analysis
- **`-i` / `--inline`** — write output inline instead of file
- **default** — emoji-block diagnostic (gut → editor → critic)

---

### `/qa-prose`

Evaluate sentence-level craft — POV, show-tell, dialogue, description.

- **`-r` / `--report`** — full report with rules loaded
- **`-i` / `--inline`** — write output inline instead of file
- **default** — emoji-block diagnostic

---

### `/qa-characters`

Evaluate character psychology, arcs, dynamics, credibility.

- **`-r` / `--report`** — full report with rules loaded
- **`-i` / `--inline`** — write output inline instead of file
- **default** — emoji-block diagnostic per character

---

### `/qa-consistency`

Verify continuity — objects, timeline, lore, arcs, OOC behavior.

- **`-r` / `--report`** — full report with rules loaded
- **`-i` / `--inline`** — write output inline instead of file
- **default** — dual-cite findings (establishment + violation)

---

### `/qa-originality`

Evaluate creative singularity — voice, concept, freshness, clichés.

- **`-r` / `--report`** — full report with rules loaded
- **`-i` / `--inline`** — write output inline instead of file
- **default** — emoji-block diagnostic

---

### `/edit-ai-fr`

Clean French fiction prose of AI patterns, language errors, mechanical repetition.

- **`--interactive`** — one correction at a time, wait for confirmation
- **`-i` / `--inline`** — write output inline instead of file
- **default** — batch mode: list all findings, then apply on command

---

### `/edit-final`

Last pass before publication — typos, grammar, typography, mechanical consistency.

- **`--interactive`** — one correction at a time, wait for confirmation
- **`-i` / `--inline`** — write output inline instead of file
- **default** — batch mode: list all findings, then apply on command
