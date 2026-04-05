# qa-characters — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `qa-characters`                            |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none (loads agent-qa-characters persona)` |

## Scenarios

### S01 — Multi-character psychological credibility

**Intent:** Verify the skill evaluates each character's psychological credibility and flags unearned reactions.

**Context:** User pastes a passage with 3+ characters in emotional conflict.

**Input:**

```
/qa-characters
[paste passage with 3+ characters in emotional conflict]
```

**Expected behavior:**

- [ ] Loads agent-qa-characters persona before analysis
- [ ] Evaluates psychological credibility of each named character
- [ ] Flags unearned emotional reactions (reactions without sufficient setup)
- [ ] Assesses cast dynamics and inter-character tension

**Expected output:**

- COUNT: assessment covers all named characters present
- CONTAINS: specific credibility findings per character
- STRUCTURE: individual character assessments, not a single blended analysis

**Anti-patterns (must NOT happen):**

- [ ] Skips a character present in the scene
- [ ] Provides generic praise without specific textual evidence
- [ ] Rewrites prose instead of diagnosing

---

### S02 — Character arc across chapters

**Intent:** Verify the skill assesses transformation arcs and identifies missing beats.

**Context:** User pastes 2-3 chapter excerpts showing a character's evolution over time.

**Input:**

```
/qa-characters
[paste 2-3 chapter excerpts showing a character's evolution]
```

**Expected behavior:**

- [ ] Maps the character's transformation arc across provided material
- [ ] Identifies missing psychological beats (unmotivated shifts)
- [ ] Distinguishes earned growth from authorial fiat
- [ ] Notes if regression or stasis is intentional vs. accidental

**Expected output:**

- CONTAINS: mapped transformation arc with stage references
- CONTAINS: identification of any missing psychological beats
- STRUCTURE: cross-chapter arc analysis, not per-chapter isolation

**Anti-patterns (must NOT happen):**

- [ ] Treats each chapter in isolation without tracking arc
- [ ] Imposes a preferred arc shape instead of diagnosing the existing one

---

### S03 — Omniscient leak detection

**Intent:** Verify the skill detects when a character reacts to information they shouldn't have.

**Context:** User pastes a scene with a deliberate knowledge boundary violation between characters.

**Input:**

```
/qa-characters
[paste scene where Character A responds to something only Character B witnessed privately]
```

**Expected behavior:**

- [ ] Detects the knowledge boundary violation
- [ ] Identifies which character knows too much and what they shouldn't know
- [ ] Traces where the information was established and how it leaked

**Expected output:**

- CONTAINS: identification of the character with unauthorized knowledge
- CONTAINS: trace of where the information was established
- STRUCTURE: clear chain from information source to violation point

**Anti-patterns (must NOT happen):**

- [ ] Misses the omniscient leak
- [ ] Flags legitimate knowledge as a leak (false positive on properly established info)

---

## Edge Cases

### E01 — Single unnamed character

**Intent:** Verify the skill handles minimal character material gracefully.

**Input:**

```
/qa-characters
[paste short passage with one unnamed character, no dialogue]
```

**Expected behavior:**

- [ ] Runs analysis on the single character present
- [ ] Flags limited material for arc assessment
- [ ] Still evaluates internal psychological coherence
- [ ] Does not fabricate dynamics that aren't in the text

**Expected output:**

- CONTAINS: psychological coherence assessment of the single character
- CONTAINS: note about limited material for arc assessment

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
