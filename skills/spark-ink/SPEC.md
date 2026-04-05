# spark-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `spark-ink`                                |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Subversive angles on a scene premise

**Intent:** Validates that spark-ink generates narrative angles that subvert expectations on a scene.

**Context:** User provides a conventional emotional scene premise (funeral reunion).

**Input:**

```
/spark-ink a reunion scene between estranged siblings at a funeral
```

**Expected behavior:**

- [ ] Displays `[SPARK-INK — ON]` tag
- [ ] Generates angles that detonate the premise out of its default orbit
- [ ] Each angle subverts the expected version of this scene (grief, reconciliation, etc.)
- [ ] Angles are narratively actionable — not abstract thematic commentary

**Expected output:**

- COUNT: at least 3 distinct subversive angles
- STRUCTURE: each angle is narratively actionable, not abstract
- CONTAINS: angles that avoid the default emotional beats (tears, hug, forgiveness)

**Anti-patterns (must NOT happen):**

- [ ] Produces the obvious emotional beats (tears, hug, forgiveness)
- [ ] Generates generic writing advice ("show don't tell", "use subtext")
- [ ] Angles could apply to any scene, not specifically this one

---

### S02 — Non-obvious character version

**Intent:** Validates that spark-ink finds the unexpected version of a character concept.

**Context:** User provides a character concept that has a well-known trope version.

**Input:**

```
/spark-ink a villain who genuinely believes they're saving the world
```

**Expected behavior:**

- [ ] Displays `[SPARK-INK — ON]` tag
- [ ] Finds versions of this character that are NOT the standard "sympathetic villain" trope
- [ ] Each angle reframes what "believes they're saving the world" could actually look like
- [ ] At least one angle makes the reader uncomfortable about agreeing with the villain

**Expected output:**

- COUNT: at least 3 distinct character versions
- CONTAINS: at least one version that avoids the Thanos/Ozymandias archetype
- CONTAINS: at least one version that creates reader discomfort

**Anti-patterns (must NOT happen):**

- [ ] Produces the Thanos/Ozymandias archetype without a twist
- [ ] Falls back on "make them more human" as the angle
- [ ] Offers character traits without narrative consequence

---

### S03 — Unexpected plot directions

**Intent:** Validates that spark-ink offers plot directions the author would not have considered.

**Context:** User provides a classic betrayal/revelation plot point.

**Input:**

```
/spark-ink the protagonist discovers their mentor has been lying to them for years
```

**Expected behavior:**

- [ ] Displays `[SPARK-INK — ON]` tag
- [ ] Offers directions beyond the obvious (confrontation, betrayal arc, trust collapse)
- [ ] At least one angle reframes who the real victim is
- [ ] Directions are specific enough to write toward, not just thematic gestures

**Expected output:**

- COUNT: at least 3 distinct plot directions
- CONTAINS: at least one direction that reframes victim/perpetrator
- STRUCTURE: directions are specific enough to write toward

**Anti-patterns (must NOT happen):**

- [ ] All angles lead to the same emotional arc (anger -> acceptance)
- [ ] Produces options that any writing prompt generator would produce

---

## Edge Cases

### E01 — Premise is already subversive

**Intent:** Validates that spark-ink does not dilute an already subversive premise back toward safe territory.

**Input:**

```
/spark-ink a love story where both characters are actively trying to destroy each other
```

**Expected behavior:**

- [ ] Recognizes the premise is already subversive
- [ ] Does not retreat toward "but maybe they secretly love each other"
- [ ] Pushes further into the tension, finds angles that escalate rather than resolve

**Expected output:**

- CONTAINS: angles that escalate the premise rather than resolving it
- STRUCTURE: no retreat toward conventional romance resolution

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
