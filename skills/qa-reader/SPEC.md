# qa-reader — Spec

## Meta

| Field       | Value                                    |
| ----------- | ---------------------------------------- |
| Skill       | `qa-reader`                              |
| Version     | `v2`                                     |
| Last tested | `—`                                      |
| Depends on  | `none (loads agent-qa-reader persona)`   |

## Scenarios

### S01 — Chapter opening hook evaluation

**Intent:** Verify the skill evaluates hook strength and first-page engagement.

**Context:** User pastes the first 1-2 pages of a chapter opening.

**Input:**

```
/qa-reader
[paste chapter opening — first 1-2 pages]
```

**Expected behavior:**

- [ ] Loads agent-qa-reader persona before analysis
- [ ] Evaluates hook strength (does the opening create a reason to keep reading)
- [ ] Assesses first-page engagement (tension, curiosity, stakes)
- [ ] Identifies what the opening promises the reader

**Expected output:**

- CONTAINS: hook strength verdict
- CONTAINS: identified reader promise
- STRUCTURE: engagement-focused assessment, not prose craft analysis

**Anti-patterns (must NOT happen):**

- [ ] Evaluates prose craft instead of reading experience
- [ ] Gives generic "strong opening" without explaining why
- [ ] Suggests rewriting instead of diagnosing engagement

---

### S02 — Full chapter pacing and tension

**Intent:** Verify the skill maps tension curves and identifies pacing sags.

**Context:** User pastes a full chapter of 8-15 pages.

**Input:**

```
/qa-reader
[paste full chapter — 8-15 pages]
```

**Expected behavior:**

- [ ] Maps the tension curve across the chapter (rising, falling, plateaus)
- [ ] Identifies specific pacing sags (where the reader's attention would drift)
- [ ] Diagnoses why sags occur (over-description, redundant beats, missing stakes)
- [ ] Notes effective tension peaks and what makes them work

**Expected output:**

- STRUCTURE: tension curve mapped across the chapter
- CONTAINS: specific pacing sags with locations and causes
- CONTAINS: effective tension peaks identified

**Anti-patterns (must NOT happen):**

- [ ] Only evaluates the beginning and end, skipping the middle
- [ ] Confuses slow pacing with bad pacing (deliberate deceleration is valid)

---

### S03 — Bookends mode on opening and closing chapters

**Intent:** Verify the --bookends flag evaluates symmetry between opening and closing.

**Context:** User pastes both the opening and closing chapters with the `--bookends` flag.

**Input:**

```
/qa-reader --bookends
[paste opening chapter + closing chapter]
```

**Expected behavior:**

- [ ] Evaluates bookend symmetry (thematic echoes, mirrored images, callbacks)
- [ ] Assesses thematic closure (does the ending deliver on the opening's promise)
- [ ] Checks emotional arc from first chapter to last
- [ ] Notes missed symmetry opportunities

**Expected output:**

- CONTAINS: identified thematic echoes or symmetry elements
- CONTAINS: thematic closure assessment
- CONTAINS: missed symmetry opportunities if any

**Anti-patterns (must NOT happen):**

- [ ] Analyzes each chapter independently without comparing them
- [ ] Demands exact mirroring instead of thematic resonance

---

## Edge Cases

### E01 — Non-narrative text (essay, article)

**Intent:** Verify the skill adapts engagement criteria to non-fiction.

**Input:**

```
/qa-reader
[paste non-fiction essay or article excerpt]
```

**Expected behavior:**

- [ ] Recognizes the text as non-narrative
- [ ] Adapts engagement criteria to non-fiction (argument hooks, intellectual tension, pacing of ideas)
- [ ] Does not force fiction metrics (character tension, plot hooks) onto the text
- [ ] Still evaluates readability and reader engagement within the form

**Expected output:**

- CONTAINS: recognition of non-narrative form
- CONTAINS: engagement assessment adapted to non-fiction criteria

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
