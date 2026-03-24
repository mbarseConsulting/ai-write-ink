---
name: step-01-genre
description: 'Calibrate genre conventions for the forge session'

nextStepFile: './step-02-scope.md'

context:
  reads: [user input]
  produces: [genre conventions -- frozen for session]
---

# Step 1/6: Genre Calibration

## STEP GOAL

Produce a frozen set of genre conventions (genre name, key conventions, failure modes) that will drive all downstream evaluation.

## CONTEXT BOUNDARIES

**You have:** The user's original input.
**Validated before you:** Nothing -- this is the first step.
**You pass forward:** Genre name, key conventions, failure modes -- frozen for the session.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Invoke `/calibrate-ink` on the user's input.
- Present results and HALT for user validation.
- Do NOT proceed to the next step until user says OK.

## Sequence of Instructions

### 1. Invoke /calibrate-ink

Run `/calibrate-ink` on the user's input material. Let calibrate-ink identify the genre from the content. If ambiguous, calibrate-ink will ask -- let it.

### 2. Present Results

```
## Step 1/6 -- Genre

[calibrate-ink output -- genre name, key conventions, failure modes]

[OK / ADJUST]
```

### 3. Handle User Response

- **OK:** Genre conventions are frozen for the session. Read fully and follow: `{nextStepFile}`
- **ADJUST:** User provides corrections. Re-run /calibrate-ink with adjustments. Return to step 2.
- **Any other input:** Answer the user's question, then re-display the menu.

## Success/Failure Metrics

**Success:**
- Genre identified with clear conventions
- User explicitly validated with OK
- Conventions frozen for the session

**Failure:**
- Proceeding without user validation
- Running next skill before OK received
- Generic genre identification without specific conventions

