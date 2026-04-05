# outline-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `outline-ink`                              |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Story premise to multi-level outline

**Intent:** Verify that a story premise produces a hierarchical outline from arcs down to scenes.

**Context:** User provides a high-level trilogy premise with thematic tags per book.

**Input:**

```
/outline-ink
A trilogy where magic is slowly disappearing from the world. Book 1: discovery. Book 2: resistance. Book 3: renaissance or extinction.
```

**Expected behavior:**

- [ ] Loads agent persona from `agents/agent-outline-ink.md`
- [ ] Produces a multi-level structure (arc -> chapters -> scenes)
- [ ] Each level has distinct granularity (arcs are thematic, chapters are structural, scenes are concrete)
- [ ] The outline covers all three books at appropriate depth
- [ ] Structure is interactive — works with the author section by section

**Expected output:**

- STRUCTURE: hierarchical outline with at least 3 levels (arc, chapter, scene)
- COUNT: all 3 books addressed
- CONTAINS: distinct granularity at each level

**Anti-patterns (must NOT happen):**

- [ ] Produces prose instead of structure
- [ ] Dumps the entire outline in one block with no interaction
- [ ] Stays at one level only (e.g., only arcs, no chapters or scenes)

---

### S02 — Expand a chapter into scene beats

**Intent:** Verify drilling down from a chapter outline to scene-level detail.

**Context:** User provides a single chapter summary and asks for scene-beat expansion.

**Input:**

```
/outline-ink
Expand Chapter 3 into scene beats:

Chapter 3 — "The Silence": The protagonist discovers the village where magic died first. She meets the last person who remembers. He refuses to talk. She finds his journal instead.
```

**Expected behavior:**

- [ ] Breaks the chapter into individual scene beats
- [ ] Each beat has a clear function (setup, tension, reveal, etc.)
- [ ] Beats are sequenced with pacing awareness
- [ ] The four story elements (village, last person, refusal, journal) are all addressed

**Expected output:**

- COUNT: at least 4 scene beats (matching the 4 story elements)
- CONTAINS: function label for each beat
- STRUCTURE: beats are sequenced, not just listed

**Anti-patterns (must NOT happen):**

- [ ] Rewrites the chapter summary as prose
- [ ] Produces a single-level list without scene structure
- [ ] Ignores story elements present in the input

---

### S03 — Restructure an existing outline

**Intent:** Verify that outline-ink can reorganize an existing structure with rationale.

**Context:** User provides an 8-chapter outline they feel is structurally flawed and asks for reorganization.

**Input:**

```
/outline-ink
This outline feels wrong. The reveal comes too early and the middle sags. Restructure:

Ch1: Setup. Ch2: Inciting incident. Ch3: The big reveal. Ch4: Aftermath. Ch5: Subplots. Ch6: Build to climax. Ch7: Climax. Ch8: Resolution.
```

**Expected behavior:**

- [ ] Identifies the structural problems (early reveal, sagging middle)
- [ ] Proposes a reorganized structure
- [ ] Each change has explicit rationale (why move the reveal, what fills the middle)
- [ ] Preserves all story elements — reorganizes, doesn't delete

**Expected output:**

- CONTAINS: identification of structural problems
- CONTAINS: rationale for each proposed change
- STRUCTURE: all 8 original story elements preserved in new order

**Anti-patterns (must NOT happen):**

- [ ] Accepts the outline as-is
- [ ] Deletes story elements during reorganization
- [ ] Produces prose instead of structure

---

## Edge Cases

### E01 — Premise too vague to outline

**Intent:** Verify that outline-ink asks clarifying questions before structuring.

**Input:**

```
/outline-ink
I want to write a fantasy novel.
```

**Expected behavior:**

- [ ] Does not start outlining immediately
- [ ] Asks clarifying questions about scope, genre conventions, tone, central conflict
- [ ] Identifies what's missing before proposing structure

**Expected output:**

- CONTAINS: clarifying questions about the project
- STRUCTURE: no outline produced before clarification

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
