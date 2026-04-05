# qa-consistency — Spec

## Meta

| Field       | Value                                        |
| ----------- | -------------------------------------------- |
| Skill       | `qa-consistency`                             |
| Version     | `v2`                                         |
| Last tested | `—`                                          |
| Depends on  | `none (loads agent-qa-consistency persona)`   |

## Scenarios

### S01 — Physical injury tracking

**Intent:** Verify the skill tracks physical state across scenes and flags healing inconsistencies.

**Context:** User pastes a chapter where a character sustains an injury in one scene and uses the injured limb freely in a later scene.

**Input:**

```
/qa-consistency
[paste chapter where character breaks arm in scene 1, uses both hands freely in scene 3]
```

**Expected behavior:**

- [ ] Loads agent-qa-consistency persona before analysis
- [ ] Tracks the injury from its introduction through subsequent scenes
- [ ] Flags the inconsistency (broken arm used normally without healing)

**Expected output:**

- CONTAINS: scene numbers or locations where the contradiction occurs
- STRUCTURE: timeline of physical state from injury to violation
- CONTAINS: the specific inconsistency (broken arm used freely)

**Anti-patterns (must NOT happen):**

- [ ] Misses the physical state contradiction
- [ ] Invents injuries not present in the text
- [ ] Suggests plot fixes instead of reporting findings

---

### S02 — Multi-chapter timeline

**Intent:** Verify the skill builds a timeline and flags chronological contradictions.

**Context:** User pastes 2-3 chapters with temporal markers that contain contradictions.

**Input:**

```
/qa-consistency
[paste 2-3 chapters with temporal markers — "three days later", "last Monday", specific dates]
```

**Expected behavior:**

- [ ] Builds a chronological timeline from temporal markers
- [ ] Flags contradictions (e.g., "Monday" followed by "two days later" on "Wednesday" = error)
- [ ] Distinguishes vague time from contradictory time

**Expected output:**

- STRUCTURE: reconstructed chronological timeline
- CONTAINS: each contradiction with source references
- CONTAINS: distinction between vague and contradictory time markers

**Anti-patterns (must NOT happen):**

- [ ] Ignores temporal markers and only checks objects
- [ ] Reports vague time references as contradictions

---

### S03 — Worldbuilding lore coherence

**Intent:** Verify the skill checks lore consistency against established rules.

**Context:** User pastes a passage with established magic system rules followed by a scene that violates one.

**Input:**

```
/qa-consistency
[paste passage with established magic system rules, then a scene that violates one]
```

**Expected behavior:**

- [ ] Identifies the established lore rules from the text
- [ ] Detects the violation of those rules
- [ ] References the specific rule and the specific violation
- [ ] Flags abandoned worldbuilding threads if present

**Expected output:**

- CONTAINS: the established rule that was violated
- CONTAINS: the specific violation with location
- STRUCTURE: rule-to-violation mapping

**Anti-patterns (must NOT happen):**

- [ ] Applies external lore not established in the provided text
- [ ] Misses the lore violation while reporting minor surface issues

---

## Edge Cases

### E01 — Standalone scene with no prior context

**Intent:** Verify the skill handles a scene with no continuity baseline.

**Input:**

```
/qa-consistency
[paste single standalone scene with no prior chapters or worldbuilding]
```

**Expected behavior:**

- [ ] Reports that limited continuity checking is possible without prior context
- [ ] Still checks internal consistency within the scene (object state, timeline within scene, spatial logic)
- [ ] Does not fabricate a continuity baseline

**Expected output:**

- CONTAINS: note about limited continuity checking without prior context
- CONTAINS: internal consistency findings within the scene

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
