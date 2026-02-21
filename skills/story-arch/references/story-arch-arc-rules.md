# story-arch — Arc Rules

> Loaded by: story-arch in `--report` mode when arc material is provided (character sheet, explicit want/need, arc trajectory)
> Scope: protagonist arc — want/need, lie, ghost, transformation, subplot resonance
> Default output: Diagnostic (supplements structure-rules)

---

## Axes

### want-need-split

**What it looks at:** Distinction between the protagonist's conscious desire (want) and actual psychological need (need). Are both distinct, active, and in tension?

**Failure modes:**
- Want and need are identical — protagonist wants what they need, no internal conflict
- Want is clear, need is absent or never endangered
- Need is stated explicitly in dialogue without ever being shown structurally

**States:**
- `distinct and in tension` — want and need actively oppose each other, structure exploits both
- `present but passive` — distinction exists but doesn't generate narrative internal conflict
- `absent` — only one register (want without need, or immediate need without deeper desire)

**Default sev:** MAJ

---

### lie-and-ghost

**What it looks at:** The foundational wound (ghost) and the false belief it generates (lie). Do both drive the decisions that propel the plot?

**Failure modes:**
- Ghost is biographical information without narrative consequence (mentioned, not exploited)
- Lie is never endangered by story events
- Wound and lie are identical — no distinction between the fact and the belief it generates
- Ghost is revealed too early, reducing arc tension

**States:**
- `driving` — ghost and lie generate identifiable decisions across the acts
- `present` — identifiable but don't influence major structural beats
- `decorative` — mentioned, no effect on plot
- `absent` — no identifiable ghost or lie

**Default sev:** MAJ

---

### arc-completion

**What it looks at:** Whether the transformation is earned through story events or simply declared.

**Failure modes:**
- Character "realizes" something without the story having forced that realization
- Transformation arrives at the climax without being prepared by micro-transformations in preceding acts
- Arc is purely external (protagonist succeeds at their mission) without internal transformation
- Transformation is reversed but not credible (fall arc without accumulation of failures)

**States:**
- `earned` — transformation flows from events, micro-progressions visible across acts
- `declared` — character changes but the structure hasn't forced the change
- `partial` — external transformation without corresponding internal transformation
- `absent` — character ends where they began, without justification for intentional stasis

**Default sev:** MAJ

---

### subplot-resonance

**What it looks at:** Whether subplots resonate with the main arc (mirror, complication, counterpoint).

**Failure modes:**
- Subplots are narratively disconnected from the main arc — they neither influence nor reflect anything
- A subplot resolves the same theme as the main arc without adding anything — duplication
- Subplots have their own complete arc without contact point with the protagonist
- Subplot resolutions don't inform the climax of the main arc

**States:**
- `resonant` — each major subplot complicates or illuminates the main arc
- `disconnected` — subplots run in parallel without resonance
- `duplicate` — repeats the main arc without distinct contribution

**Default sev:** SUG (single subplot) / MAJ (if all subplots)

---

## Loading rules

- Required: arc material provided (character sheet with want/need, outline with arc, or explicit author statement).
- Always supplementing structure-rules, never standalone.
- `lie-and-ghost` and `arc-completion` are the priority axes — correcting subplot-resonance before them is premature.
