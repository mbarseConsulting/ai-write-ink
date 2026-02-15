# Grammar Rules — edit-final

> Scope: micro
> Loaded when: always
> Evaluates: Spelling, grammar, punctuation — the mechanical layer
> Preferred output: inline

---

## Finding Axes

### spelling

- **Detects**: Typos, missing words, letter inversions, homophone errors ("ce"/"se", "ou"/"ou", "a"/"a"). Accented characters. Proper noun spelling (cross-reference with established usage).
- **Works**: Zero typos. Every word spelled correctly. Homophones used correctly. Accents placed accurately.
- **Fails**: Any misspelling, missing word, or homophone error. Each one is a finding.
- **Fix pattern**: Direct correction — the error and its fix. No analysis needed.
- **Example**:
  > "Elle ce dirigea vers la sorti."
  > → "ce" → "se" (homophone) ; "sorti" → "sortie" (orthographe)
  > → "Elle se dirigea vers la sortie."

### grammar

- **Detects**: Agreement errors (subject-verb, noun-adjective, past participle with avoir/etre). Conjugation errors. Dangling modifiers. Broken relative clauses. Pronoun ambiguity creating confusion.
- **Works**: All agreements correct. Conjugations accurate. Modifiers attach to their intended referent. Pronouns are unambiguous.
- **Fails**: "Les enfants mangeait" (agreement). "Ayant fini son repas, la porte s'ouvrit" (dangling modifier). Pronoun "il" referring ambiguously to two male characters.
- **Fix pattern**: Direct correction with the grammar rule cited. For ambiguity: propose clarification.
- **Example**:
  > "Les fleurs qu'il a cueilli étaient fanées."
  > → Accord participe passé avec avoir : COD "qu'" (les fleurs) antéposé
  > → "Les fleurs qu'il a cueillies étaient fanées."

### punctuation

- **Detects**: Incorrect comma usage in complex sentences. Semicolon/period confusion. Colon misuse. Question/exclamation placement in dialogue. Missing or misplaced punctuation.
- **Works**: French punctuation rules followed. Commas serve syntactic clarity. Semicolons separate independent clauses. Colons introduce as expected.
- **Fails**: Comma splice joining independent clauses. Missing comma after a subordinate clause in initial position. Semicolon where a comma suffices.
- **Fix pattern**: Direct correction with the punctuation rule cited.
- **Example**:
  > "Quand il arriva elle dormait déjà."
  > → Virgule manquante après la subordonnée antéposée
  > → "Quand il arriva, elle dormait déjà."
