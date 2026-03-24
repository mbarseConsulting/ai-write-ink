---
name: mod-ink
description: "Use when: (1) applying modifications to existing prose — editorial direction, not just a fix, (2) changes risk breaking continuity with surrounding text, (3) author gives a direction that needs propagation beyond a single phrase"
---

**`[MOD]`** -- Display immediately.

## OPTIONS

| Flag        | Effect                                                             |
| ----------- | ------------------------------------------------------------------ |
| `--inline`  | Line-level edits allowed. Voice lock and continuity still apply.   |
| `--dry`     | Show the change plan only. Do not execute.                         |
| `--verbose` | Append per-passage diff contract (CHANGED/BROKE/FIX) after output. |

## BEHAVIOR

This modifier changes HOW you apply text modifications. It does not change WHAT you write. Combines with any active skill or task.

### Intent extraction

Before anything else, interpret the author's direction as intent, not literal instruction. "Make him more hesitant" is a power dynamic shift across every passage carrying that dynamic -- not an "euh" inserted in one line of dialogue. Name the intent in one sentence.

### Propagation rule

Every modification triggers a bidirectional scan. After changing passage X, read every passage -- upstream and downstream -- that references, continues, depends on, or sets up X. If any of them now contradicts, dangles, or mismatches in tone -- that passage enters the modification set. Repeat until no new passages are affected.

### Voice lock

Before modifying, extract and lock the text's voice profile. Four parameters:

1. **Register** -- Identify it explicitly (literary, oral, neutral, raw, other). If a word you are about to write would not appear in the surrounding three paragraphs, replace it.
2. **Sentence rhythm** -- Count the average clause depth in the surrounding paragraphs. Measure the dominant pattern: short declarative, long subordinated, mixed, fragmented. Match it in your rewrite.
3. **Vocabulary boundary** -- List 3-5 words characteristic of the text's lexical field. Every paragraph you rewrite must stay within that field. If you cannot find a synonym inside the boundary, flag it to the author.
4. **Narrator stance** -- Name the stance (intimate first-person, distant third, omniscient, etc.). If your rewrite shifts the psychic distance, you broke it. Revert.

**Voice verification:** Write 2-3 sentences that could belong in the text. They must satisfy all four parameters above. If the samples sound cleaner or more "correct" than the original, voice is broken -- redo.

### Author gate

Before executing, present intent, change plan, and voice lock together:

```
INTENT: [one sentence -- the direction as interpreted]

DIRECT HITS:
  [1] Paragraph N ("first five words...") -- WHAT changes, WHY (intent link)
  [2] ...

PROPAGATION TARGETS:
  [3] Paragraph M ("first five words...") -- propagation from [1]: WHAT breaks, HOW you fix it
  [4] Paragraph K ("first five words...") -- upstream from [1]: setup now over-promises, HOW you fix it
  [5] Seam between N and N+1 -- transition mismatches because X
  ...

VOICE LOCK:
  Register: [named]
  Rhythm: [pattern + clause depth]
  Vocabulary boundary: [3-5 words]
  Narrator stance: [named]
  Samples:
    - [sentence 1]
    - [sentence 2]
```

`--dry` stops here. No modifications before approval.

### Executing

- **Minimum unit: the paragraph.** Rewrite the full paragraph so rhythm, tone, and transitions integrate. Exception: `--inline` permits line-level edits when the change is local and no rhythm or transition breaks.
- **Additions** are written in the locked voice. Re-read neighboring paragraphs to verify transitions read as continuous.
- **Cuts** -- after removing a passage, read the paragraph before and after as a continuous pair. If the join breaks, rewrite the bridging paragraph.
- **Zone expansion** -- if modifying a passage reveals a break not in the original plan, that passage enters the modification set. Mark it `[EXPANDED]` in the output.
- **Untouched paragraphs stay untouched.** Do not improve what the direction does not require.
- **High modification density** -- if more than half the paragraphs enter the modification set, stop and warn the author: "This is approaching a rewrite. Confirm you want mod, not a full rewrite."

### Post-execution seam check

After all modifications, read every boundary between a modified and an unmodified paragraph. Verify: (a) no logical gap, (b) no tonal shift, (c) no dangling reference. If any boundary fails, extend the modification to the bridging paragraph and re-check.

### Diff visibility

Mark every modified paragraph with an inline marker:

- `[mod]` before paragraphs you rewrote (direct hits)
- `[prop]` before paragraphs modified due to propagation
- `[seam]` before paragraphs modified only to fix a transition

## OUTPUT

`--inline` -> modified text in conversation. Default -> write to the same file.
`--verbose` -> append per-passage diff contract after the modified text.

## ACTIVATION - DEACTIVATION - HANDOFF

Applies to this response only. Auto-resets after.
