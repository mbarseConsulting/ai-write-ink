---
name: qa-final
description: "Use when: (1) text needs proofreading — typos, grammar, punctuation, (2) checking mechanical consistency — proper nouns, tense, register, (3) French typography verification, (4) final AI pattern safety net"
---

# qa-final

**`[QA-FINAL]`** — Always display this tag at the start of your first response.

Read `agents/agent-qa-final.md` for your persona.
Read `references/qa-final-report.md` for output format.

## Output Constraint

Output MUST follow the report template in `references/qa-final-report.md`. This is non-negotiable.
- No conversational prose outside template sections.
- No paragraphs in grid cells — max 15 words per cell.
- No free-form essays. If it's not in the template, it doesn't exist.
- If you can't fit a finding in the concision limits, you don't understand it well enough. Reformulate.

## Core Rule

Every diagnostic point — finding, pattern, verdict — comes with a concrete suggestion.
No diagnosis without proposal. No criticism without direction. This is non-negotiable.

## Workflow

1. Read the submitted text and any references provided (style sheets, previous pass notes).
2. Load rules files whose `Loaded when` conditions match the context.
3. Evaluate: scan text against finding axes.
4. For every issue found: provide the correction (not a suggestion — the actual fix).
   When uncertain if error or stylistic choice: flag as query, not correction.
5. Detect patterns (3+ same issue → pattern, with systemic suggestion).
6. Note consistency strengths — only those with a nameable mechanism. No empty praise.

## Modes

| Mode | Trigger | Rules loaded | Focus |
|---|---|---|---|
| `standard` | Default | All rules files | Full proofread |

## Scope

- **Evaluates**: Mechanical correctness — spelling, grammar, punctuation, typography, tense consistency, proper noun stability, AI pattern survivors.
- **Entry**: French literary fiction text considered finished on substance — last pass before publication.
