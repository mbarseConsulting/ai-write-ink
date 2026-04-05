# arch-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `arch-ink`                                 |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Chapter plan evaluation

**Intent:** Verify that arch-ink evaluates act structure, flags weak midpoints, and identifies missing throughlines.

**Context:** No special setup. User provides a three-act chapter plan inline.

**Input:**

```
/arch-ink
My novel in 3 acts: a cop obsessed with an unsolved case. Act 1: the case resurfaces. Act 2: he discovers the culprit is his mentor. Act 3: confrontation.
```

**Expected behavior:**

- [ ] Loads agent persona from `agents/agent-arch-ink.md`
- [ ] Evaluates the three-act structure as presented
- [ ] Flags the midpoint (or its absence) — Act 2 has a reveal but where is the midpoint shift?
- [ ] Identifies throughlines (obsession, mentor relationship, justice vs. loyalty)
- [ ] Points out structural gaps (e.g., what drives Act 2 between the reveal and Act 3?)
- [ ] Validates the plan before any writing happens

**Expected output:**

- CONTAINS: mention of midpoint weakness or absence
- CONTAINS: at least one identified throughline
- STRUCTURE: output is a structural diagnosis, not prose or outline

**Anti-patterns (must NOT happen):**

- [ ] Writes prose based on the plan
- [ ] Accepts the structure without critique
- [ ] Gives generic structural advice unrelated to the specific material

---

### S02 — Full outline structural diagnosis

**Intent:** Verify diagnosis of act breaks, pacing issues, and structural gaps on a full outline.

**Context:** User provides a complete 8-chapter outline for analysis.

**Input:**

```
/arch-ink
8-chapter outline:
Ch1: Setup, protagonist introduced. Ch2: Inciting incident — she finds the letter. Ch3: Investigation begins. Ch4: False lead. Ch5: Real clue discovered. Ch6: Confrontation with antagonist. Ch7: Twist — the antagonist is her mother. Ch8: Resolution.
```

**Expected behavior:**

- [ ] Identifies act break positions (where does Act 1 end? Act 2?)
- [ ] Diagnoses pacing (Ch3-Ch5 may sag — three investigation chapters in sequence)
- [ ] Flags the twist placement (Ch7 of 8 — is it too late? too predictable by then?)
- [ ] Checks for structural gaps (no B-plot visible, no midpoint reversal)
- [ ] Presents findings as a structural diagnosis, not a rewrite

**Expected output:**

- CONTAINS: act break positions
- CONTAINS: pacing diagnosis for the Ch3-Ch5 sequence
- CONTAINS: twist placement assessment
- STRUCTURE: findings are presented as diagnosis, not a rewritten outline

**Anti-patterns (must NOT happen):**

- [ ] Rewrites the outline
- [ ] Produces prose
- [ ] Focuses only on story content, ignoring structure

---

### S03 — Character arc evaluation

**Intent:** Verify evaluation of arc structure and transformation credibility when arc material is provided.

**Context:** User provides a character arc description with start state, end state, and turn point.

**Input:**

```
/arch-ink
Character arc for the protagonist: starts as a cynical journalist who trusts no one. By the end, she risks her career to protect a source she barely knows. The turn happens in chapter 5 when she sees the source's child.
```

**Expected behavior:**

- [ ] Evaluates the arc structure (cynical -> self-sacrificing)
- [ ] Assesses transformation credibility (is the child scene enough to drive this shift?)
- [ ] Checks if the arc has sufficient stages (not just start-state and end-state)
- [ ] Flags missing intermediate beats (what happens between cynicism and sacrifice?)

**Expected output:**

- CONTAINS: credibility assessment of the turning point
- CONTAINS: identification of missing intermediate beats
- STRUCTURE: output evaluates arc stages, not just endpoints

**Anti-patterns (must NOT happen):**

- [ ] Writes the character's scenes
- [ ] Accepts the arc without evaluating credibility
- [ ] Gives generic arc advice ("every character needs a wound")

---

## Edge Cases

### E01 — Material too short for structural analysis

**Intent:** Verify that arch-ink flags when the scope is insufficient for meaningful structure work.

**Input:**

```
/arch-ink
A woman opens a door and sees her ex.
```

**Expected behavior:**

- [ ] Flags that a single scene/moment is below the threshold for structural analysis
- [ ] Suggests what level of material arch-ink needs (chapter plan, outline, arc description)
- [ ] Does not force a structural framework onto a single beat

**Expected output:**

- CONTAINS: indication that material is insufficient for structural analysis
- CONTAINS: suggestion of what level of material is needed

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
