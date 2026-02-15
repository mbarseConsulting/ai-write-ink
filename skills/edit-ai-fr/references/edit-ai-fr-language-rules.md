# French Language Rules — edit-ai-fr

> Scope: micro
> Loaded when: always
> Evaluates: French language quality for literary fiction — grammar as craft, constructions as voice
> Preferred output: inline

---

## Finding Axes

### tense-discipline

- **Detects**: Accidental tense slips in narration. Passé composé where passé simple is expected. Unmotivated tense shifts within a paragraph. Plus-que-parfait misuse in backstory passages.
- **Works**: Passé simple for narrative action, imparfait for description and habitual. Plus-que-parfait for established backstory. Every tense shift is intentional and motivated by temporal logic.
- **Fails**: The narrator slips into passé composé mid-narration. A paragraph mixes passé simple and imparfait without temporal justification. Backstory uses passé simple instead of plus-que-parfait.
- **Fix pattern**: Identify the temporal layer (action / description / backstory) and apply the correct tense. If the shift is intentional, ensure the transition is marked.
- **Example**:
  > "Il traversa la cour. Le soleil a brillé sur les pierres."
  > → Glissement passé simple → passé composé en narration
  > → "Le soleil brillait sur les pierres" (imparfait descriptif)

### syntax-naturalness

- **Detects**: Sentence rhythm that sounds translated. Relative clauses stacking three deep. Word order that follows English emphasis patterns instead of French. Important information buried mid-sentence instead of landing at the end (French focus position).
- **Works**: French sentence rhythm: nominal phrases, inversions where natural, relative clauses that don't stack. Word order serves emphasis — the important word lands at the end.
- **Fails**: A sentence is grammatically correct but sounds wrong to a native ear. English word order transposed into French syntax. The sentence peak is in the middle, not at the end.
- **Fix pattern**: Restructure to place the key information at the end of the sentence. Break stacked relatives. Use French-native constructions (detached complements, inversion, nominal phrases).
- **Example**:
  > "C'était la raison pour laquelle la femme qui vivait dans la maison qui se trouvait au bout de la rue avait décidé de partir."
  > → Relatives empilées — syntaxe lourde, rythme non-français
  > → Découper : phrases courtes, complément détaché, information en fin de phrase

### forbidden-locutions

- **Detects**: Anglicisms ("réaliser" for "se rendre compte", "définitivement" for "assurément"). Bureaucratic turns ("au niveau de", "en termes de", "il est à noter"). Verbal filler ("en fait", "du coup" in narration). Academic hedging in fiction ("semblait", "paraissait" overuse).
- **Works**: French prose uses native constructions. No English logic underneath. No administrative register leaking into narration. Hedging is a character choice, not a narrator habit.
- **Fails**: A construction reveals English-source thinking or administrative register. "Réaliser" used as a calque of "to realize." "Du coup" appears in narration (acceptable in dialogue).
- **Fix pattern**: Replace with native French equivalent. If hedging: decide — does the narrator know, or doesn't they? Commit.
- **Example**:
  > "Elle réalisa qu'il ne reviendrait pas."
  > → Anglicisme — « réaliser » calque de « to realize »
  > → "Elle comprit" / "Elle se rendit compte" / "L'évidence la frappa"

### translation-artifacts

- **Detects**: Constructions that reveal English-source thinking: possessives instead of articles for body parts ("ses yeux" vs "les yeux"), progressive forms ("était en train de" overuse), English idiom calques, preposition choices that follow English logic, passive constructions where French uses active or pronominal.
- **Works**: French syntax follows French logic. Body parts use articles. Pronominal forms are preferred over passive. Idioms are native, not calqued.
- **Fails**: "Elle leva ses yeux" instead of "Elle leva les yeux." "Il était en train de marcher" instead of "Il marchait." "Il a été surpris par" instead of "Il s'est étonné de."
- **Fix pattern**: Identify the English construction underneath. Replace with the native French equivalent. If unsure, test: would a monolingual French speaker write it this way?
- **Example**:
  > "Elle ferma ses yeux et prit une profonde respiration."
  > → Double calque anglais : possessif + "prendre une respiration"
  > → "Elle ferma les yeux et inspira profondément."

### dialogue-format

- **Detects**: Incorrect or inconsistent French dialogue formatting. Missing tirets cadratins. Incises reduced to "dit-il" without action beats. Unnecessary dialogue tags when the speaker is obvious. Info dumps disguised as conversation.
- **Works**: French dialogue conventions respected: tirets cadratins, incises with action beats that reveal character, tags only when necessary for clarity. Dialogue sounds like speech, not exposition.
- **Fails**: Guillemets instead of tirets. Every line tagged with "dit-il/dit-elle." Two characters in a scene and every line still tagged. A character explains backstory to someone who already knows it.
- **Fix pattern**: Fix formatting to French conventions. Replace bare tags with action beats. Remove unnecessary tags. Flag "as you know" dialogue for author decision.
- **Example**:
  > "Je sais," dit-il. "C'est pour ça que je suis venu," dit-il.
  > → Double tag inutile — le locuteur est évident
  > → Remplacer le second tag par un action beat ou supprimer
