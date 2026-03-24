---
name: step-03-brief
description: 'Extract structured intent from the input using brief-ink'

nextStepFile: './step-04-crit.md'
previousStepFile: './step-02-scope.md'

context:
  reads: [user input, genre conventions from step 1, scope from step 2]
  produces: [validated brief including READER FEEL -- passed to agents via Forge Contract]
---

# Step 3/6: Brief Extraction

## STEP GOAL

Produce a validated /brief-ink output (all sections populated, READER FEEL explicit with opening/turn/close, GAPS flagged) that becomes the foundation agents build prose from.

## CONTEXT BOUNDARIES

**You have:** The user's original input, genre conventions from Step 1, scope from Step 2.
**Validated before you:** Genre (Step 1), scope and ink chain (Step 2).
**You pass forward:** The full validated brief (all /brief-ink sections), READER FEEL (opening/turn/close), identified GAPS.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Invoke `/brief-ink` on the user's input.
- If input > 1000 lines: invoke `/steps` first, then feed chunked analysis into `/brief-ink`.
- Present the full brief and HALT for user validation.
- Do NOT proceed to the next step until user says OK.

## Sequence of Instructions

### 1. Check Input Length

If the input exceeds 1000 lines, activate `/steps` as a modifier -- chunk the input into ~500-word blocks before feeding to `/brief-ink`.

### 2. Invoke /brief-ink

Run `/brief-ink` on the input. Extract all sections:
- COMPASS (emotional trajectory)
- TENSION ENGINE (the pulling question)
- READER FEEL (opening | turn | close)
- GOLD (verbatim passages to preserve, if any)
- SHOW (emotions to translate into action)
- SCENE (plot beats that must happen)
- ATMOSPHERE (mood, sensory, spatial)
- SUBTEXT (what must be felt, never stated)
- SEQUENCE (proposed beat order)
- TRAPS (scene-specific anti-patterns)
- GAPS (missing context requiring author input)

READER FEEL is mandatory. If /brief-ink does not produce it, AP extracts it from the input: what should the reader feel at opening, at the turn, at close.

### 3. Present Results

```
## Step 3/6 -- Brief

[full brief-ink output]

READER FEEL:
- Opening: [what the reader should feel]
- Turn: [what shifts]
- Close: [what the reader is left with]

GAPS: [list of missing context, if any]

[OK / ADJUST / FILL GAPS]
```

### 4. Handle User Response

- **OK:** Brief is validated. This brief will be passed to agents via the Forge Contract. Read fully and follow: `{nextStepFile}`
- **ADJUST:** User modifies intentions. Re-run /brief-ink with adjustments. Return to step 3.
- **FILL GAPS:** User provides the missing context. Re-run /brief-ink with added context. Return to step 3.
- **Any other input:** Answer the user's question, then re-display the menu.

## Success/Failure Metrics

**Success:**
- All brief-ink sections populated (or explicitly marked empty with reason)
- READER FEEL explicitly present with opening/turn/close
- GAPS identified and flagged to user
- User explicitly validated with OK (or filled gaps first)

**Failure:**
- Incomplete brief (missing sections without reason)
- READER FEEL absent or vague
- Not flagging GAPS to user
- Proceeding with unfilled GAPS without user acknowledgment
- Skipping /steps on long input

