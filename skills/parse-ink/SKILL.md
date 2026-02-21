---
name: parse
description: "Load before writing any content derived from a user prompt into a file. Forces intent analysis and reformulation — never verbatim paste."
---

# parse-ink

**`[PARSE MODE — ON]`** — Display this immediately.

## Rules

These rules OVERRIDE your writing behavior until the user confirms or the conversation ends.

### The Prohibition

**NEVER write raw prompt text verbatim into a file.**

"Verbatim" includes: sentences the user already said, slightly reworded. If the user's original words are still recognizable → it's verbatim. Reformulate.

No exception for "it already sounds like a rule". No exception for "it's clear enough". No exception.

### Mandatory Pre-Write Analysis

Before writing anything to a file, answer these three questions OUT LOUD:

1. **Intent** — What is the user actually asking for? Not what they said — what they MEANT. State it in one sentence that doesn't use the user's words.
2. **Format** — What type of content does the target file expect? (behavioral rule / persona constraint / output spec / structural template / reference material)
3. **Gap** — What is missing or ambiguous in the raw prompt that would cause a failure if written as-is?

If you cannot answer all three → ask. Do not write.

### Reformulation Protocol

1. Answer the three questions above
2. Write the reformulated version
3. Show it to the user BEFORE writing to file
4. Wait for confirmation

**NEVER write to a file without showing the reformulation first.**

### Reformulation Test

Before writing, ask:

- Could this text have been produced by someone who copy-pasted without understanding? If yes → reformulate.
- Does this sentence use words the user already said, in the same order? If yes → reformulate.
- Does this text FUNCTION correctly in its target context — would an agent with no prior conversation produce the intended behavior from this text alone? If unclear → reformulate or ask.

### What Good Reformulation Looks Like

Raw: "make the agent always be harsh"
→ Intent: enforce critical stance unconditionally
→ Format: behavioral rule
→ Reformulation: `Your first response to any input is a challenge, objection, or critique. Agreement is forbidden without prior pushback.`

Raw: "the agent should know a lot about structure"
→ Intent: constrain the agent to structural analysis tasks
→ Format: FOCUS section, not persona trait
→ Reformulation: `[FOCUS] Operates exclusively at structural level — acts, arcs, turning points, throughlines. Does not engage with prose quality, character psychology, or line-level craft.`

Raw: "add that the agent speaks French"
→ Intent: set language output constraint
→ Format: operational rule, not persona
→ Reformulation: `**Language:** French. All output in French regardless of input language.`

## Deactivation

User says "ok", "go", "écris", "c'est bon" → write the file. Confirm with **`[PARSE MODE — OFF]`**.
