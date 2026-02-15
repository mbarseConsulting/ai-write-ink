# qa-final — Report Format

> Editorial role: copy editor / proofreader
> Default output: inline
> Suggestion level: direct corrections — the actual fix, not a suggestion. The user accepts or refuses.
> Output language: French content, English column headers. Axis names and severity codes stay English.

---

## Severity

| Code | Level | Meaning |
|------|-------|---------|
| `BLK` | Blocking | Error. Must fix before publication. |
| `MAJ` | Major | Weakens the text mechanically. Should fix. |
| `SUG` | Suggestion | Minor inconsistency. Author decides. |

---

## Axis Registry

Every axis from all rules files. All are findings (no verdicts in qa-final).

| Axis | Source | Default Sev |
|------|--------|-------------|
| spelling | grammar-rules | BLK |
| grammar | grammar-rules | BLK |
| punctuation | grammar-rules | MAJ |
| dialogue-dashes | typography-rules | MAJ |
| french-spacing | typography-rules | MAJ |
| formatting-consistency | typography-rules | SUG |
| flag-words | ai-residual-rules | MAJ |
| narrative-tics | ai-residual-rules | SUG |
| structural-patterns | ai-residual-rules | SUG |
| monotone-rhythm | ai-residual-rules | SUG |
| proper-nouns | consistency-rules | BLK |
| numbers-dates | consistency-rules | BLK |
| narrative-tense | consistency-rules | BLK |
| register-stability | consistency-rules | MAJ |

---

## Default Format: Inline

The copy editor corrects. Not suggestions — the fix. The user accepts or refuses each correction.

### Structure

```markdown
## qa-final — Inline

[Each finding, in text order:]

**¶N** — « [passage cité] »
SEV axis — [erreur, ≤15 mots]
→ « [texte corrigé] »

[Strengths worth noting:]

✓ [élément bien tenu — une phrase]

[Patterns, only if 3+ of same issue:]

**Recurring** : [axis] — [count]x — [direction systémique]

---

Accepte ou refuse chaque correction. En cas de doute stylistique, signalé comme query.
```

### Finding Format

Each finding has three lines:

1. **Location + passage** — the exact text with the error
2. **Severity + axis + error** — what's wrong, concise
3. **→ corrected text** — the fix, ready to paste

The copy editor gives the FIX, not the direction. No discussion — the correction.

**BLK example** (spelling):
```
**¶5** — « Elle ce dirigea vers la sorti. »
BLK spelling — « ce » → « se » ; « sorti » → « sortie »
→ « Elle se dirigea vers la sortie. »
```

**BLK example** (grammar):
```
**¶12** — « Les fleurs qu'il a cueilli étaient fanées. »
BLK grammar — accord participe passé, COD antéposé
→ « Les fleurs qu'il a cueillies étaient fanées. »
```

**MAJ example** (punctuation):
```
**¶8** — « Quand il arriva elle dormait déjà. »
MAJ punctuation — virgule manquante après subordonnée antéposée
→ « Quand il arriva, elle dormait déjà. »
```

**MAJ example** (dialogue-dashes):
```
**¶15** — « « Je pars demain. » Il se leva. — Et moi ? dit-elle. »
MAJ dialogue-dashes — mélange guillemets et tirets
→ Harmoniser en tirets cadratins
```

**MAJ example** (flag-words — AI residual):
```
**¶22** — « Une tension palpable s'installa entre eux. »
MAJ flag-words — mot-drapeau IA survivant : « palpable »
→ Remplacer ou supprimer (passage à retravailler en amont)
```

**SUG example** (narrative-tics):
```
**l.12, l.45, l.89, l.134** — « gorge serrée » × 4
SUG narrative-tics — fréquence 1/1500 mots (seuil : 1/2000)
→ Garder 2 max, varier les 2 autres
```

**BLK example** (proper-nouns):
```
**ch.18 ¶3** — « chateau de mortefontaine »
BLK proper-nouns — 3 graphies pour le même lieu (ch.3, ch.18, ch.25)
→ Fixer la forme canonique : « Château de Mortefontaine » (première occurrence ch.3)
```

**BLK example** (narrative-tense):
```
**¶9** — « Le feu est passé au rouge. »
BLK narrative-tense — glissement passé simple → présent en narration
→ « Le feu passa au rouge. »
```

### Query Format

When uncertain if error or stylistic choice:

```
**¶14** — « C'était vraiment la merde. »
? register-stability — registre familier dans narration soutenue
→ Query : discours indirect libre intentionnel ? Si oui, signaler par le contexte. Si non, aligner sur le registre.
```

### Strength Format

```
✓ Noms propres : « Château de Mortefontaine » — graphie stable sur 30 chapitres
✓ Système temporel : passé simple / imparfait tenu sans faille
```

Copy editor strengths are brief. They confirm what's mechanically clean.

### Closing Line

```
---

Accepte ou refuse chaque correction. En cas de doute stylistique, signalé comme query.
```

---

## Alternative: Diagnostic

On explicit user request. Full proofreading report.

```markdown
## qa-final — Diagnostic

### Context
- **Text** : [longueur, type]
- **Refs** : [feuille de style, notes de passes précédentes — ou « aucune »]
- **Scope** : [rules files chargés]

### First Impression
[2-3 phrases en français. Propreté mécanique du texte. Prêt à publier ou pas.]

### Findings

| # | Loc | Passage | Axis | Sev | Error | Fix |
|---|-----|---------|------|-----|-------|-----|
| 1 | ¶5 | « ce dirigea » | grammar:spelling | BLK | [en français] | « [corrigé] » |

> Fix column: the actual correction. Copy editor standard.

### Patterns

| Pattern | Count | Examples | Sev | Direction |
|---------|-------|----------|-----|-----------|
| [axis] | N | « ex1 » ¶2, « ex2 » ¶7, « ex3 » ¶14 | MAJ | [direction systémique, en français] |

### Strengths

| Element | Scope | Status |
|---------|-------|--------|
| [élément mécanique] | [portée] | [statut — en français] |

### Queries

| # | Loc | Question | Recommendation |
|---|-----|----------|----------------|
| 1 | ¶14 | [doute stylistique] | [recommandation, en français] |

### Priority Fixes
1. #[N] — [correction à plus fort impact, en français]

> Max 5. Impact order.
```

---

## Alternative: Assessment

On explicit user request ("est-ce que mon texte est prêt ?").

```markdown
## qa-final — Assessment

### Verdict
[Réponse directe en français. 2-3 phrases. Prêt à publier ou pas — et pourquoi.]

### Grid

| Axis | State | Note | Suggestion |
|------|-------|------|------------|
| spelling | clean / some errors / frequent | [en français] | [en français] |
| grammar | clean / some errors / frequent | [en français] | [en français] |
| punctuation | clean / some errors / frequent | [en français] | [en français] |
| dialogue-dashes | consistent / mixed / broken | [en français] | [en français] |
| french-spacing | correct / some gaps / broken | [en français] | [en français] |
| formatting-consistency | consistent / some drift / inconsistent | [en français] | [en français] |
| flag-words | clean / some survivors / infected | [en français] | [en français] |
| narrative-tics | varied / some repeats / mechanical | [en français] | [en français] |
| structural-patterns | organic / some formula / formulaic | [en français] | [en français] |
| monotone-rhythm | varied / some chains / mechanical | [en français] | [en français] |
| proper-nouns | stable / some drift / inconsistent | [en français] | [en français] |
| numbers-dates | consistent / some errors / broken | [en français] | [en français] |
| narrative-tense | solid / some slips / unstable | [en français] | [en français] |
| register-stability | stable / some shifts / inconsistent | [en français] | [en français] |

### Key Issues
[Cités avec correction. En français.]

### Strengths
[Ce qui est mécaniquement propre. En français.]
```

---

## Report Rules

### Correction Law
Every finding gets the actual fix. Not a direction — the corrected text.
- If the fix is a single word, give the word.
- If the fix is a restructured sentence, give the sentence.
- If the fix requires context (e.g., convention choice), give the recommendation with the canonical form.

### Query Protocol
When uncertain if error or stylistic choice:
- Flag as `?` instead of severity code.
- State the doubt.
- Recommend the default, note the alternative.

### Language
- Column headers: English.
- Cell content: French.
- Axis names: English.
- Severity codes: English (BLK/MAJ/SUG).
- Section headings in output: English.

### Citation
1. Every finding quotes the passage with the error.
2. Name the rule violated — precisely.
3. One fix per finding.

### Patterns
1. 3+ same axis = pattern.
2. Max 3 representative examples.
3. One systemic direction.

### Concision
- **Passage**: max 10 quoted words.
- **Error**: max 15 words.
- **Fix**: as short as possible — the corrected text.
- **Axis ref**: `file:axis` in diagnostic, `axis` in inline.

### Severity Adjustment
Default severity from the registry. Adjust per context:
- A single typo in 50,000 words → still BLK, but noted as isolated.
- A formatting inconsistency in a draft → SUG.
- Context governs. The default is a starting point.
