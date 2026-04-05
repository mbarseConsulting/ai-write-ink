# forge-ink — Spec

## Meta

| Field       | Value                                                              |
| ----------- | ------------------------------------------------------------------ |
| Skill       | `forge-ink`                                                        |
| Version     | `v2`                                                               |
| Last tested | `—`                                                                |
| Depends on  | `agent-judge-arena`, `agent-straight-arena`, `agent-spark-arena`   |

## Scenarios

### S01 — Scene prompt produces two competing versions with QA verdict

**Intent:** Verify the full forge pipeline: two independent prose versions, QA evaluation, winner selection.

**Context:** No special setup. User provides a scene prompt for competitive crafting.

**Input:**

```
/forge-ink
A woman comes home and discovers that all her furniture has been replaced by identical replicas. Nothing is missing. Everything is new.
```

**Expected behavior:**

- [ ] Displays `[FORGE]` tag
- [ ] Spawns two independent prose versions (Agent A and Agent B)
- [ ] The two versions are written independently (no cross-contamination)
- [ ] QA evaluates both versions on defined criteria
- [ ] Selects a winner with explicit rationale

**Expected output:**

- COUNT: exactly 2 independent prose versions
- CONTAINS: QA evaluation with defined criteria
- CONTAINS: winner selection with explicit rationale
- STRUCTURE: winning version is presented clearly and separately

**Anti-patterns (must NOT happen):**

- [ ] Produces only one version and skips the competition
- [ ] Agents see each other's output before completion
- [ ] QA evaluation is vague or lacks specific criteria
- [ ] Merges the two versions without author consent

---

### S02 — Forge with specific style constraint

**Intent:** Verify that both competing versions respect an explicit style constraint.

**Context:** User provides a style constraint alongside the scene prompt.

**Input:**

```
/forge-ink
Style: first person, present tense, short sentences.
A man realizes during a dinner party that he has forgotten his own name.
```

**Expected behavior:**

- [ ] Displays `[FORGE]` tag
- [ ] Both versions use first person, present tense, short sentences
- [ ] The constraint is respected as a hard rule, not a suggestion
- [ ] QA evaluates constraint adherence as part of the criteria

**Expected output:**

- COUNT: exactly 2 versions, both in first person present tense
- CONTAINS: QA assessment of constraint adherence
- STRUCTURE: both versions use short sentences throughout

**Anti-patterns (must NOT happen):**

- [ ] One or both versions ignore the style constraint
- [ ] The constraint is acknowledged but not enforced in the prose

---

### S03 — Forge on a rewrite

**Intent:** Verify that forge produces two competing rewrites of the same passage.

**Context:** User provides existing prose with a rewrite direction.

**Input:**

```
/forge-ink
Rewrite this — make it hit harder:

He left the room. She watched him go. The door closed. She sat down.
```

**Expected behavior:**

- [ ] Both versions rewrite the same source passage
- [ ] Both attempt to "hit harder" per the direction
- [ ] Source passage is preserved as reference for QA comparison
- [ ] QA evaluates which rewrite better fulfills the direction

**Expected output:**

- COUNT: exactly 2 competing rewrites
- CONTAINS: source passage preserved as reference
- CONTAINS: QA verdict on which version hits harder

**Anti-patterns (must NOT happen):**

- [ ] Only one version is produced
- [ ] The source passage is lost or not referenced in evaluation
- [ ] Agents write unrelated scenes instead of rewriting the passage

---

## Edge Cases

### E01 — Very short prompt (single sentence)

**Intent:** Verify that forge runs the full pipeline even on minimal input.

**Input:**

```
/forge-ink
She opened the box.
```

**Expected behavior:**

- [ ] Runs the full forge pipeline (two versions, QA, verdict)
- [ ] Does not shortcut or skip steps due to prompt brevity
- [ ] Both versions expand the single sentence into a scene or moment

**Expected output:**

- COUNT: exactly 2 versions produced
- CONTAINS: QA verdict

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
