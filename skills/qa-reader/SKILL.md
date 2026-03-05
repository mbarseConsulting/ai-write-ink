---
name: qa-reader
description: "Use when: (1) evaluating reading experience — hooks, pacing, tension, engagement, (2) assessing opening or closing chapters (bookends mode), (3) diagnosing why prose bores or captivates"
---

**`[QA-READER]`** — Display this immediately.

## LOAD AGENT

Read `skills/qa-reader/agents/agent-qa-reader.md` — you ARE this persona.

**Option — `-c` / `--context`:** Use the `Agent` tool with `subagent_type: "agent-qa-reader"`. Agent works in its own context.

## OPTIONS

### Default (no flag)

Use the agent persona alone. Output follows the agent's own OUTPUT section (emoji blocks, triage, verdict). No rules files loaded. No report template.

### Report (`--report` or user asks for full diagnostic/assessment)

Activates full diagnostic mode. Loads references and report template.

## REFERENCES

**Loaded in `--report` mode only.**

| Input                                     | Rules loaded                                                  |
| ----------------------------------------- | ------------------------------------------------------------- |
| Excerpt / passage                         | `micro-rules`                                                 |
| Complete scene                            | `micro-rules` `scene-rules`                                   |
| Complete chapter                          | `micro-rules` `scene-rules` `chapter-rules`                   |
| Multiple chapters / manuscript            | `micro-rules` `scene-rules` `chapter-rules` `macro-rules`     |
| Opening (ch.1 or user says "opening")     | `micro-rules` `opening-rules`                                 |
| Closing (last ch. or user says "closing") | `micro-rules` `closing-rules`                                 |
| Both opening + closing                    | `micro-rules` `opening-rules` `closing-rules` `promise-rules` |

Rules path: `skills/qa-reader/references/qa-reader-{name}-rules.md`

**Report format:** `skills/qa-reader/references/qa-reader-report.md`

**Output MUST follow the report template.** This is non-negotiable.

**Rules:**

- Never load bookends rules in standard mode. Never load standard meso/macro in bookends mode.
- Never load macro for a single scene or chapter.
- Micro is always loaded.
- When in doubt about scope, ask. Don't guess.

## OUTPUT

| Input                    | Default format |
| ------------------------ | -------------- |
| Standard mode, any scope | Diagnostic     |
| Bookends mode            | Assessment     |
| User says "inline"       | Inline         |
