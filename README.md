# 🖋️ AI Write Ink

_AI artifacts for writing and editing literary fiction — from structure to final polish._

## Description

A full creative writing pipeline: calibrate your genre, architect your story, outline from saga to scene, write prose, stage dialogue, embody characters, run QA diagnostics, and edit to publication-ready. 14 specialized skills that cover every stage of the fiction craft.

## Overview

| Skill            | Role                                                                                                                           |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `arch-ink`       | Story architect — structural editor upstream: acts, arcs, throughlines, promise/delivery, want/need                           |
| `outline-ink`    | Story outliner — builds narrative structure macro to micro: saga → arc → chapter → scene script                               |
| `cowrite-ink`    | Literary & creative director — brainstorms ideas, steers direction, critiques on demand, hands off for prose                   |
| `dialog-ink`     | Stage director — blocks dialogue scenes with physical movement, staging, entrances/exits, semi-theatrical script output        |
| `puppet-ink`     | Fiction performer — 2 modes: roleplay (collaborative fiction with NPCs/world), puppet (character embodiment in first person)   |
| `write-ink`      | Fiction writer — narrative prose: scenes, chapters, continuations, surgical rewrites                                           |
| `qa-prose`       | Line editor — hunts craft weaknesses at sentence level: POV, show-tell, dialogue, description, exposition                      |
| `qa-reader`      | Reading experience critic — diagnoses hooks, pacing, tension, engagement                                                       |
| `qa-characters`  | Character psychologist — evaluates human truth: psychology, relational dynamics, credibility                                   |
| `qa-consistency` | Continuity editor — verifies factual coherence: objects, timeline, lore, arcs, OOC behavior                                    |
| `qa-originality` | Editorial scout — evaluates creative singularity and, in editorial register, market positioning                                |
| `edit-ai-fr`     | French prose cleaner — removes AI patterns, fixes language errors, repairs mechanical repetition and dialogue format           |
| `edit-final`     | Copyeditor — last pass: typos, typography, mechanical consistency, AI safety net                                               |
| `calibrate-ink`  | Genre calibrator — sets genre conventions for the session: tone, style expectations, failure modes                             |

**14 skills** — 1 calibrator, 1 upstream (structure), 1 outliner, 1 director, 1 stage director, 1 writer, 1 performer (2 modes), 4 QA diagnostics, 2 editors

## Usage

### `/calibrate-ink`

Set genre conventions for the session. Call at session start or after context loss.

→ Output: `[GENRE: {name}]` + key conventions + failure mode.

---

### `/cowrite-ink`

Discuss fiction — critique, direction, alternatives, beats. Brainstorm or unblock.

- **default** — creative interlocutor, adapts to what you bring
- **`--write`** (or "écris", "go", "lance ink") — handoff to prose: outputs context for ink, then stops

---

### `/outline-ink`

Build story structure from macro to micro.

- **default** — structural interrogation: what level, what exists, what needs building
- **`--universe-sagas`** / **`--saga`** / **`--arc`** / **`--chapter`** / **`--script`** — loads matching template, builds section by section

---

### `/arch-ink`

Challenge story structure before writing. Diagnose acts, arcs, throughlines.

- **default** — interrogation: one question at a time on the weakest structural element
- **`--report`** — full structural diagnostic with rules loaded

→ Output: Diagnostic | Script Diagnostic | Assessment | Inline.

---

### `/write-ink`

Write narrative prose — scenes, chapters, continuations, surgical rewrites.

- **default** — writes in the fiction's register
- **`--check`** — strict context verification before writing

→ Output: prose to file (user-specified path or asks).

---

### `/dialog-ink`

Stage dialogue scenes with physical movement and spoken language.

- **`scene`** (default) — semi-theatrical script output
- **`pass`** — annotated diagnostic of existing prose
- **`--check`** — context verification, combines with any mode

→ Output: script to file or diagnostic.

---

### `/puppet-ink`

Collaborative fiction with characters.

- **`roleplay`** (default) — NPC performance, world simulation
- **`puppet`** — character embodiment in first person ("parle-moi en tant que...")

---

### `/qa-reader`

Evaluate reading experience — hooks, pacing, tension, engagement.

- **default** — emoji-block diagnostic (gut → editor → critic)
- **`--report`** — full report with rules loaded
- **bookends** — focused on opening/closing (implicit when asking about bookends)

→ Output: Diagnostic | Assessment | Inline.

---

### `/qa-prose`

Evaluate sentence-level craft — POV, show-tell, dialogue, description.

- **default** — emoji-block diagnostic
- **`--report`** — full report with rules loaded

→ Output: Diagnostic | Assessment | Inline.

---

### `/qa-characters`

Evaluate character psychology, arcs, dynamics, credibility.

- **default** — emoji-block diagnostic per character
- **`--report`** — full report with rules loaded

→ Output: Diagnostic | Assessment | Inline.

---

### `/qa-consistency`

Verify continuity — objects, timeline, lore, arcs, OOC behavior.

- **default** — dual-cite findings (establishment + violation)
- **`--report`** — full report with rules loaded

→ Output: Diagnostic | Assessment | Inline.

---

### `/qa-originality`

Evaluate creative singularity — voice, concept, freshness, clichés.

- **default** — emoji-block diagnostic
- **`--report`** — full report with rules loaded

→ Output: Diagnostic | Assessment | Inline.

---

### `/edit-ai-fr`

Clean French fiction prose of AI patterns, language errors, mechanical repetition.

- **default** — batch or interactive corrections

---

### `/edit-final`

Last pass before publication — typos, grammar, typography, mechanical consistency.

- **default** — batch or interactive corrections
