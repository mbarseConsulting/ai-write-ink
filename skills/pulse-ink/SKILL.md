---
name: pulse-ink
description: "Use when: (1) quick diagnostic on fiction prose — engagement and originality in one pass, (2) flagging stock patterns and engagement drops before deep QA, (3) spammable triage on any scene or chapter draft"
---

## BEHAVIOR

Scan in thirds — beginning, middle, end. For each third: flag problems and mark what's strong. Then sort all findings by severity (worst-first). The output is a triage, not a walkthrough. No report, no preamble, no summary.

### Scan priorities (in order)

1. **Stock** — trope/scene/image executed without new texture. Always 🔴. Name the trope or source.
2. **Engagement drop** — where a reader skims, stops caring, or puts the book down.
3. **Craft failure** — showing-vs-telling, dead dialogue, broken pacing, passive POV.

### Detection tags

| Tag | Detects | Sev |
|-----|---------|-----|
| `stock` | Trope, stock scene, or dead metaphor used without fresh treatment. Name it. | always 🔴 |
| `drop` | Engagement dies — no tension, no question, no pull. Reader leaves. | 🟠 or 🟡 |
| `flat` | Dialogue without subtext, or all characters same voice. | 🟡 |
| `told` | Named emotion, or show-then-tell double tap that kills the effect. | 🟡 |
| `pace` | Consecutive beats at same intensity, or narrative time vs importance mismatch. | 🟡 |
| `drift` | POV passivity, psychic distance break, weak hook, or scene without arc. | 🟡 |
| `fresh` | Passage that works and must be protected during revision. Name why. | 🟢 |

### What you skip

No fix suggestions. No creative directions. No axis breakdowns.

## OUTPUT

One line per finding. No exceptions.

```
🔴 [tag — location] « quoted passage » — what the reader experiences
🟠 [tag — location] « quoted passage » — what the reader experiences
🟡 [tag — location] « quoted passage » — what the reader experiences
🟢 [fresh — location] « quoted passage » — why it works, don't touch
```

- **Severity:** 🔴 = stock or engagement death. 🟠 = engagement dropped. 🟡 = mechanical misfire. 🟢 = protect this.
- **Location**: scene or paragraph — enough to find the passage.
- **Quote**: shortest excerpt proving the finding. Max ~15 words.
- **Why**: one clause. What the reader experiences (problems) or why it's strong (greens).
- **Ordering**: 🔴 before 🟠 before 🟡. 🟢 at the end, grouped.

End with: `[pulse: X🔴 Y🟠 Z🟡 | W🟢]`

Nothing after the pulse line.

**Diffability:** Same text produces same findings in same order. Run on v1 and v2 — diff the outputs. Vanished lines = fixed. New lines = regressions.

### Hard limits

- Max 25 lines total for ~3 pages of text. Fewer is better.
- If two problems overlap on one passage, keep the higher-severity tag.
- When cutting to stay under 25 lines: drop 🟡 first, then 🟠. Never drop a 🔴.

## SCOPE

No setup. No reference files. Run on whatever text follows the command.

**Long text (>1000 words):** Use /steps to process the text in segments before producing findings. This prevents skipping passages in dense prose.

If text exceeds ~15 pages: "Text exceeds pulse-ink scope. Run on a section, or use /qa-reader + /qa-originality for full manuscript."

## ACTIVATION - DEACTIVATION - HANDOFF

**`[PULSE]`** — Display immediately. Then scan.

**Applies to this response only. Auto-resets after.**
