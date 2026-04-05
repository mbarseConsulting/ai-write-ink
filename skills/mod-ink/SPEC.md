# mod-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `mod-ink`                                  |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Targeted character modification with continuity check

**Intent:** Verify that an editorial direction modifies the target and checks surrounding text for continuity breaks.

**Context:** User provides a passage with an editorial direction to shift a character's emotional state.

**Input:**

```
/mod-ink
Make this character angrier in this passage.

He walked into the room, nodded at her, and sat down. "How was your day?" he asked, folding the newspaper. She didn't answer. He looked up. "Everything okay?" She still didn't answer. He went back to reading.
```

**Expected behavior:**

- [ ] Displays `[MOD]` tag
- [ ] Interprets "angrier" as editorial intent, not a literal word insertion
- [ ] Modifies dialogue, action, and/or interiority to convey anger
- [ ] Checks surrounding text for continuity breaks (e.g., if he's angry in paragraph 2 but calm in paragraph 3)
- [ ] Presents the modification plan before applying (author gate)

**Expected output:**

- CONTAINS: modification plan presented before final output
- STRUCTURE: modified passage conveys anger through action/dialogue, not adverbs
- CONTAINS: continuity check results

**Anti-patterns (must NOT happen):**

- [ ] Inserts the word "angrily" and calls it done
- [ ] Modifies without presenting the plan first
- [ ] Touches paragraphs that are not affected by the change

---

### S02 — Ripple propagation mode

**Intent:** Verify that `--ripple` propagates the change to affected downstream passages.

**Context:** User provides multiple paragraphs where a character trait needs to shift throughout. The `--ripple` flag is used.

**Input:**

```
/mod-ink --ripple
She's no longer afraid of him — she's contemptuous.

[Five paragraphs where the character interacts with fear-based body language, dialogue, and internal monologue]
```

**Expected behavior:**

- [ ] Displays `[MOD]` tag
- [ ] Identifies all passages where fear manifests (body language, dialogue, thoughts)
- [ ] Propagates the shift from fear to contempt across all affected passages
- [ ] Marks propagation targets distinctly from direct hits
- [ ] Verifies seams between modified and unmodified text

**Expected output:**

- CONTAINS: list of identified propagation targets
- STRUCTURE: direct hits and propagation targets are distinguished
- CONTAINS: seam verification between modified and unmodified text

**Anti-patterns (must NOT happen):**

- [ ] Changes only the first occurrence and ignores the rest
- [ ] Rewrites the entire text instead of targeted propagation
- [ ] Breaks the character's voice while propagating

---

### S03 — Tone shift on a paragraph

**Intent:** Verify that a tone adjustment preserves narrative information while changing register.

**Context:** User provides a single paragraph with a directive to shift its register.

**Input:**

```
/mod-ink
Make this paragraph more clinical, detached — like a police report.

She screamed when she saw the body. Her hands were shaking. She couldn't breathe. The room spun around her and she grabbed the doorframe to keep from falling.
```

**Expected behavior:**

- [ ] Shifts tone to clinical/detached without losing the narrative facts
- [ ] Same events are present (seeing the body, physical reaction, grabbing the doorframe)
- [ ] Register change is consistent throughout the paragraph
- [ ] No emotional amplification — the direction is "detached"

**Expected output:**

- CONTAINS: all original narrative events preserved (body, physical reaction, doorframe)
- STRUCTURE: clinical/detached register throughout, no emotional language
- MATCH: tone consistent with police report style

**Anti-patterns (must NOT happen):**

- [ ] Removes narrative information while changing tone
- [ ] Produces a summary instead of a rewritten paragraph
- [ ] Mixes clinical tone with emotional language inconsistently

---

## Edge Cases

### E01 — Contradictory modification direction

**Intent:** Verify that mod-ink surfaces conflicts in editorial direction rather than guessing.

**Input:**

```
/mod-ink
Make him both calmer and more threatening in this scene.

[Dialogue scene between two characters]
```

**Expected behavior:**

- [ ] Surfaces the tension between "calmer" and "more threatening"
- [ ] Asks the author to clarify: calm-threatening (cold menace) vs. pick one
- [ ] Does not silently choose an interpretation

**Expected output:**

- CONTAINS: identification of the contradiction
- CONTAINS: clarification question to the author

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
