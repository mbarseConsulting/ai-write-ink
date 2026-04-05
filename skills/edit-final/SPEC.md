# edit-final — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `edit-final`                               |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none (loads agent-edit-final persona)`    |

## Scenarios

### S01 — Chapter draft proofreading

**Intent:** Verify the skill catches typos, grammar errors, and punctuation issues.

**Context:** User pastes a chapter draft with deliberate errors for proofreading.

**Input:**

```
/edit-final
[paste chapter draft with deliberate typos, missing commas, and punctuation errors]
```

**Expected behavior:**

- [ ] Loads agent-edit-final persona before analysis
- [ ] Catches typos (misspellings, doubled words, missing words)
- [ ] Flags grammar errors with corrections
- [ ] Identifies punctuation issues (missing periods, incorrect comma usage)

**Expected output:**

- CONTAINS: each finding with location and correction
- STRUCTURE: findings are itemized with location references
- COUNT: at least 1 finding per error category (typo, grammar, punctuation)

**Anti-patterns (must NOT happen):**

- [ ] Rewrites sentences for style (this is proofreading, not line editing)
- [ ] Misses obvious typos while flagging stylistic preferences
- [ ] Changes the author's intentional style choices

---

### S02 — Multi-chapter typographic consistency

**Intent:** Verify the skill checks consistency across chapters.

**Context:** User pastes excerpts from multiple chapters with inconsistent typographic conventions.

**Input:**

```
/edit-final
[paste excerpts from 2-3 chapters with inconsistent dash styles, quote styles, and spacing conventions]
```

**Expected behavior:**

- [ ] Detects typographic inconsistencies across chapters (em-dash vs. en-dash, curly vs. straight quotes)
- [ ] Reports which convention is used where and recommends standardization
- [ ] Checks spacing conventions (double space after period, space before punctuation)
- [ ] Flags inconsistent formatting of recurring elements (numbers, dates, names)

**Expected output:**

- CONTAINS: identified inconsistencies with chapter/location references
- CONTAINS: standardization recommendation for each inconsistency
- STRUCTURE: cross-chapter comparison, not per-chapter isolation

**Anti-patterns (must NOT happen):**

- [ ] Only checks within each chapter without cross-chapter comparison
- [ ] Imposes a typographic standard without noting the author's predominant usage

---

### S03 — Clean text confirmation

**Intent:** Verify the skill handles near-perfect text without introducing noise.

**Context:** User pastes well-proofread text to confirm cleanliness.

**Input:**

```
/edit-final
[paste clean, well-proofread text with minimal or no errors]
```

**Expected behavior:**

- [ ] Confirms minimal errors found
- [ ] Does not introduce unnecessary changes
- [ ] May note 1-2 very minor observations without requiring action
- [ ] Does not inflate findings to appear thorough

**Expected output:**

- CONTAINS: confirmation of minimal or no errors
- STRUCTURE: output is brief, not padded

**Anti-patterns (must NOT happen):**

- [ ] Invents errors in clean text
- [ ] Suggests stylistic rewrites disguised as proofreading
- [ ] Reports "no errors" without actually scanning the text

---

## Edge Cases

### E01 — Text in mixed languages

**Intent:** Verify the skill applies appropriate conventions per language section.

**Input:**

```
/edit-final
[paste text mixing French and English sections — e.g., French narration with English dialogue or vice versa]
```

**Expected behavior:**

- [ ] Identifies the language of each section
- [ ] Applies French typographic conventions to French sections (espaces insecables, guillemets)
- [ ] Applies English typographic conventions to English sections
- [ ] Flags inconsistencies within each language section separately

**Expected output:**

- CONTAINS: language identification for each section
- CONTAINS: language-appropriate convention checks

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
