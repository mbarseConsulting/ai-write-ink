# qa-prose — Report Format

> Editorial role: line editor
> Default output: inline
> Suggestion level: proposed rewrites — the user accepts or refuses each one
> Output language: French content, English column headers. Axis names and severity codes stay English.

---

## Severity

| Code | Level | Meaning |
|------|-------|---------|
| `BLK` | Blocking | Must fix. The text is broken at this point. |
| `MAJ` | Major | Should fix. The text is weakened. |
| `SUG` | Suggestion | Could improve. Author decides. |

---

## Axis Registry

Every axis from all rules files. All are findings (no verdicts in qa-prose).

| Axis | Source | Default Sev |
|------|--------|-------------|
| pov-discipline | craft-rules | BLK |
| show-tell | craft-rules | MAJ |
| over-explanation | craft-rules | MAJ |
| exposition-control | craft-rules | MAJ |
| dialogue-craft | craft-rules | SUG |
| description-craft | craft-rules | SUG |
| flag-words | ai-rules | MAJ |
| ai-structures | ai-rules | MAJ |
| ai-tics | ai-rules | MAJ |
| repetition | ai-rules | SUG |
| forbidden-locutions | ai-rules | SUG |
| tense-discipline | language-rules | BLK |
| syntax-naturalness | language-rules | MAJ |
| translation-artifacts | language-rules | MAJ |

---

## Default Format: Inline

Line editing is manuscript markup. Each finding is a margin note with a proposed rewrite. The user reads each one and decides: accept, refuse, or adapt.

### Structure

```markdown
## qa-prose — Inline

[Each finding, in text order:]

**¶N** — « [passage cité] »
SEV axis — [problème, ≤15 mots]
→ « [réécriture proposée] »

[Strengths worth noting:]

**¶N** — « [passage cité] »
✓ [ce qui fonctionne et pourquoi — une phrase]

[Patterns, only if 3+ of same issue:]

**Recurring** : [axis] — [count]x — [direction systémique, une phrase]

---

Accepte ou refuse chaque réécriture proposée. Les adaptations sont bienvenues.
```

### Finding Format

Each finding has four lines:

1. **Location + passage** — the exact text flagged
2. **Severity + axis + problem** — what's wrong, concise, in French
3. **Proposed rewrite** — the concrete alternative, ready to paste
4. *(implicit)* — the user accepts, refuses, or adapts

The proposed rewrite is NOT a direction. It's the actual text. The line editor shows, doesn't just tell.

**BLK example** (pov-discipline):
```
**¶4** — « Elle sourit, soulagée de le voir partir. Il sentit une pointe de culpabilité. »
BLK pov-discipline — head-hopping, deux POV en deux phrases
→ « Elle sourit — il crut y lire du soulagement. Quelque chose se tordit dans sa poitrine. »
```

**MAJ example** (show-tell):
```
**¶7** — « Elle ressentit une profonde tristesse en regardant la maison vide. »
MAJ show-tell — émotion nommée, pas montrée
→ « Ses doigts se refermèrent sur la clé. La maison attendait derrière la grille, volets clos. »
```

**MAJ example** (flag-words):
```
**¶12** — « Une tension palpable régnait dans la pièce. »
MAJ flag-words — « palpable » mot-drapeau IA
→ « Personne ne touchait à son verre. Le silence avait cette densité d'avant les ruptures. »
```

**MAJ example** (translation-artifacts):
```
**¶9** — « Il mit ses mains dans ses poches et leva ses yeux vers le ciel. »
MAJ translation-artifacts — possessifs anglais sur parties du corps
→ « Il mit les mains dans les poches et leva les yeux vers le ciel. »
```

**SUG example** (repetition):
```
**¶15-18** — « Il traversa… Il poussa… Il monta… Il entra… »
SUG repetition — chaîne « Il + verbe », monotonie structurelle
→ « Il traversa la cour. La porte céda sous sa paume. En haut de l'escalier, la chambre l'attendait. »
```

### Strength Format

```
**¶22** — « Le café avait un goût de lendemain. »
✓ Image sensorielle ancrée, spécifique — condensation efficace
```

Strengths are noted. They reinforce what works. No rewrite — just the mechanism named.

### Pattern Format

When 3+ findings share the same axis:

```
**Recurring** : show-tell — 5x (¶3, ¶7, ¶14, ¶21, ¶28) — les émotions sont systématiquement nommées au lieu d'être incarnées. Réflexe à désapprendre : supprimer le label, garder le geste.
```

One line. Axis, count, locations, systemic direction.

### Closing Line

Every inline report ends with:

```
---

Accepte ou refuse chaque réécriture proposée. Les adaptations sont bienvenues.
```

---

## Alternative: Diagnostic

On explicit user request ("fais-moi un diagnostic complet"). Full structured report.

```markdown
## qa-prose — Diagnostic

### Context
- **Text** : [longueur, type]
- **Refs** : [fiches, docs — ou « aucune »]
- **Scope** : [fichiers de règles chargés]

### First Impression
[2-3 phrases en français. Réaction instinctive de line editor. Pas un résumé — l'instinct.]

### Findings

| # | Loc | Passage | Axis | Sev | Issue | Rewrite |
|---|-----|---------|------|-----|-------|---------|
| 1 | ¶3 | « cité ≤10 mots » | craft:pov-discipline | BLK | [≤15 mots, en français] | « [réécriture proposée] » |

> Rewrite column: the actual rewrite, not a direction. Line editor standard.

### Patterns

| Pattern | Count | Examples | Sev | Direction |
|---------|-------|----------|-----|-----------|
| [axis] | N | « ex1 » ¶2, « ex2 » ¶7, « ex3 » ¶14 | MAJ | [correction systémique, en français, ≤15 mots] |

### Strengths

| Passage | Axis | Mechanism | Effect |
|---------|------|-----------|--------|
| « cité ≤10 mots » | [axis] | [ce que l'auteur a fait] | [pourquoi ça fonctionne] |

> Never empty. Name the craft mechanism.

### Priority Fixes
1. #[N] — [action à plus fort impact, en français]

> Max 5. Impact order.
```

---

## Alternative: Assessment

On explicit user request ("est-ce que ma prose est bonne ?"). Verdict + grid.

```markdown
## qa-prose — Assessment

### Verdict
[Réponse directe en français. 2-3 phrases. L'avis honnête du line editor.]

### Grid

| Axis | State | Note | Suggestion |
|------|-------|------|------------|
| pov-discipline | clean / slips / broken | [en français] | [en français] |
| show-tell | shows / mixed / tells | [en français] | [en français] |
| over-explanation | trusts reader / occasionally doubles / systematic | [en français] | [en français] |
| exposition-control | woven / some blocks / dumps | [en français] | [en français] |
| dialogue-craft | alive / functional / flat | [en français] | [en français] |
| description-craft | filtered / mixed / catalog | [en français] | [en français] |
| flag-words | clean / some survivors / infected | [en français] | [en français] |
| ai-structures | organic / some patterns / formulaic | [en français] | [en français] |
| ai-tics | varied / some repeats / mechanical | [en français] | [en français] |
| repetition | varied / some echoes / monotone | [en français] | [en français] |
| forbidden-locutions | clean / some leaks / systematic | [en français] | [en français] |
| tense-discipline | solid / some slips / unstable | [en français] | [en français] |
| syntax-naturalness | native / some stiffness / translated | [en français] | [en français] |
| translation-artifacts | clean / some calques / pervasive | [en français] | [en français] |

> Every Suggestion cell is filled. Even positive: « maintenir » or « pousser plus loin ».

### Key Issues
[Cités avec passage, réécriture proposée. Même rigueur que l'inline.]

### Strengths
[Ce qui fonctionne. Mécanisme nommé. En français.]
```

---

## Report Rules

### Rewrite Law
Every finding gets a proposed rewrite. Not a direction — the text. The user decides.
- If you can't write the rewrite, you haven't understood the problem.
- The rewrite preserves the author's substance. It fixes the craft issue and nothing else.
- Never add content the author didn't intend.

### Language
- Column headers: English.
- Cell content (issues, notes, suggestions, rewrites): French.
- Axis names: English (technical identifiers).
- Severity codes: English (BLK/MAJ/SUG).
- Section headings in output: English.
- Closing line: French.

### Citation
1. Every finding quotes the passage. No abstract complaints.
2. Name the mechanism — not "doesn't work", WHY.
3. One rewrite per finding. Not options.

### Patterns
1. 3+ same axis = pattern.
2. Max 3 example locations.
3. One systemic direction.

### Concision
- **Passage**: max 10 quoted words.
- **Issue**: max 15 words.
- **Rewrite**: as long as needed — it's the actual text.
- **Axis ref**: `axis` (no file prefix in inline, `file:axis` in diagnostic).

### Severity Adjustment
Default severity from the registry. Adjust per context:
- A single tense slip in otherwise solid narration → SUG, not BLK.
- A show-tell issue on the central emotional beat of the scene → BLK, not MAJ.
- Context governs. The default is a starting point.
