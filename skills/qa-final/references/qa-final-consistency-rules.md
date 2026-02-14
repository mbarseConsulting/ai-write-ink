# Consistency Rules — qa-final

> Scope: meso
> Loaded when: text >= 2 scenes or submitted with reference material
> Evaluates: Mechanical consistency across the manuscript — not plot, mechanics
> Preferred output: diagnostic

---

## Finding Axes

### proper-nouns

- **Detects**: Inconsistent spelling of character names, place names, invented terms, organization names across the manuscript. Hyphenation drift, capitalization drift.
- **Works**: Every proper noun is spelled identically throughout. "Chateau de Mortefontaine" never becomes "Mortefontaine-le-Chateau." Compound names, hyphenation, and capitalization are stable.
- **Fails**: A character name changes spelling. A place name gains or loses a hyphen. An invented term shifts capitalization mid-manuscript.
- **Fix pattern**: Establish the canonical form (first usage or most frequent) and align all occurrences.
- **Example**:
  > Ch.3 "Chateau de Mortefontaine" ... Ch.18 "chateau de mortefontaine" ... Ch.25 "Mortefontaine-le-Chateau"
  > → Nom propre : 3 graphies pour le même lieu
  > → Fixer la forme canonique et aligner les 3 occurrences

### numbers-dates

- **Detects**: Age inconsistencies, duration miscalculations, date contradictions. Currencies, measurements, and time references that don't add up.
- **Works**: Ages track with time. Durations are consistent. If a character is 32 in chapter 1 and 6 months pass, they're still 32 (or 33 if birthday occurred).
- **Fails**: A character's stated age contradicts established birth date plus elapsed time. A journey described as 3 days takes a week by the calendar.
- **Fix pattern**: Build a reference table. Cross-check ages, dates, and durations. Correct the inconsistent reference.
- **Example**:
  > Ch.1 "né en 1985" ... Ch.12 "en 2020, à trente-deux ans"
  > → Dates : né en 1985, aurait 35 ans en 2020, pas 32
  > → Corriger : "trente-cinq ans" ou ajuster l'année de naissance

### narrative-tense

- **Detects**: Accidental shifts between passe simple and passe compose in narration. Tense system instability within narrative mode. Inconsistent flashback tense treatment.
- **Works**: Passe simple for narrative action, imparfait for description. Dialogue uses any tense naturally. Flashbacks use plus-que-parfait consistently. Returns to present narrative clearly marked.
- **Fails**: A paragraph of passe simple narration slips into passe compose for one sentence. A flashback starts in plus-que-parfait and drifts to passe simple without returning.
- **Fix pattern**: Identify the tense system, locate the slip, and align to the established convention.
- **Example**:
  > "Il traversa la rue. Le feu est passé au rouge. Elle l'attendait de l'autre côté."
  > → Temps : glissement passé simple → présent → imparfait en narration
  > → "Le feu passa au rouge" (passé simple, aligné sur le système narratif)

### register-stability

- **Detects**: Unintentional shifts in narrative distance or formality. Sudden colloquialism in formal narration. Narrative distance (close third vs distant third) changing within scenes.
- **Works**: Narrative register is stable within scenes. Formality level consistent in narration. Shifts in register are intentional (dialogue, free indirect speech).
- **Fails**: Formal narration interrupted by colloquial phrasing outside of dialogue or free indirect speech. Close third suddenly becomes distant third mid-scene.
- **Fix pattern**: Identify the established register and align the outlier. If the shift is intentional (free indirect speech), ensure it's readable as such.
- **Example**:
  > "Le marquis considéra la situation avec gravité. C'était vraiment la merde."
  > → Registre : narration soutenue puis familier sans discours indirect libre
  > → Si DIL : signaler par le contexte. Sinon : aligner sur le registre narratif
