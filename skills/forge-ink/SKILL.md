---
name: forge-ink
description: "Use when: (1) producing the best possible prose from a prompt through competitive crafting, (2) user wants two independent prose versions evaluated by QA pipeline, (3) user says 'forge' or wants structured prose production with diagnostic loop"
effort: max
---

**`[FORGE]`** -- Display immediately.

## OPTIONS

| Flag             | Effect                                                        |
| ---------------- | ------------------------------------------------------------- |
| `--dry`          | Phase 0 only -- cadrage + pre-flight, no craft                |
| `--spark`        | Enable Agent B (dual mode with challenger)                    |
| `--scene`        | Force SCENE scope                                             |
| `--chapter`      | Force CHAPTER scope                                           |
| `--sequence`     | Force SEQUENCE scope                                          |
| `--no-spark-gen` | With --spark: skip /spark-ink generation, user provides brief |

## ROUND MAP

| Phase     | Name            | Actor                | Rounds           |
| --------- | --------------- | -------------------- | ---------------- |
| 0         | Cadrage         | AP + User            | 6 steps          |
| 1         | Craft           | 1 or 2 AC (parallel) | 1 each           |
| 2         | Evaluation Loop | AP + User            | user-driven      |
| 3         | Verdict         | AP + User            | 1                |
| **Total** |                 |                      | **~9-12 rounds** |

Default: single agent. With `--spark`: dual agent.

## AGENTS

- **AP:** Read `agents/agent-judge-forge.md` -- you ARE this persona. Agent files are authoritative for agent behavior -- skill.md defines the workflow, agent files define how each role executes within it.
- **Agent A "Straight":** `agents/agent-straight-forge.md` -- baseline prose writer, always active.
- **Agent B "Spark":** `agents/agent-spark-forge.md` -- challenger prose writer, `--spark` only.

## OUTPUT

### Chain Decision format (Phase 1, each agent)

```
CHAIN DECISION:
- /outline-ink --script: [YES -- 5 beats identified / NO -- single continuous moment, reason]
- /dialog-ink: [YES -- 40% dialogue weight / NO -- interior monologue, reason]
- /write-ink: [always]
```

### Forge Report format (Phase 2)

```
## Forge Report

### [Agent name] -- [output path]
**Pulse:** [pulse line]
**Intent alignment:** [YES / PARTIAL / NO]

[Selected QA findings -- severity-sorted]

Summary: [2 sentences -- what works, what fails]
```

Dual mode: repeat the agent block per agent, then append:

```
### Comparison
| Axis | Agent A | Agent B | Edge |
|------|---------|---------|------|
| [per QA skill run] | [finding] | [finding] | [A/B/tie] |
```

### Forge CR format (Phase 3, dual mode only, max 25 lines)

```
## Forge CR

**Intent:** [1 sentence]
**Scope:** [SCENE / CHAPTER / SEQUENCE]
**Genre:** [calibrated]

**Recommendation:** [A / B / neither] -- [why, citing QA evidence]

**Agent A "Straight":**
- Strengths: [2-3 items with QA citations]
- Weaknesses: [2-3 items with QA citations]

**Agent B "Spark":** (if --spark)
- Strengths: [2-3 items with QA citations]
- Weaknesses: [2-3 items with QA citations]

**Sparks landed:** [which challenger directions produced quality]
**Sparks missed:** [which didn't, why]

**Gaps remaining:** [what's still missing]
```

---

## Phase 0 -- Cadrage

**MANDATORY. Do not launch agents before GATE 0.**

Phase 0 runs six steps in sequence. Each step has its own file in `steps/`. AP reads and executes each step file in order. Never skip a step or merge steps -- each exists because it produces a distinct artifact that downstream steps depend on.

1. `steps/step-01-genre.md` -- Genre calibration
2. `steps/step-02-scope.md` -- Scope detection + ink chain derivation
3. `steps/step-03-brief.md` -- Intent extraction via /brief-ink
4. `steps/step-04-crit.md` -- Critical challenge of the brief
5. `steps/step-05-preflight.md` -- Pre-flight diagnostic (/pulse-ink, /arch-ink)
6. `steps/step-06-contract.md` -- Forge Contract assembly + GATE 0

Each step halts for user validation before advancing. If `--dry`, stop after step 6 (present contract but do not launch agents).

**GATE 0:** User says YES at step 6 -> the contract becomes the frozen **Forge Contract**. Proceed to Phase 1.

**NEVER launch without explicit "yes."**

---

## Phase 1 -- Craft

**Agent(s) launched. AP on standby.**

### Agent craft process

Agents receive the Forge Contract, which contains the validated brief from step 3. Agents do NOT re-run /brief-ink. They use the validated brief as input and execute the remaining ink chain.

### Dispatch

**Single agent (default):**

Use the `Agent` tool with `subagent_type: "agent-straight-forge"`.
**prompt**: Forge Contract (includes validated brief, genre, scope, ink chain, crit findings, pre-flight results), the original input, output path `local/forge/straight/draft.md`.

**Dual agent (`--spark`):**

Also use the `Agent` tool with `subagent_type: "agent-spark-forge"`.
**prompt**: Forge Contract (same as above), the original input, challenger brief, output path `local/forge/spark/draft.md`.

Launch both in parallel (two `Agent` tool calls in a single message).

**No visibility between agents.**

Agents state their Chain Decision (see OUTPUT format) before executing the chain. This evaluates pertinence of /outline-ink and /dialog-ink for the material.

**GATE 1:** Draft(s) delivered -> Phase 2.

---

## Phase 2 -- Evaluation Loop

**User-driven. AP runs what user asks. Loop until user says DONE.**

### 2a. Draft delivery

AP presents the draft(s) and asks:

```
Draft(s) delivered to [paths].
What diagnostic do you want to run?
[pulse-ink (triage: stock patterns, engagement drops) / qa-prose (sentence craft: POV, show-tell, dialogue) / qa-reader (reading experience: hooks, pacing, tension) / qa-originality (creative singularity: voice, cliches, freshness) / all / skip to verdict]
```

### 2b. Diagnostic

User picks. AP runs selected QA skill(s) on draft(s). AP presents results using the Forge Report format.

**QA contradiction resolution:** See agent-judge-forge.md (authoritative).

### 2c. User decision

```
[REWORK -- send findings to agent for rewrite]
[ANOTHER QA -- run a different diagnostic]
[DONE -- proceed to verdict]
```

**REWORK:** AP sends QA findings to the agent via `SendMessage` (using agent name). Agent rewrites to `local/forge/[agent-name]/draft-rN.md` (r1, r2, r3...). Loop restarts at 2a.

**ANOTHER QA:** User picks a different diagnostic. AP runs it. Loop restarts at 2b.

**DONE:** Proceed to Phase 3.

**No system-imposed limit on iterations.** User loops as long as they want.

In dual mode: same loop for both drafts. User can REWORK one or both agents.

---

## Phase 3 -- Verdict & Finalization

### Single agent mode

1. Invoke `/check` against original prompt -- verify intent served.
2. Present final draft with summary of QA findings across all iterations.
3. User accepts or requests one more pass.
4. Write to `[target]_forge.md` or `local/forge/final.md`.

### Dual agent mode

1. Invoke `/check` against original prompt for both drafts.
2. Side-by-side comparison:
   ```
   | Axis | Agent A | Agent B | Edge |
   |------|---------|---------|------|
   | [per QA result from Phase 2] | [finding] | [finding] | [A/B/tie] |
   ```
3. Present the Forge CR (see OUTPUT format).
4. User choice. AP recommends, user decides:
   - **Pick A** -> write to `[target]_forge.md`
   - **Pick B** -> write to `[target]_forge.md`
   - **Cherry-pick** -> user specifies passages from each -> AP assembles -> `[target]_forge.md`
   - **Neither** -> user decides: adjust contract and relaunch, or stop

**Never overwrite the original input.** The `_forge` suffix allows comparison and rollback.

Write final deliverable. Confirm with **`[FORGE -- OFF]`**.

## ACTIVATION - DEACTIVATION - HANDOFF

Persistent mode. Stays active through all phases.

User says "stop", "abort", "kill forge" -> shut down all agents, clean up, **`[FORGE -- OFF]`**.
