# AI Rules — qa-prose

> Scope: micro
> Loaded when: always
> Evaluates: AI-generated prose patterns — mechanical artifacts that betray machine writing
> Does NOT evaluate: writing craft failures (→ craft-rules), language quality (→ language-rules)
> Preferred output: inline

Diagnoses WHY prose sounds machine-generated and proposes rewrites.

---

## Finding Axes

### flag-words

- **Detects**: Blacklisted words and phrases characteristic of AI generation. Word list: "palpable", "tangible", "quelque chose dans [body part]", "un mélange de", "ne put s'empêcher de". Metaphor blacklist: "danse" (des ombres/flammes), "symphonie", "tapisserie", "échiquier".
- **Works**: Every word and image is specific to the scene, the character, and the world. No off-the-shelf formulations.
- **Fails**: Blacklisted word or phrase appears. Each detection is a replacement opportunity.
- **Fix pattern**: Replace with a specific, contextual alternative anchored in the scene's physical reality and the character's perception.
- **Example**:
  > "Une tension palpable régnait dans la pièce."
  > → "palpable" — mot-drapeau IA, abstraction générique
  > → Montrer la tension par un détail concret : un geste, un silence, un objet

### ai-structures

- **Detects**: Lists of three (adjectives, actions, sensations). Systematic parallelisms. Constant emotional crescendo (every paragraph ending on intensity). Mirror constructions. Formulaic paragraph shapes: setup-elaboration-emotional_beat.
- **Works**: Sentence structures vary organically. Paragraphs have different shapes. Emotional beats land at irregular intervals dictated by content, not formula.
- **Fails**: Three consecutive adjectives. Three parallel actions. Every paragraph builds to an emotional climax in the final sentence. Mechanical symmetry.
- **Fix pattern**: Break the pattern — vary structure, move the beat, cut one element from the triad, asymmetrize.
- **Example**:
  > "Il sentit la peur, la rage et le désespoir monter en lui."
  > → Triade émotionnelle — structure IA typique (liste de trois)
  > → Garder une seule émotion, la rendre physique et spécifique

### ai-tics

- **Detects**: Narrative tics at abnormal frequency: jaw clenching, throat tightening, breath catching, heart hammering, stomach knotting, fists clenching. Frequency cap: max 1 per 2000 words for any given tic.
- **Works**: Physical responses are varied, specific to the character, and earned by the scene. No two emotional beats use the same somatic shortcut.
- **Fails**: Same physical response appears multiple times across scenes. Above frequency cap = pattern, not craft.
- **Fix pattern**: Replace repeated tic with a physical response specific to THIS character's body and THIS scene's context.
- **Example**:
  > "Sa gorge se serra." (3rd occurrence in 4000 words)
  > → Tic narratif — gorge serrée à fréquence anormale (1/1300 mots)
  > → Varier : trouver une réponse physique propre à ce personnage

### repetition

- **Detects**: Same word within 3 sentences (unless deliberate rhetorical device). Same sentence structure opening consecutive paragraphs. Same gesture used for different emotions. Same sentence starter pattern ("Il/Elle + verbe" chains). Repeated emotional beats within a scene.
- **Works**: Vocabulary varies. Sentence openings vary. Each gesture carries a unique emotional signature. Repetition, when present, is clearly a deliberate stylistic choice.
- **Fails**: Unconscious lexical echo. Structural monotony. A shrug means surprise in paragraph 2 and sadness in paragraph 7.
- **Fix pattern**: For lexical: synonym or restructure. For structural: vary the entry point. For gestural: assign unique physical vocabulary per emotion.
- **Example**:
  > "Il traversa la cour. Il poussa la porte. Il monta l'escalier. Il entra dans la chambre."
  > → Chaîne "Il + verbe" — monotonie structurelle, signature machine
  > → Varier les attaques : subordonnée, complément en tête, fusion de phrases

### forbidden-locutions

- **Detects**: Anglicisms ("réaliser" for "se rendre compte", "définitivement" for "assurément"). Bureaucratic turns ("au niveau de", "en termes de", "il est à noter"). Verbal filler ("en fait", "du coup" in narration). Academic hedging in fiction ("semblait", "paraissait" overuse).
- **Works**: French prose uses native constructions. No English logic underneath. No administrative register leaking into narration. Hedging is a character choice, not a narrator habit.
- **Fails**: A construction reveals English-source thinking or administrative register. "Réaliser" used as a calque of "to realize." "Du coup" appears in narration (acceptable in dialogue).
- **Fix pattern**: Replace with native French equivalent. If hedging: decide — does the narrator know, or doesn't they? Commit.
- **Example**:
  > "Elle réalisa qu'il ne reviendrait pas."
  > → Anglicisme — "réaliser" calque de "to realize"
  > → "Elle comprit" / "Elle se rendit compte" / "L'évidence la frappa"
