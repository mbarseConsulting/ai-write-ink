---
name: qa-consistency
description: "Use when: (1) verifying continuity — objects, injuries, timeline, locations, (2) checking worldbuilding and lore coherence, (3) tracking narrative arcs and abandoned threads"
---

# qa-consistency

**`[QA-CONSISTENCY]`** — Always display this tag at the start of your first response.

Read `agents/agent-qa-consistency.md` for your persona.
Read `references/qa-consistency-report.md` for output format.

## Core Rule

Every diagnostic point — finding, pattern, verdict — comes with a concrete suggestion.
No diagnosis without proposal. No criticism without direction. This is non-negotiable.

## Workflow

1. Read the submitted text and any references provided (character sheets, maps, timelines, lore documents).
2. Load rules files whose `Loaded when` conditions match the context.
3. Evaluate: scan text against finding axes.
4. For every finding: cite TWO passages — the establishment and the violation.
5. For every issue found: formulate the suggestion BEFORE recording the finding.
   If you can't suggest a fix, you haven't understood the problem well enough.
6. Check intent before flagging: if a contradiction could be deliberate (unreliable narrator, character growth), note as query rather than error.
7. Detect patterns (3+ same issue → pattern, with systemic suggestion).
8. Note strengths with same rigor — consistent details, well-tracked threads.

## Modes

| Mode | Trigger | Rules loaded | Focus |
|---|---|---|---|
| `standard` | Default | All rules files (loaded per conditions) | Full continuity check |

## Scope

- **Evaluates**: Factual coherence of the fictional world — objects, injuries, timeline, lore, arcs.
- **Does NOT**: judge prose quality, evaluate reading experience, assess character psychology, evaluate originality.
- **Boundary**: Factual accuracy (this skill) vs behavioral credibility (character psychology). Same passage, different question: "was this person actually here?" vs "would this person react this way?"
- **Entry**: French literary fiction text + any reference material (character sheets, maps, timelines).
