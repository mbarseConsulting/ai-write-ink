# calibrate-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `calibrate-ink`                            |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none (reads genre-conventions.md reference)` |

## Scenarios

### S01 — Dark fantasy project calibration

**Intent:** Validates that calibrate-ink reads genre conventions, identifies the genre, and establishes session parameters.

**Context:** Fresh session start. User specifies genre explicitly.

**Input:**

```
/calibrate-ink
Genre: dark fantasy
```

**Expected behavior:**

- [ ] Reads the `genre-conventions.md` reference file
- [ ] Identifies "dark fantasy" as the genre
- [ ] Sets conventions specific to dark fantasy (tone, register, pacing expectations)
- [ ] Calibrates tone and register for the session

**Expected output:**

- CONTAINS: dark fantasy-specific conventions (tone, register, pacing)
- STRUCTURE: output is concise parameters, not prose
- CONTAINS: calibrated session settings

**Anti-patterns (must NOT happen):**

- [ ] Dumps the entire genre-conventions.md file
- [ ] Produces a creative writing sample instead of calibration
- [ ] Sets generic conventions that could apply to any genre

---

### S02 — Mid-conversation recalibration after context loss

**Intent:** Validates that calibrate-ink can recalibrate from project state when context has drifted.

**Context:** Conversation has been running for 20+ turns on a noir thriller project. User senses the tone has drifted.

**Input:**

```
/calibrate-ink
```

**Expected behavior:**

- [ ] Re-reads genre conventions
- [ ] Recalibrates from available project context (previous turns, stated genre)
- [ ] Resets tone/register to match the original calibration
- [ ] Does not ask for genre again if it was already established

**Expected output:**

- CONTAINS: recalibrated parameters matching the original genre
- STRUCTURE: output references the established genre without re-asking

**Anti-patterns (must NOT happen):**

- [ ] Ignores prior context and starts from scratch
- [ ] Continues with the drifted tone

---

### S03 — Switching between two projects

**Intent:** Validates that calibrate-ink fully resets and recalibrates when switching projects.

**Context:** Previous calibration was for a romance novel. User explicitly switches to a different genre.

**Input:**

```
/calibrate-ink
Switching to the sci-fi project. Genre: hard science fiction.
```

**Expected behavior:**

- [ ] Fully resets previous calibration (romance conventions cleared)
- [ ] Establishes new parameters for hard science fiction
- [ ] No bleed from the previous genre's conventions

**Expected output:**

- CONTAINS: hard science fiction-specific conventions
- STRUCTURE: no trace of romance conventions in output

**Anti-patterns (must NOT happen):**

- [ ] Carries over tone/register from the previous genre
- [ ] Blends conventions from both genres

---

## Edge Cases

### E01 — No genre specified

**Intent:** Validates that calibrate-ink asks for genre before calibrating rather than assuming.

**Context:** No genre has been mentioned in the conversation.

**Input:**

```
/calibrate-ink
```

**Expected behavior:**

- [ ] Asks the user to specify a genre before calibrating
- [ ] Does not guess or assume a default genre
- [ ] Does not produce calibration output until genre is confirmed

**Expected output:**

- CONTAINS: question asking the user to specify a genre

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
