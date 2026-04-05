# brief-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `brief-ink`                                |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Rich scene prompt extraction

**Intent:** Verify that a rich scene prompt is decomposed into classified, weighted, sequenced intentions.

**Context:** User provides a multi-beat scene prompt with action, emotion, dialogue, and subtext.

**Input:**

```
/brief-ink
She sits on the bed. He won't look at her. She waits. He says "I know" but he knows nothing. She wants to scream but she just places her hand on the sheet, next to his, without touching.
```

**Expected behavior:**

- [ ] Extracts intentions (not events, not a summary)
- [ ] Classifies each intention by treatment type (action, emotion, dialogue, subtext, atmosphere, etc.)
- [ ] Weights each element by importance (heavy, medium, light)
- [ ] Sequences elements in a scene order (which may differ from prompt order)

**Expected output:**

- STRUCTURE: output is a structured brief, not prose
- CONTAINS: classified treatment types for each intention
- CONTAINS: weight indicators (heavy, medium, light or equivalent)
- COUNT: at least 3 distinct intentions extracted

**Anti-patterns (must NOT happen):**

- [ ] Produces prose instead of a brief
- [ ] Lists events in prompt order without resequencing
- [ ] Gives craft instructions ("use short sentences", "show don't tell")
- [ ] Invents context not present in the prompt

---

### S02 — Gold-dial mode preserves verbatim lines

**Intent:** Verify that `--gold-dial` keeps dialogue lines as GOLD (verbatim) while parsing everything else.

**Context:** User invokes with `--gold-dial` flag on a prompt mixing dialogue and action.

**Input:**

```
/brief-ink --gold-dial
He looked at her and said "I never loved you." She picked up the glass and threw it. "Get out." He didn't move.
```

**Expected behavior:**

- [ ] Dialogue lines ("I never loved you", "Get out") are marked as GOLD — preserved verbatim
- [ ] Non-dialogue elements are parsed and classified normally
- [ ] GOLD elements appear in the sequence at their natural position

**Expected output:**

- CONTAINS: GOLD marker on dialogue lines
- STRUCTURE: brief distinguishes GOLD from non-GOLD elements clearly
- COUNT: exactly 2 GOLD dialogue elements

**Anti-patterns (must NOT happen):**

- [ ] Rewrites or paraphrases the GOLD dialogue lines
- [ ] Marks non-dialogue as GOLD
- [ ] Produces prose

---

### S03 — Vague prompt with implied intentions

**Intent:** Verify that implicit intentions are surfaced explicitly.

**Context:** User provides a prompt composed entirely of mundane actions with no stated emotion.

**Input:**

```
/brief-ink
He tidied the dishes. Checked the lock. Turned off the hallway light. Stood in the dark.
```

**Expected behavior:**

- [ ] Extracts intentions beyond the surface actions
- [ ] Surfaces the implied subtext (ritual, solitude, waiting, control)
- [ ] Does not just list the four actions as scene beats
- [ ] Identifies the emotional trajectory beneath the mundane

**Expected output:**

- CONTAINS: subtext identification (ritual, solitude, waiting, control, or equivalent)
- STRUCTURE: output goes beyond surface-level action listing
- CONTAINS: emotional trajectory or arc beneath the mundane actions

**Anti-patterns (must NOT happen):**

- [ ] Produces a flat list of actions with no subtext extraction
- [ ] Produces prose
- [ ] Adds context the author didn't provide

---

## Edge Cases

### E01 — Prompt that IS already a brief

**Intent:** Verify that brief-ink recognizes an already-structured input and doesn't re-brief it.

**Input:**

```
/brief-ink
SUBTEXT: she's testing him. ATMOSPHERE: cold kitchen, morning light. GOLD: "You promised." SEQUENCE: 1. She enters. 2. Silence. 3. The line. 4. He looks away.
```

**Expected behavior:**

- [ ] Recognizes the input is already structured as a brief
- [ ] Does not re-process into another brief
- [ ] Acknowledges the structure or asks if refinement is needed

**Expected output:**

- CONTAINS: acknowledgment that input is already a brief

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
