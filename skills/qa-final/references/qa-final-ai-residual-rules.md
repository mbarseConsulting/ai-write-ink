# AI Residual Rules — qa-final

> Scope: micro
> Loaded when: always
> Evaluates: AI pattern survivors — last scan for machine-generated artifacts after all editing passes
> Does NOT evaluate: WHY it sounds machine — this file FLAGS and COUNTS
> Preferred output: inline

If these patterns persist after previous editing, the text needs another pass.

---

## Finding Axes

### flag-words

- **Detects**: Survivors from the AI blacklist still present in the text. "Palpable", "tangible", "quelque chose dans", "un melange de", "ne put s'empecher de". Any word or phrase on the blacklist.
- **Works**: Zero blacklisted words remain. Every flagged word has been replaced or removed.
- **Fails**: One or more blacklisted words survive. Simple detection — no analysis of why.
- **Fix pattern**: Finding = word + location + "replace or remove."
- **Example**:
  > "Une tension palpable s'installa entre eux."
  > → Mot-drapeau IA survivant : "palpable" — l.47
  > → Remplacer ou supprimer

### narrative-tics

- **Detects**: Physical response tics at abnormal frequency across the manuscript. Jaw clenching, throat tightening, breath catching, heart hammering, stomach knotting, fists clenching. Count per manuscript.
- **Works**: No tic exceeds the frequency cap (1 per 2000 words for any given tic). Physical responses are varied.
- **Fails**: "Gorge serrée" appears 8 times in 12000 words. "Poings serrés" appears 5 times in 8000 words. Above threshold = flag with count and all locations.
- **Fix pattern**: List all locations for the tic. Provide the count and the frequency. Author decides which to keep and which to vary.
- **Example**:
  > "gorge serrée" : 8 occurrences (l.12, l.45, l.89, l.134, l.178, l.223, l.267, l.301)
  > → Tic narratif : fréquence 1/1500 mots (seuil : 1/2000)
  > → Garder 4 max, varier les 4 autres

### structural-patterns

- **Detects**: Formulaic paragraph structures surviving at abnormal rates. Lists of three, systematic parallelisms, mirror constructions, setup-elaboration-emotional_beat paragraph shapes.
- **Works**: Paragraph structures vary organically. No detectable formula repeating beyond what natural prose would produce.
- **Fails**: 5+ paragraphs following the same shape (setup → elaboration → emotional beat in final sentence). Systematic triads.
- **Fix pattern**: Flag with examples and count. The author restructures or requests rewrite guidance.
- **Example**:
  > 7 paragraphes sur 20 suivent le schéma "contexte → développement → émotion en fin de ¶"
  > → Structure IA : schéma formulaire à 35% — seuil dépassé
  > → Varier les formes de paragraphes

### monotone-rhythm

- **Detects**: Sequences of same-length, same-structure sentences. 5+ consecutive sentences starting with subject-verb. 3+ consecutive paragraphs with identical rhythm.
- **Works**: Sentence length and structure vary naturally. No mechanical regularity detectable.
- **Fails**: "Il fit X. Il prit Y. Il alla Z. Il vit A. Il sentit B." Five subject-verb openers in sequence. Three paragraphs with identical sentence-count and rhythm.
- **Fix pattern**: Flag the sequence with start/end locations. Author restructures with varied attacks: subordinates, complements, nominal phrases.
- **Example**:
  > l.45-49 : "Il regarda... Il comprit... Il décida... Il se leva... Il sortit..."
  > → Rythme monotone : 5 phrases consécutives "Il + verbe" — signature machine
  > → Varier les attaques : subordonnées, compléments en tête, phrases nominales
