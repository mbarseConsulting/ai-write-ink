# Language Rules — qa-prose

> Scope: micro
> Loaded when: always
> Evaluates: French language quality for literary fiction — grammar as craft, not as rule-following
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

### translation-artifacts

- **Detects**: Constructions revealing English-source thinking: possessives for body parts ("ses yeux" vs "les yeux"), progressive overuse ("était en train de"), English idiom calques, preposition choices following English logic, passive where French uses active or pronominal.
- **Works**: Body parts use articles, not possessives (unless ambiguous). Progressive is rare and marked. Idioms are natively French. Prepositions follow French logic. Active and pronominal forms preferred over passive.
- **Fails**: "Il leva ses yeux" instead of "Il leva les yeux." "Elle était en train de marcher" where "elle marchait" suffices. English passive calqued into French.
- **Fix pattern**: Replace with the French-native construction. Articles for body parts. Simple tenses over progressive. Pronominal over passive. French preposition logic.
- **Example**:
  > "Il mit ses mains dans ses poches et leva ses yeux vers le ciel."
  > → Possessifs anglais sur parties du corps — artefact de traduction
  > → "Il mit les mains dans les poches et leva les yeux vers le ciel"
