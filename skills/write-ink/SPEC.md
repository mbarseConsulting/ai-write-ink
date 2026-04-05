# write-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `write-ink`                                |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Scene prompt with setting and characters

**Intent:** Verify that a rich scene prompt produces narrative prose with correct POV and no meta-commentary.

**Context:** User provides a scene prompt with characters, setting, emotional stakes, and spatial details.

**Input:**

```
/write-ink
Two sisters meet at a train station after ten years. The elder wants an apology. The younger doesn't even know what she did. Late evening, platform 4, the last train has already left.
```

**Expected behavior:**

- [ ] Loads agent persona from `agents/agent-write-ink.md`
- [ ] Produces narrative prose (not a summary, not a list, not an outline)
- [ ] Maintains a consistent POV throughout the scene
- [ ] Physical setting (station, platform, evening) is woven into the prose
- [ ] Both characters are present and distinct

**Expected output:**

- STRUCTURE: narrative prose, not summary/outline/bullets
- CONTAINS: physical setting elements (station, platform, evening)
- CONTAINS: both characters present and distinguishable
- No meta-commentary, no craft notes, no "here's what I wrote"

**Anti-patterns (must NOT happen):**

- [ ] Paraphrases the prompt back instead of writing a scene
- [ ] Produces analysis, summary, or bullet points instead of prose
- [ ] Breaks POV mid-scene without justification
- [ ] Adds meta-commentary about the writing

---

### S02 — Continuation of existing text

**Intent:** Verify that continuation matches tone, style, and register of the preceding text.

**Context:** User provides existing prose and asks for continuation.

**Input:**

```
/write-ink
Continue this:

He set the cup on the edge of the table, right where the wood was marked by twenty years of cups placed in the same spot. The kitchen smelled of cold coffee and of something else — something that had been there so long it no longer had a name.
```

**Expected behavior:**

- [ ] Matches the register (literary, measured, quiet)
- [ ] Matches the rhythm (mid-length sentences, precise physical detail)
- [ ] Matches vocabulary level (no sudden shift to casual or ornate)
- [ ] Continues the scene rather than restarting it
- [ ] Preserves the implied character and setting

**Expected output:**

- MATCH: register matches the source (literary, measured, quiet)
- MATCH: rhythm matches the source (mid-length sentences, precise physical detail)
- STRUCTURE: continuation, not a restart or summary of the source

**Anti-patterns (must NOT happen):**

- [ ] Shifts to a different register or energy level
- [ ] Rewrites the provided text instead of continuing it
- [ ] Introduces a dramatic event that breaks the established tone

---

### S03 — Rewrite request with specific direction

**Intent:** Verify surgical rewrite that preserves what works and changes what's directed.

**Context:** User provides a passage with a specific editorial direction for the rewrite.

**Input:**

```
/write-ink
Rewrite this passage — make her angrier, but keep it cold, not explosive:

She looked at him across the table. "You could have told me," she said. He didn't answer. She picked up her glass and drank.
```

**Expected behavior:**

- [ ] Rewrites the passage, not the whole scene
- [ ] The character reads as angrier (cold anger, not explosive)
- [ ] Preserves elements that already work (the setting, the silence, the glass)

**Expected output:**

- STRUCTURE: result is prose, not a diff or annotation
- CONTAINS: cold anger conveyed through the character's actions/dialogue
- CONTAINS: preserved elements from original (table, silence, glass)

**Anti-patterns (must NOT happen):**

- [ ] Produces a completely new scene instead of a rewrite
- [ ] Makes the anger explosive/loud despite the "cold" direction
- [ ] Adds explanatory notes about what was changed

---

## Edge Cases

### E01 — No context provided (bare prompt)

**Intent:** Verify that write-ink asks for minimum context before writing when prompt is too bare.

**Input:**

```
/write-ink
Write a scene.
```

**Expected behavior:**

- [ ] Does not start writing immediately
- [ ] Asks for minimum context (who, where, what's at stake)
- [ ] Does not invent characters or setting without author input

**Expected output:**

- CONTAINS: questions asking for context (characters, setting, stakes)

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
