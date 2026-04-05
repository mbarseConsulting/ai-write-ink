# pulse-ink — Spec

## Meta

| Field       | Value                  |
| ----------- | ---------------------- |
| Skill       | `pulse-ink`            |
| Version     | `v2`                   |
| Last tested | `—`                    |
| Depends on  | `none`                 |

## Scenarios

### S01 — Scene draft triage

**Intent:** Verify the skill scans in thirds, produces severity-sorted findings, and flags stock patterns.

**Context:** User pastes a scene draft of 2-4 pages for quick diagnostic.

**Input:**

```
/pulse-ink
[paste scene draft — 2-4 pages]
```

**Expected behavior:**

- [ ] Scans text in thirds (beginning, middle, end)
- [ ] Produces findings sorted by severity (most critical first)
- [ ] Flags stock patterns and engagement drops with locations
- [ ] Flags strengths alongside problems

**Expected output:**

- STRUCTURE: triage format, not a full analytical report
- CONTAINS: findings sorted by severity
- CONTAINS: at least one strength and one problem identified

**Anti-patterns (must NOT happen):**

- [ ] Produces a long analytical report instead of a triage
- [ ] Ignores one or more thirds
- [ ] Rewrites prose instead of flagging

---

### S02 — Chapter draft top-3 triage

**Intent:** Verify the skill identifies top problems and top strengths in a longer piece.

**Context:** User pastes a longer chapter draft of 8-15 pages.

**Input:**

```
/pulse-ink
[paste chapter draft — 8-15 pages]
```

**Expected behavior:**

- [ ] Identifies top 3 problems, severity-sorted
- [ ] Identifies top 3 strengths
- [ ] Each finding references a specific location in the text

**Expected output:**

- COUNT: approximately 3 problems and 3 strengths
- CONTAINS: specific location references for each finding
- STRUCTURE: output remains concise and actionable (triage, not deep dive)

**Anti-patterns (must NOT happen):**

- [ ] Lists more than ~5 items per category (this is triage, not exhaustive QA)
- [ ] Provides vague findings without textual references

---

### S03 — Multi-scene comparison triage

**Intent:** Verify the skill triages multiple scenes and highlights relative differences.

**Context:** User pastes 2-3 separate scenes for comparative diagnostic.

**Input:**

```
/pulse-ink
[paste 2-3 separate scenes for comparison]
```

**Expected behavior:**

- [ ] Triages each scene independently
- [ ] Highlights relative strengths and weaknesses across scenes
- [ ] Notes which scene has the strongest engagement/originality

**Expected output:**

- STRUCTURE: per-scene triage followed by cross-scene comparison
- CONTAINS: relative ranking or comparison across scenes
- CONTAINS: identification of strongest scene

**Anti-patterns (must NOT happen):**

- [ ] Merges all scenes into one analysis without distinguishing them
- [ ] Only analyzes one scene and ignores the others

---

## Edge Cases

### E01 — Very short passage (< 1 paragraph)

**Intent:** Verify the skill handles minimal material gracefully.

**Input:**

```
/pulse-ink
[paste 2-3 sentences]
```

**Expected behavior:**

- [ ] Still runs the scan
- [ ] Flags that material is too short for full thirds analysis
- [ ] Provides what findings are possible from the available text
- [ ] Does not pad findings to fill a template

**Expected output:**

- CONTAINS: indication that material is too short for full analysis
- CONTAINS: whatever findings are possible from available text

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
