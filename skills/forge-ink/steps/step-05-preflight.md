---
name: step-05-preflight
description: 'Run pre-flight diagnostics on source material before committing to craft'

nextStepFile: './step-06-contract.md'
previousStepFile: './step-04-crit.md'

context:
  reads: [user input (source material), scope from step 2]
  produces: [pulse-ink triage, arch-ink findings if SEQUENCE]
---

# Step 5/6: Pre-flight Diagnostic

## STEP GOAL

Produce a pulse-ink triage (color-coded: red/orange/yellow/green with findings) and, if SEQUENCE scope, arch-ink structural findings -- the go/no-go evidence for launching craft.

## CONTEXT BOUNDARIES

**You have:** The user's original input (source material), scope from Step 2.
**Validated before you:** Genre (Step 1), scope and ink chain (Step 2), brief (Step 3), crit findings (Step 4).
**You pass forward:** Pulse line and findings, arch-ink findings (if SEQUENCE) -- both carried into the Forge Contract.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Invoke `/pulse-ink` on the source material.
- If SEQUENCE scope: also invoke `/arch-ink -r` for structural validation.
- Present results and HALT for user validation.
- Do NOT proceed to the next step until user says OK.

## Sequence of Instructions

### 1. Invoke /pulse-ink

Run `/pulse-ink` on the source material. This produces a color-coded triage:
- Red: stock patterns, tropes executed without fresh texture
- Orange: engagement drops
- Yellow: flat dialogue, told emotions, pacing issues, POV drift
- Green: what works and must be protected

### 2. Invoke /arch-ink (conditional)

If the scope detected at Step 2 is **SEQUENCE**: also invoke `/arch-ink -r` on the source material for structural validation (act breaks, midpoints, throughlines).

If scope is SCENE or CHAPTER: skip /arch-ink.

### 3. Present Results

```
## Step 5/6 -- Pre-flight

Pulse: [pulse line -- X red Y orange Z yellow | W green]
[pulse-ink findings]

Arch-ink: [structural findings, if SEQUENCE scope -- or "N/A (scope: SCENE/CHAPTER)"]

[OK -- proceed to contract / ADJUST / STOP]
```

### 4. Handle User Response

- **OK:** Pre-flight passed. Source material is fit for craft. Read fully and follow: `{nextStepFile}`
- **ADJUST:** AP presents routing options as a copy-paste menu:

```
What needs fixing?
[1 -- Brief problems -> return to Step 3]
[2 -- Genre mismatch -> return to Step 1]
[3 -- Source material problems -> you fix the source, then we restart Step 5]
```

User picks a number. AP routes accordingly:
  - **1:** Return to Step 3 (`steps/step-03-brief.md`)
  - **2:** Return to Step 1 (`steps/step-01-genre.md`)
  - **3:** User fixes source, then AP restarts from Step 5.
- **STOP:** Source material has too many issues. Workflow ends. Display **`[FORGE -- OFF]`**.
- **Any other input:** Answer the user's question, then re-display the menu.

## Success/Failure Metrics

**Success:**
- /pulse-ink run with clear triage (pulse line + findings)
- /arch-ink run if SEQUENCE scope
- User explicitly decided: OK, ADJUST, or STOP
- Stock/trope patterns surfaced before craft

**Failure:**
- Skipping /pulse-ink
- Not running /arch-ink on SEQUENCE scope
- Proceeding without user validation
- Downplaying red findings to avoid STOP

