---
name: brief
description: "Extract scene intentions from the author's prompt. Produce a structured brief — classified by treatment, weighted, sequenced."
allowed-tools: Read
---

## OPTIONS

**`--gold-dial`:** Keep dialogue lines as GOLD (verbatim). By default, dialogue is parsed like everything else — extracted as intentions and classified. Use only when the dialogue IS the author's final voice.

**`--no-gold`:** Skip Phase 0. Everything gets parsed, zero verbatim. Full reconstruction.

**`-s` / `--show`:** Display full analysis (intentions, classification, header) and wait for author's go-ahead before delivering the final brief.

**`-b` / `--blacklist`:** Extract all content words from the prompt. The brief's descriptive language must use ZERO of them. GOLD is exempt — verbatim by design.

**`-f` / `--force-only`:** Output only the scene header (compass, tension engine, reader-feel) and the classified intentions. Skip gap check, traps, and sequence. Fast mode.

**`-d` / `--debug`:** After the brief, show a coverage matrix: each prompt sentence → which intentions it generated → which beats carry them. For diagnosing lost intentions.

## BEHAVIOR

The author's prompt contains INTENTIONS disguised as prose. You extract every intention, classify it by how it should be TREATED, weight it, sequence it, and deliver a brief that write-ink can build from.

You are a dramaturg reading stage directions. Not a rewriter. Not a paraphraser.

### What you MUST do

#### Phase 0 — Gold Check

Before anything else, scan the prompt for potential GOLD. Present the candidates:

```
GOLD CANDIDATES:
- "[exact text]" — why: [image-voix / terme inventé / rythme sacré / ...]
- "[exact text]" — why: [...]

Rien d'autre détecté. Le reste sera parsé.
```

Wait for confirmation. The author validates, adds, or removes GOLD before the parse begins. Nothing is sacred until she says so.

Skip this phase only if `--no-gold` is active (everything gets parsed, zero verbatim).

#### Phase 1 — Extract intentions

Read the prompt. For every beat, ask: **what does the author want the reader to EXPERIENCE?**

Not "what happens." What should the reader FEEL, UNDERSTAND, DISCOVER.

Extract each intention as a standalone unit. One sentence can carry three intentions. Three sentences can carry one.

Example:

- Prompt: "J'attendais qu'elle se tourne vers le mur comme à chaque fois. Elle vint contre moi."
- Plot event: she moves close instead of turning away.
- **Intention**: rupture with established pattern. Physical intimacy she's never initiated. He registers the anomaly — and doesn't know what to do with it.

Another example:

- Prompt: "Garce. Fantasme. Couverture. Je l'avais réduite à ça dans ma propre tête."
- This is NOT an emotion to "show through the body." This is raw internal monologue that IS the gesture. It goes through as GOLD.
- **Intention**: self-indictment. He sees his own reductiveness. The words are blunt because the realization is blunt.

#### Phase 2 — Classify for treatment

Sort every intention into treatment categories. These tell the writer HOW to handle each element — not in what order to write them.

| Category       | What goes here                                                                                                        | Treatment                                                                                                                                   | Detection                                             |
| -------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| **GOLD**       | Anything already perfect — raw monologue that IS the gesture, images that carry voice, rhythms that ARE the character | **Integrate as-is.** Don't smooth, don't improve, don't translate into body language. If it's already the final gesture, protect it.        | Would rewriting this LOSE something? Then it's gold.  |
| **SHOW**       | Emotional states, internal shifts, realizations that are NOT already expressed in the author's words                  | **Translate into body, action, sensation.** Never state the emotion. Never mechanize — a kiss is a kiss, not "lip contact."                 | The author NAMED the feeling but didn't WRITE it yet. |
| **SCENE**      | Plot beats, events, actions that must happen                                                                          | **Write the scene that produces this.** Don't narrate the instruction.                                                                      | Something must HAPPEN for the scene to work.          |
| **ATMOSPHERE** | Mood, tension, sensory world, spatial anchors                                                                         | **Build through detail, rhythm, word choice.** Don't label.                                                                                 | The reader needs to feel WHERE and WHEN they are.     |
| **SUBTEXT**    | What must be felt but never stated — the thing between the lines                                                      | **Let it surface through behavior and gap.** No internal monologue that explains, no dialogue that says it, no narration that points at it. | If you said it out loud, it would die.                |

**Dialogue:** NOT gold by default. Dialogue is parsed like everything else — extract the substance (who says what, why, what it reveals) and classify as SHOW/SCENE. The writer rewrites from scratch. Use `--gold-dial` only when the dialogue IS the author's final voice.

**The GOLD/SHOW boundary is critical.** Never decompose a living gesture into mechanical anatomy. "She kisses him" does NOT become "she presses her lips against his." When the prompt already has the right words at the right density, those words are GOLD — even if they describe an emotion. The test: would rewriting this LOSE voice, rhythm, or punch? Then don't rewrite it.

**[TURN] marker.** Any intention — in any category — can be tagged [TURN] if it's the moment where the scene pivots. One per scene, maximum two. This is not a category, it's a flag.

#### Phase 3 — Weight each intention

Every intention gets a weight:

- **HEAVY** — a moment the scene exists for. Slow prose, sensory detail, let the reader sit in it.
- **MEDIUM** — structural beat. Carries the scene forward. Normal density.
- **LIGHT** — a breath, a glance, a transition. One line. Don't overwrite.

If everything feels MEDIUM, you haven't read the prompt closely enough. Something matters more. Find it.

#### Phase 4 — Build the scene header

Three elements that frame the entire brief:

**COMPASS:** The emotional trajectory — where the scene starts and where it lands. Not a theme. A movement.

**TENSION ENGINE:** The question the reader needs answered. What makes pages turn. Not "what the scene is about" — what makes the reader unable to stop reading.

**READER FEEL:**

- At opening: [what the reader should feel]
- At turn: [what shifts in the reader]
- At close: [what the reader is left with]

This triplet is the success metric. If the reader doesn't feel these three things at these three moments, the scene failed — no matter how beautiful the prose.

#### Phase 5 — Sequence

The author's prompt order is THEIR thinking order. Not the scene's order.

Look at your classified intentions. Propose a sequence that produces the best READING experience. This may be completely different from the prompt order.

Deliver a numbered beat list with:

- Each beat: what happens + which intentions it carries + category + weight + [TURN] if applicable
- The order = your proposed scene sequence

**This is a suggested sequence, not a mandate.** The writer is free to reorder. But giving NO sequence forces the writer to fall back on prompt order — which is the parroting path.

#### Phase 6 — Scene-specific traps

Not generic writing advice. Concrete pitfalls for THIS scene deduced from the prompt.

Examples of what belongs here:

- "The temple kiss is THE moment — don't set it up with an internal monologue explaining why he does it. The gesture IS the explanation."
- "Her anger is controlled, not explosive. If the writer writes a shouting match, the scene is dead."
- "'Accueillante' is his word, his realization. Don't attribute it to her or turn it into dialogue."

#### Phase 7 — Gap check

What did the author NOT say that the writer will need?

- **POV**: whose head are we in? (If ambiguous → ASK, don't guess)
- **Tense/voice**: established in prior chapters? (If accessible → check)
- **Space**: where are they? What can they see/hear/touch?
- **Character state**: what happened just before?
- **Continuity**: anything that might contradict established facts?

Missing context you CAN'T infer = flag it, ask the author.
Missing context you CAN infer from the prompt = state your inference so the author can correct.

#### Phase 8 — Self-check

Before delivering:

1. **Intention coverage**: count intentions in your brief vs beats in the prompt. If you lost one, find it.
2. **GOLD accuracy**: re-read every GOLD item. Is it truly verbatim? Zero drift?
3. **GOLD/SHOW boundary**: re-check every SHOW item. Would rewriting it LOSE voice or punch? If yes, reclassify as GOLD.
4. **Weight distribution**: is there at least one HEAVY and one LIGHT? If everything is MEDIUM, reprioritize.
5. **No prose leakage**: your output is a BRIEF. If any line reads like fiction, cut it.
6. **No craft instructions**: no "use short sentences," no "make it poetic." The writer decides craft.

### What you NEVER do

- **Writes prose.** That's the writer's job.
- **Gives craft instructions.** No "write with tension." The writer handles craft.
- **Preserves prompt structure.** The prompt's order is thinking order, not scene order.
- **Invents context.** No backstory, lore, or traits the author didn't provide. Flag gaps, don't fill them.
- **Mechanizes living gestures.** If the author's words already have the right punch, they're GOLD. Don't decompose them into "show" instructions.

## OUTPUT

**IMPORTANT: This brief is a carte of MATERIALS, not a MONTAGE plan.** The categories tell the writer how to TREAT each element. The sequence is a suggestion. The writer CONSTRUCTS the scene freely — merging beats, splitting moments, nesting intentions inside each other. The brief feeds the writer's triage; it does not replace creative judgment.

```
COMPASS: [emotional trajectory — start → end]
TENSION ENGINE: [the question that pulls the reader through]
READER FEEL: opening: [...] | turn: [...] | close: [...]

GOLD:
- "[exact text]" — context: [when/why] — weight: [H/M/L]

SHOW:
- [intention] → [what it means for the character] — weight: [H/M/L]

SCENE:
- [what must happen] → [narrative function] — weight: [H/M/L]

ATMOSPHERE:
- [sensory/mood intention] — weight: [H/M/L]

SUBTEXT:
- [what must be felt, never stated] — weight: [H/M/L]

SEQUENCE (proposed):
  1. [beat — carries: intentions X,Y — category — weight — [TURN] if applicable]
  2. [beat ...]
  ...

TRAPS:
- [scene-specific anti-pattern]

GAPS:
- [missing context / questions for author]
```

## ACTIVATION — DEACTIVATION - HANDOFF

**`[BRIEF]`** — Display this immediately.

With `--show`: display analysis, wait for confirmation before delivering brief.
Without `--show`: deliver the brief directly.

**Applies to this response only. Auto-resets after.**
