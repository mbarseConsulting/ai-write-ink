# qa-prose — Spec

## Meta

| Field       | Value                                  |
| ----------- | -------------------------------------- |
| Skill       | `qa-prose`                             |
| Version     | `v2`                                   |
| Last tested | `—`                                    |
| Depends on  | `none (loads agent-qa-prose persona)`  |

## Scenarios

### S01 — Show vs. tell diagnosis

**Intent:** Verify the skill identifies telling and suggests showing alternatives.

**Context:** User pastes a passage with a mix of showing and telling.

**Input:**

```
/qa-prose
[paste passage with mixed show/tell — e.g., "She was angry" next to sensory descriptions]
```

**Expected behavior:**

- [ ] Loads agent-qa-prose persona before analysis
- [ ] Identifies specific instances of telling (names the lines)
- [ ] Suggests showing alternatives without rewriting the whole passage
- [ ] Recognizes effective telling (intentional summary) and doesn't flag it

**Expected output:**

- CONTAINS: specific telling instances with line references
- CONTAINS: showing alternatives for flagged instances
- STRUCTURE: distinguishes intentional telling from problematic telling

**Anti-patterns (must NOT happen):**

- [ ] Flags all telling indiscriminately (some telling is craft)
- [ ] Rewrites the passage instead of diagnosing
- [ ] Provides generic show-don't-tell advice without line-level specificity

---

### S02 — Dialogue technique evaluation

**Intent:** Verify the skill evaluates attribution, subtext, and distinct voices in dialogue.

**Context:** User pastes a dialogue-heavy scene with 2-3 characters.

**Input:**

```
/qa-prose
[paste dialogue-heavy scene with 2-3 characters talking]
```

**Expected behavior:**

- [ ] Evaluates dialogue attribution (over-tagging, said-bookisms, missing tags)
- [ ] Assesses subtext quality (characters saying what they mean vs. layered dialogue)
- [ ] Checks whether each character has a distinct voice
- [ ] Notes dialogue rhythm and pacing

**Expected output:**

- CONTAINS: attribution assessment
- CONTAINS: subtext quality evaluation
- CONTAINS: voice distinction analysis per character

**Anti-patterns (must NOT happen):**

- [ ] Ignores dialogue entirely and only analyzes narration
- [ ] Imposes a single dialogue style preference

---

### S03 — POV consistency analysis

**Intent:** Verify the skill flags POV breaks, head-hopping, and distance inconsistencies.

**Context:** User pastes a chapter written in close third person with subtle POV violations.

**Input:**

```
/qa-prose
[paste chapter written in close third person with subtle POV violations]
```

**Expected behavior:**

- [ ] Identifies the established POV mode (close third, omniscient, first, etc.)
- [ ] Flags POV breaks and head-hopping with specific line references
- [ ] Notes narrative distance inconsistencies (suddenly zooming out or in)
- [ ] Distinguishes between intentional POV shifts and errors

**Expected output:**

- CONTAINS: identified POV mode
- CONTAINS: POV breaks with specific line references
- STRUCTURE: distinguishes intentional shifts from errors

**Anti-patterns (must NOT happen):**

- [ ] Misidentifies the POV mode
- [ ] Flags legitimate omniscient narration as head-hopping

---

## Edge Cases

### E01 — Poetry or experimental prose

**Intent:** Verify the skill adapts its criteria to non-standard forms.

**Input:**

```
/qa-prose
[paste prose poem or experimental text with fragmented syntax]
```

**Expected behavior:**

- [ ] Recognizes the form as poetry/experimental
- [ ] Adapts evaluation criteria to the form (doesn't apply novel conventions)
- [ ] Evaluates craft within the form's own logic
- [ ] Does not penalize intentional rule-breaking

**Expected output:**

- CONTAINS: recognition of the experimental/poetic form
- CONTAINS: evaluation adapted to the form's own criteria

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
