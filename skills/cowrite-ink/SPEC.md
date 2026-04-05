# cowrite-ink — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `cowrite-ink`                              |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none`                                     |

## Scenarios

### S01 — Author is stuck on a scene

**Intent:** Verify that cowrite-ink provides actionable directions and alternative beats, not prose.

**Context:** No special setup. User describes a writing block on a specific transition.

**Input:**

```
/cowrite-ink
I'm stuck on the transition between the murder and the next morning. I don't know how to make 8 hours pass without it being flat.
```

**Expected behavior:**

- [ ] Loads agent persona from `agents/agent-cowrite-ink.md`
- [ ] Provides concrete, actionable directions (not abstract advice)
- [ ] Proposes multiple alternative approaches to the transition
- [ ] Asks narrowing questions to understand the author's instinct
- [ ] Stays in discussion mode throughout

**Expected output:**

- COUNT: at least 2 alternative approaches proposed
- STRUCTURE: output is discussion/directions, not prose
- CONTAINS: narrowing questions to the author

**Anti-patterns (must NOT happen):**

- [ ] Writes the transition scene as prose
- [ ] Gives generic advice ("show, don't tell", "use sensory detail")
- [ ] Provides only one option with no alternatives

---

### S02 — Critique of a passage

**Intent:** Verify that critique identifies strengths and weaknesses with specific reasoning.

**Context:** User pastes a short passage and asks for feedback.

**Input:**

```
/cowrite-ink
What do you think of this passage?

He ran through the rain. His heart was pounding. He had to get there before it was too late. Every second counted. The streets were empty and the night was dark. He kept running.
```

**Expected behavior:**

- [ ] Identifies specific strengths (if any) with reasoning
- [ ] Identifies specific weaknesses with reasoning (e.g., cliche density, generic action, no sensory specificity)
- [ ] Points to exact phrases or patterns, not vague impressions
- [ ] Suggests directions for improvement without writing the fix

**Expected output:**

- CONTAINS: specific phrase-level references from the passage
- CONTAINS: reasoning for each identified weakness
- STRUCTURE: critique format, not a rewrite

**Anti-patterns (must NOT happen):**

- [ ] Rewrites the passage
- [ ] Says "it's good" or "it needs work" without specifics
- [ ] Gives a laundry list of generic writing rules

---

### S03 — Brainstorming character motivation

**Intent:** Verify that brainstorming explores multiple options and asks narrowing questions.

**Context:** User has a plot point decided but needs help with underlying motivation.

**Input:**

```
/cowrite-ink
My antagonist betrays the protagonist in act 3 but I can't find a motivation that isn't cliche. He's not evil, not jealous, not greedy. What else is there?
```

**Expected behavior:**

- [ ] Explores multiple non-obvious motivations
- [ ] Each option is concrete and tied to the story context
- [ ] Asks questions to narrow down (what does the antagonist value? what's his relationship to the protagonist?)
- [ ] Eliminates the stated cliches (evil, jealous, greedy)

**Expected output:**

- COUNT: at least 3 distinct motivation options
- CONTAINS: narrowing questions about the antagonist
- STRUCTURE: each option is tied to the story, not generic

**Anti-patterns (must NOT happen):**

- [ ] Writes a scene showing the betrayal
- [ ] Suggests evil, jealousy, or greed despite the exclusion
- [ ] Gives a single answer without exploration

---

## Edge Cases

### E01 — User asks cowrite-ink to write actual prose

**Intent:** Verify that cowrite-ink redirects to write-ink and stays in discussion mode.

**Input:**

```
/cowrite-ink
Write the opening scene of my novel. A train station, dawn, a woman with a suitcase.
```

**Expected behavior:**

- [ ] Does not write prose
- [ ] Redirects the author to write-ink for prose production
- [ ] May discuss the scene (angles, tone, POV options) but does not draft it
- [ ] Stays firmly in discussion/critique mode

**Expected output:**

- CONTAINS: redirection to write-ink
- STRUCTURE: discussion or scene analysis, not prose

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
