# dialog-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `dialog-ink`                               |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Two characters in a defined space

**Intent:** Verify dialogue with physical staging and spatial awareness.

**Context:** User provides a two-character scene with explicit spatial setup (kitchen, positions).

**Input:**

```
/dialog-ink
Two sisters meet in a small kitchen after ten years apart. The elder is standing by the stove. The younger just walked in through the back door.
```

**Expected behavior:**

- [ ] Loads agent persona from `agents/agent-dialog-ink.md`
- [ ] Produces dialogue with physical staging (not just floating voices)
- [ ] Characters move in the space (kitchen, stove, back door are used)
- [ ] Both voices are distinct (different speech patterns, different energy)
- [ ] Physical action reflects the emotional subtext of the exchange

**Expected output:**

- STRUCTURE: output is raw dialogue material with staging, not polished prose
- CONTAINS: spatial references to kitchen, stove, and/or back door
- CONTAINS: distinct speech patterns for each sister

**Anti-patterns (must NOT happen):**

- [ ] Produces dialogue without any physical action or staging
- [ ] Characters are indistinguishable in voice
- [ ] Ignores the spatial setup (kitchen, stove, door)

---

### S02 — Tense confrontation scene

**Intent:** Verify that dialogue carries subtext and physical action reflects emotional state.

**Context:** Power-asymmetry scene with an information gap between characters.

**Input:**

```
/dialog-ink
A boss calls an employee into her office. She knows he's been stealing. He doesn't know she knows. Corner office, glass walls, late afternoon.
```

**Expected behavior:**

- [ ] Dialogue carries subtext (she's probing, he's deflecting)
- [ ] Physical action reflects power dynamics (who sits, who stands, who touches objects)
- [ ] The glass walls and late afternoon are present in staging
- [ ] Tension escalates through the exchange, not just through words

**Expected output:**

- CONTAINS: subtext-driven dialogue (probing/deflecting pattern)
- CONTAINS: power-dynamic physical staging
- CONTAINS: setting elements (glass walls, late afternoon light)

**Anti-patterns (must NOT happen):**

- [ ] Characters state their intentions directly with no subtext
- [ ] Scene is all dialogue with no physical beats
- [ ] Setting is mentioned once then forgotten

---

### S03 — Multi-character scene (3+ characters)

**Intent:** Verify management of turn-taking, distinct voices, and spatial positioning with more than two characters.

**Context:** Three characters in a confined social space with conflicting loyalties.

**Input:**

```
/dialog-ink
Three friends at a bar booth. One just confessed to an affair. The second is the spouse's best friend. The third is trying to keep the peace. Crowded bar, Friday night.
```

**Expected behavior:**

- [ ] All three characters have distinct voices
- [ ] Turn-taking is managed (no character disappears for too long)
- [ ] Spatial positioning is tracked (booth seating, who faces whom)
- [ ] The crowded bar environment is present (noise, interruptions, proximity)
- [ ] Each character's role (confessor, loyalist, peacemaker) is clear through dialogue and action

**Expected output:**

- COUNT: 3 distinct character voices present
- CONTAINS: environmental details from the crowded bar
- STRUCTURE: turn-taking distributed across all three characters

**Anti-patterns (must NOT happen):**

- [ ] One character dominates while others vanish
- [ ] Characters lose spatial coherence (impossible movements)
- [ ] All three sound identical

---

## Edge Cases

### E01 — No characters specified

**Intent:** Verify that dialog-ink asks for characters before writing.

**Input:**

```
/dialog-ink
Write a confrontation scene.
```

**Expected behavior:**

- [ ] Does not start writing immediately
- [ ] Asks who the characters are, where they are, what's at stake
- [ ] Does not invent characters without author input

**Expected output:**

- CONTAINS: questions about characters, location, or stakes

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
