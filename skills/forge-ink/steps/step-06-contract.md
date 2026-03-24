---
name: step-06-contract
description: 'Assemble and validate the Forge Contract before launching agents'

nextPhase: 'Phase 1 -- Craft'
previousStepFile: './step-05-preflight.md'

context:
  reads: [all step 1-5 outputs, user's original input, flags]
  produces: [frozen Forge Contract -- passed to agents at dispatch]
---

# Step 6/6: Forge Contract

## STEP GOAL

Produce the frozen Forge Contract -- a single document assembling all validated Step 1-5 outputs, verified by /check, that agents receive as their complete and only instruction set.

## CONTEXT BOUNDARIES

**You have:** All validated outputs from Steps 1-5, the user's original input, active flags.
**Validated before you:** Genre (Step 1), scope and ink chain (Step 2), brief (Step 3), crit findings (Step 4), pre-flight results (Step 5).
**You pass forward:** The frozen Forge Contract. This is the ONLY document agents receive -- it must be self-contained. Step outputs are transcribed into the contract, not redefined: the contract preserves exactly what each step validated.

## MANDATORY EXECUTION RULES

- Read this entire file before taking any action.
- Assemble the contract from previously validated step outputs.
- Run `/check` to verify the contract captures all user intentions.
- Present the complete contract and HALT for user validation.
- Do NOT launch agents until user says YES.

## Sequence of Instructions

### 1. Assemble the Contract

Compile all validated outputs into the Forge Contract:

```
## FORGE CONTRACT (validate or adjust)

GENRE: [validated at Step 1 -- genre name, conventions, failure modes]

PROMPT: [user's original input -- verbatim, never modified]

SCOPE: [validated at Step 2 -- SCENE / CHAPTER / SEQUENCE]
  Reason: [from Step 2]

INK CHAIN: [validated at Step 2 -- the exact chain for this scope]
  Agent-evaluated: /outline-ink --script and /dialog-ink per scene.

BRIEF:
  [full brief-ink output validated at Step 3]

READER FEEL TARGET:
- Opening: [from brief, Step 3]
- Turn: [from brief, Step 3]
- Close: [from brief, Step 3]

CRIT FINDINGS:
  [warnings from Step 4 -- carried as context for agents]

PRE-FLIGHT:
  Pulse: [pulse line from Step 5]
  Arch-ink: [structural findings from Step 5, if SEQUENCE -- or N/A]

INTENT ANCHOR: "[AP's restatement -- what the prose must accomplish, one sentence]"

DEALBREAKERS (must NOT do or lose):
- [inferred from input and brief, or USER INPUT NEEDED]

CONTEXT (if provided):
- POV: [character / unspecified]
- Tense: [past / present / unspecified]
- Prior events: [summary / none]
- World details: [relevant constraints]

AGENTS:
  Mode: [single / dual (--spark)]
  Agent A "Straight" -- baseline prose, /crit self-review.
  Agent B "Spark" -- challenger prose, /crit self-review. (if --spark)

CHALLENGER BRIEF (--spark only):
  - [user's directions, or USER INPUT NEEDED]
  -> If no directions and not --no-spark-gen: AP runs /spark-ink, presents results, user validates before proceeding.
```

### 2. Run /check

Invoke `/check` against the user's original prompt and all conversation context. Verify the contract captures everything the user asked for. If /check finds MISSED or PARTIAL items, fix them before presenting.

### 3. Handle Challenger Brief (--spark only)

If `--spark` mode is active and user has not provided challenger directions:
- If not `--no-spark-gen`: invoke `/spark-ink` on the input + brief + crit findings. Present 4+ provocations to user. User validates which sparks to include.
- If `--no-spark-gen`: mark challenger brief as USER INPUT NEEDED.

### 4. Present the Contract

Display the complete assembled contract.

```
[Complete contract from step 1]

---
GATE 0: [YES / ADJUST / CANCEL]
```

### 5. Handle User Response

- **YES:** Contract becomes the frozen **Forge Contract**. Proceed to Phase 1 (Craft) as defined in skill.md.
- **ADJUST:** User specifies what to change. AP modifies and re-presents. Return to step 4.
- **CANCEL:** Workflow ends. Display **`[FORGE -- OFF]`**.
- **Any other input:** Answer the user's question, then re-display the menu.

**NEVER launch agents without explicit YES.**

## Success/Failure Metrics

**Success:**
- All Step 1-5 outputs correctly assembled
- READER FEEL TARGET populated from Step 3 brief
- /check found no MISSED items (or they were fixed)
- Challenger brief validated if --spark mode
- User explicitly said YES
- Contract frozen -- no modifications after YES

**Failure:**
- Missing step outputs in the contract
- READER FEEL TARGET absent
- /check not run before presenting
- Launching agents before YES
- Modifying frozen contract after user approval
