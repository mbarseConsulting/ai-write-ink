# IA Patterns Rules — edit-ai-fr

> Scope: micro
> Loaded when: always
> Evaluates: AI-pattern survivors — mechanical artifacts that betray machine writing
> Preferred output: inline

---

## Finding Axes

### flag-words

- **Detects**: Blacklisted words and phrases characteristic of AI generation in French.
  - Word blacklist: "palpable", "tangible", "quelque chose dans [body part]", "un mélange de", "ne put s'empêcher de"
  - Metaphor blacklist: "danse" (des ombres/flammes), "symphonie", "tapisserie", "échiquier"
- **Works**: Every word is specific to the scene, the character, and the world. No off-the-shelf formulations.
- **Fails**: Blacklisted word appears. Each detection is a replacement opportunity.
- **Fix pattern**: Replace with a specific, contextual alternative anchored in the scene's physical reality and the character's perception.
- **Example**:
  > "Une tension palpable régnait dans la pièce."
  > → « palpable » — mot-drapeau IA, abstraction générique
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
  > "Sa gorge se serra." (3e occurrence en 4000 mots)
  > → Tic narratif — gorge serrée à fréquence anormale (1/1300 mots)
  > → Varier : trouver une réponse physique propre à ce personnage

### lexical-repetition

- **Detects**: Same word within 3 sentences (unless deliberate rhetorical device). Same sentence structure opening consecutive paragraphs. Same sentence starter pattern ("Il/Elle + verbe" chains).
- **Works**: Vocabulary varies. Sentence openings vary. Repetition, when present, is clearly a deliberate stylistic choice.
- **Fails**: Unconscious lexical echo. Structural monotony.
- **Fix pattern**: For lexical: synonym or restructure. For structural: vary the entry point.
- **Example**:
  > "Il traversa la cour. Il poussa la porte. Il monta l'escalier. Il entra dans la chambre."
  > → Chaîne « Il + verbe » — monotonie structurelle, signature machine
  > → Varier les attaques : subordonnée, complément en tête, fusion de phrases

### structural-patterns

- **Detects**: Formulaic paragraph structures surviving at abnormal rates. Lists of three, systematic parallelisms, mirror constructions, setup-elaboration-emotional_beat paragraph shapes.
- **Works**: Paragraph structures vary organically. No detectable formula repeating beyond what natural prose would produce.
- **Fails**: 5+ paragraphs following the same shape (setup → elaboration → emotional beat in final sentence). Systematic triads.
- **Fix pattern**: Flag with examples and count. The author restructures or requests rewrite guidance.
- **Example**:
  > 7 paragraphes sur 20 suivent le schéma « contexte → développement → émotion en fin de ¶ »
  > → Structure IA : schéma formulaire à 35% — seuil dépassé
  > → Varier les formes de paragraphes

### monotone-rhythm

- **Detects**: Sequences of same-length, same-structure sentences. 5+ consecutive sentences starting with subject-verb. 3+ consecutive paragraphs with identical rhythm.
- **Works**: Sentence length and structure vary naturally. No mechanical regularity detectable.
- **Fails**: "Il fit X. Il prit Y. Il alla Z. Il vit A. Il sentit B." Five subject-verb openers in sequence. Three paragraphs with identical sentence-count and rhythm.
- **Fix pattern**: Flag the sequence with start/end locations. Author restructures with varied attacks: subordinates, complements, nominal phrases.
- **Example**:
  > l.45-49 : « Il regarda... Il comprit... Il décida... Il se leva... Il sortit... »
  > → Rythme monotone : 5 phrases consécutives « Il + verbe » — signature machine
  > → Varier les attaques : subordonnées, compléments en tête, phrases nominales
