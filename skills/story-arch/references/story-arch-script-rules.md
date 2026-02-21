# Script Rules — story-arch

> Loaded by: story-arch in `--report` mode when input is a script or chapter plan
> Scope: chapter/scene structure — does the script earn its scenes and serve the arc?
> Evaluates: structural soundness of a chapter plan BEFORE writing
> Preferred output: Diagnostic or Assessment
> Requires: the script. Strengthened by: arc outline, character sheets, previous/next chapter scripts.

---

## Finding Axes

### chapter-function

**What it looks at:** Does the chapter serve a nameable function in the arc? Can you state what the arc loses without this chapter?

**Failure modes:**
- "It's a transition chapter" — transitions are not functions
- "It sets up later events" — setup without standalone value is dead weight
- Chapter function duplicates an adjacent chapter
- Chapter does three things vaguely instead of one thing precisely

**States:**
- `drives-arc` — the arc cannot work without this chapter
- `supports-arc` — the arc would survive, but weaker
- `decorative` — pleasant but removable
- `aimless` — no identifiable function

**Default sev:** BLK

---

### chapter-change

**What it looks at:** What is different at the end of the chapter vs the beginning? Something must change: character position, knowledge, relationships, stakes, power balance.

**Failure modes:**
- Nothing changes — the chapter is a vignette, not a unit of story
- Only external change (event happens) without internal shift
- Change is declared in the script notes but not dramatized in any scene

**States:**
- `irreversible` — something changed that cannot be undone
- `shift` — something moved, but could revert
- `static` — nothing is different at the end

**Default sev:** BLK

---

### scene-function

**What it looks at:** Does each scene have a function within the chapter? Can you name what the chapter loses if the scene is removed?

**Failure modes:**
- Scene exists "for atmosphere" or "to show character" without moving anything
- Scene's function duplicates another scene's function
- Scene does what the previous scene already accomplished
- Function is listed in the script notes but not embedded in the scene's beats

**States:**
- `load-bearing` — chapter breaks without it
- `supporting` — chapter weakens without it
- `dead-weight` — chapter survives without it

**Default sev:** MAJ

---

### scene-sequence

**What it looks at:** Is the scene order the strongest possible? Does each scene earn its position? Would reordering improve tension, revelation timing, or emotional build?

**Failure modes:**
- Scenes could be rearranged without consequence — no causal chain
- Climactic scene is not at the end (anti-climax follows climax)
- Emotional intensity flatlines across consecutive scenes
- A scene depends on information from a later scene

**States:**
- `earned` — each scene's position is justified by what precedes and follows
- `acceptable` — order works but isn't optimal
- `arbitrary` — scenes could be shuffled without consequence

**Default sev:** MAJ

---

### scene-completeness

**What it looks at:** Are all necessary scenes present? Is any step skipped that the reader needs to follow the chapter's logic or emotional arc?

**Failure modes:**
- A logical gap: character goes from state A to state C without B
- An emotional gap: character reacts to something the reader didn't witness
- A missing setup: a scene's impact depends on a beat that was skipped
- Conversely: a scene is present that the reader doesn't need (covered by scene-function)

**States:**
- `complete` — no gap identified
- `gap` — one or more missing steps
- `major-gap` — the chapter's logic breaks without an absent scene

**Default sev:** MAJ

---

### information-sequence

**What it looks at:** Is information revealed in the optimal order across scenes? Each scene should change what the reader knows or believes.

**Failure modes:**
- Reader learns everything in scene 1 — remaining scenes have no revelatory value
- Key information is buried in a low-stakes scene
- A revelation lands before the reader cares about it (no setup)
- Information repeats across scenes without adding new dimension

**States:**
- `well-sequenced` — revelations are timed for maximum impact
- `could-improve` — functional but not optimal
- `problematic` — information order weakens the chapter

**Default sev:** MAJ

---

### entry-exit-states

**What it looks at:** Are the chapter's entry and exit states defined? Is the exit state distinct from the entry state? Does exit create momentum toward the next chapter?

**Failure modes:**
- Entry state is unclear — reader doesn't know where characters stand emotionally/physically
- Exit state mirrors entry state — no progress
- Exit doesn't create forward pull — reader can close the book here
- Entry doesn't follow from the previous chapter's exit (if previous chapter exists)

**States:**
- `propulsive` — clear entry, distinct exit, forward momentum
- `adequate` — defined but not optimized
- `dead-end` — exit creates no reason to continue

**Default sev:** MAJ

---

### script-specificity

**What it looks at:** Is the script concrete enough to write from? Are beats defined, characters positioned, emotional targets clear?

**Failure modes:**
- Vague directions: "they discuss the situation", "tension builds"
- No concrete beats — just scene summaries
- Character emotional states implied but not specified
- Missing anchor: no key line, key gesture, or key image to write toward

**States:**
- `ready-to-write` — a writer could execute this script without guessing
- `needs-precision` — direction is clear but beats are vague
- `too-vague` — more planning needed before writing

**Default sev:** SUG

---

## Verdict Axes

### structural-soundness

**Assesses:** Overall structural health of the script at chapter level.

**States:**
- `solid` — scenes earn their place, sequence is justified, chapter serves the arc
- `weakened` — functional but with identified gaps or dead weight
- `broken` — chapter doesn't serve a clear function, or scenes don't serve the chapter

---

### writing-readiness

**Assesses:** Can a writer execute this script as-is, or does it need more work?

**States:**
- `ready` — specific enough to write, structurally sound, entry/exit defined
- `needs-revision` — structure is sound but beats need precision, or one structural issue to resolve
- `premature` — structural problems must be fixed before writing begins

---

## Loading rules

- Loaded when input is a script, chapter plan, scene breakdown, or beat sheet.
- Can combine with structure-rules if arc outline is provided (to verify chapter → arc coherence).
- Can combine with arc-rules if character arc material is provided.
- Priority: `chapter-function` and `chapter-change` — if both fail, everything else is secondary.
