---
name: step-04-crit
description: 'Challenge the brief with /crit to surface weaknesses before craft'

nextStepFile: './step-05-preflight.md'
previousStepFile: './step-03-brief.md'

context:
  reads: [validated brief from step 3, genre conventions from step 1]
  produces: [crit findings -- carried as warnings in Forge Contract]
---

# Step 4/6: Critical Challenge

## STEP GOAL

Produce actionable /crit findings (completeness gaps, contradictions, vague directives, execution traps) against the validated brief, carried as warnings in the Forge Contract.

## CONTEXT BOUNDARIES

**You have:** The validated brief from Step 3, genre conventions from Step 1.
**Validated before you:** Genre (Step 1), scope and ink chain (Step 2), brief (Step 3).
**You pass forward:** /crit findings as warnings -- agents receive these as known risks to mitigate.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Invoke `/crit` on the brief validated at Step 3.
- Present findings and HALT for user validation.
- Do NOT proceed to the next step until user says OK.

## Sequence of Instructions

### 1. Invoke /crit on the Brief

Run `/crit` on the brief output from Step 3. Focus on:
- Completeness: are there missing intentions the input implies but the brief doesn't capture?
- Contradictions: do any brief sections conflict with each other?
- Vagueness: are any SCENE beats or SHOW directives too abstract to execute?
- Traps: what will go wrong if agents follow this brief literally?

### 2. Present Findings

```
## Step 4/6 -- Crit

[crit findings -- biggest problems first, evidence-based, citing brief sections]

[OK / ADJUST BRIEF]
```

### 3. Handle User Response

- **OK:** Brief stands as-is despite findings. Findings will feed into the Forge Contract as warnings. Read fully and follow: `{nextStepFile}`
- **ADJUST BRIEF:** User wants to fix the brief based on crit findings. Return to `{previousStepFile}` (Step 3) with crit findings as additional input. Re-run /brief-ink.
- **Any other input:** Answer the user's question, then re-display the menu.

## Success/Failure Metrics

**Success:**
- /crit run against the brief (not the user's raw input) with evidence-based findings
- Findings clearly actionable (user knows what to fix)
- User explicitly validated with OK or chose to adjust brief

**Failure:**
- Soft crit (hedging, praise-first, no evidence)
- Not citing specific brief sections in findings
- Proceeding without user validation
- Not offering the ADJUST BRIEF option

