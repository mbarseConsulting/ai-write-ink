---
name: step-02-scope
description: 'Detect and validate the scope of the prose to produce'

nextStepFile: './step-03-brief.md'
previousStepFile: './step-01-genre.md'

context:
  reads: [user input, genre conventions from step 1]
  produces: [scope, ink chain -- both frozen for session]
---

# Step 2/6: Scope Detection

## STEP GOAL

Produce a locked scope (SCENE / CHAPTER / SEQUENCE) and its derived ink chain -- the single source of truth for which skills agents will run.

## CONTEXT BOUNDARIES

**You have:** The user's original input and genre conventions from Step 1.
**Validated before you:** Genre (Step 1).
**You pass forward:** Scope label, scope reasoning, ink chain definition, agent-evaluated skill criteria.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Apply the scope heuristic on the user's input.
- Present detected scope AND the derived ink chain. HALT for user validation.
- Do NOT proceed to the next step until user says OK.

## Sequence of Instructions

### 1. Apply Scope Heuristic

Analyze the input against these signals:

| Signal | Scope |
|--------|-------|
| Single moment, one POV, continuous time | SCENE |
| Multiple beats, time jumps, scene breaks | CHAPTER |
| Multi-chapter, arc-level structure | SEQUENCE |

If the user provided a `--scene`, `--chapter`, or `--sequence` flag, use that override directly.

### 2. Derive Ink Chain

Based on detected scope, the ink chain is:

- **SCENE:** validated brief -> /write-ink
- **CHAPTER:** validated brief -> /outline-ink --chapter -> /write-ink
- **SEQUENCE:** validated brief -> /outline-ink --chapter -> /arch-ink -r -> /write-ink

In all scopes, agents additionally evaluate pertinence of:
- `/outline-ink --script` per scene (multi-beat = YES, single continuous moment = NO)
- `/dialog-ink` per scene (dialogue-heavy = YES, narration-only = NO)

This is the single source of truth for the ink chain. The Forge Contract will reference this output.

### 3. Present Results

```
## Step 2/6 -- Scope

Detected: [SCENE / CHAPTER / SEQUENCE]
Reason: [specific signals found in the input]

Ink chain: [chain for this scope]

Agent-evaluated additions:
  /outline-ink --script: agent decides per scene (multi-beat = YES, single moment = NO)
  /dialog-ink: agent decides per scene (dialogue-heavy = YES, narration-only = NO)

[OK / ADJUST]
```

### 4. Handle User Response

- **OK:** Scope and ink chain are locked. Read fully and follow: `{nextStepFile}`
- **ADJUST:** User changes scope. Recalculate ink chain. Return to step 3.
- **Any other input:** Answer the user's question, then re-display the menu.

## Success/Failure Metrics

**Success:**
- Scope detected with clear reasoning from input signals
- Ink chain correctly derived from scope
- User explicitly validated with OK

**Failure:**
- Guessing scope without citing input signals
- Wrong ink chain for detected scope
- Proceeding without user validation

