# Micro Rules — qa-originality

> Scope: micro
> Loaded when: always
> Evaluates: Sentence and paragraph level freshness — formulation, images, word choices
> Preferred output: inline

---

## Finding Axes

### formulation-freshness

- **States**: fresh / mixed / stock
  - **fresh**: Every image is scene-specific and character-anchored. No metaphor belongs to another novel.
  - **mixed**: Some formulations are world-anchored; others fall back on generic images.
  - **stock**: Off-the-shelf metaphors throughout. Images that belong to every novel and no novel.
- **Detects**: Stock metaphors, generic images, off-the-shelf formulations. Also detects fresh, world-anchored images.
- **Fix pattern**: "What would THIS character compare it to, given THEIR job, obsessions, sensory world?" Rewrite one image. 10 min.
- **Genealogy trigger**: On stock finding, name 2-3 novels with same image and 1 that found a different angle.
- **Example**:
  > "Le temps s'arreta. Le monde autour d'elle cessa d'exister."
  > Lineage: frozen-time image as Musso, Levy, every romance since the 1990s.
  > Swerve: Ernaux, *Les Annees* — time compresses into an inventory of objects.
  > Direction: anchor in THIS character's perception — what specifically changes in their sensory field?

### linguistic-audacity

- **States**: daring / uneven / safe
  - **daring**: Departures from convention that create effects no standard construction could. Neologisms that capture, broken rules that serve meaning.
  - **uneven**: Occasional risks land; the rest defaults to convention.
  - **safe**: Correct but timid throughout. No surprises in word choice or structure.
- **Detects**: Stylistic risk-taking — neologisms, broken rules, unexpected word choices, inventive constructions.
- **Fix pattern**: Pick ONE sentence where standard syntax falls short. Break exactly that rule in service of the effect. 10 min.
- **Example**:
  > "Elle ressentit une grande tristesse." Conventionnel, sans risque.
  > Direction: find the linguistic move that performs the emotion instead of naming it.

---

## Verdict Axis

### voice-singularity

- **Assesses**: Whether the prose bears a specific authorial fingerprint at the paragraph level.
- **States**: distinctive (unmistakable — remove the byline and you know who wrote it; specific rhythm, lexical field, perceptual angle) / emerging (flashes of singularity between generic scaffolding; voice exists but inconsistent) / competent (fluent, professional, no personality; could belong to any author in genre) / generic (default prose, no authorial choice visible)
- **Gating rule**: CANNOT score "distinctive" if formulation-freshness is "stock". Cap at "emerging."
- **Suggestion pattern**:
  - emerging: Quote 2-3 passages where voice breaks through. Identify shared pattern. Apply to 5 flat paragraphs. 10 min each.
  - competent: Find one passage with specific perception — the voice seed. Rewrite 3 flat paragraphs through same lens. 10 min each.
  - generic: Cross out every image another author could have written. What's left is the voice. If nothing, write one paragraph using only THIS character's sensory world. 10 min.
