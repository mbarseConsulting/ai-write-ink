# qa-originality — Spec

## Meta

| Field       | Value                                        |
| ----------- | -------------------------------------------- |
| Skill       | `qa-originality`                             |
| Version     | `v2`                                         |
| Last tested | `—`                                          |
| Depends on  | `none (loads agent-qa-originality persona)`   |

## Scenarios

### S01 — Scene draft originality scan

**Intent:** Verify the skill identifies stock elements and rates originality across dimensions.

**Context:** User pastes a scene draft with a mix of fresh imagery and cliche elements.

**Input:**

```
/qa-originality
[paste scene draft with mix of fresh imagery and cliche elements]
```

**Expected behavior:**

- [ ] Loads agent-qa-originality persona before analysis
- [ ] Identifies specific stock elements (cliche metaphors, default imagery, trope shortcuts)
- [ ] Rates originality across concept, voice, and imagery
- [ ] Cites specific lines or phrases as evidence

**Expected output:**

- CONTAINS: specific stock elements identified with line references
- CONTAINS: originality rating across concept, voice, and imagery
- STRUCTURE: evidence-backed assessment, not vague impressions

**Anti-patterns (must NOT happen):**

- [ ] Gives a vague "this is original" without textual evidence
- [ ] Flags stylistic choices as cliches without justification
- [ ] Rewrites passages instead of diagnosing

---

### S02 — Manuscript-level artistic identity

**Intent:** Verify the skill assesses artistic identity and flags derivative passages across a longer sample.

**Context:** User pastes a full manuscript sample spanning 3-5 pages across different scenes.

**Input:**

```
/qa-originality
[paste full manuscript sample — 3-5 pages across different scenes]
```

**Expected behavior:**

- [ ] Assesses the author's artistic identity (what makes this voice distinctive)
- [ ] Identifies derivative passages and names what they derive from
- [ ] Distinguishes between influence and imitation
- [ ] Evaluates concept freshness at the premise level

**Expected output:**

- CONTAINS: description of the author's distinctive voice elements
- CONTAINS: derivative passages identified with their sources
- STRUCTURE: distinction between influence and imitation

**Anti-patterns (must NOT happen):**

- [ ] Treats each page in isolation without assessing overall identity
- [ ] Confuses genre conventions with lack of originality

---

### S03 — Opening chapter hook originality

**Intent:** Verify the skill evaluates hook originality and detects genre-default openings.

**Context:** User pastes an opening chapter's first 2-3 pages for originality assessment.

**Input:**

```
/qa-originality
[paste opening chapter — first 2-3 pages]
```

**Expected behavior:**

- [ ] Evaluates whether the opening hook is original or genre-default
- [ ] Names the genre-default pattern if detected (e.g., "waking up", "looking in mirror", "weather opening")
- [ ] Assesses whether the first impression establishes a distinctive voice

**Expected output:**

- CONTAINS: hook originality verdict (original or genre-default)
- CONTAINS: named genre-default pattern if applicable
- CONTAINS: assessment of voice distinctiveness

**Anti-patterns (must NOT happen):**

- [ ] Approves a stock opening without flagging it
- [ ] Penalizes a genre opening that subverts expectations

---

## Edge Cases

### E01 — Deliberately genre-conventional piece

**Intent:** Verify the skill distinguishes intentional convention from lazy defaults.

**Input:**

```
/qa-originality
[paste romance or thriller scene that deliberately uses genre conventions with craft]
```

**Expected behavior:**

- [ ] Recognizes the conventions as intentional when executed with skill
- [ ] Distinguishes between "convention deployed well" and "default used lazily"
- [ ] Still identifies areas where originality could enhance without breaking genre
- [ ] Does not penalize genre adherence as inherently unoriginal

**Expected output:**

- CONTAINS: distinction between intentional convention and lazy default
- CONTAINS: areas where originality could enhance the piece

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
