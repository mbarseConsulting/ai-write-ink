# qa-reader — Report Format

> Editorial role: developmental editor
> Default output: diagnostic (standard mode) / assessment (bookends mode)
> Suggestion level: structural directions — not rewrites, but where to push and why
> Output language: French content, English column headers. Axis names and severity codes stay English.

---

## Severity

| Code | Level | Meaning |
|------|-------|---------|
| `BLK` | Blocking | Must fix. The reading experience is broken. |
| `MAJ` | Major | Should fix. The reader's engagement is weakened. |
| `SUG` | Suggestion | Could improve. Author decides. |

## Verdict Scale

| Verdict | Meaning |
|---------|---------|
| **Works** | Achieves what it should. Say WHY. |
| **Weakens** | Potential undermined. Say WHAT, WHERE, and HOW TO FIX. |
| **Fails** | Does not achieve. Say WHY, name the mechanism, PROPOSE DIRECTION. |

---

## Axis Registry

### Standard Mode — Always loaded

| Axis | Source | Type | Default Sev |
|------|--------|------|-------------|
| hook | micro-rules | finding | MAJ |
| sentence-rhythm | micro-rules | finding | SUG |
| density | micro-rules | finding | MAJ |
| sensory-clarity | micro-rules | finding | MAJ |
| dialogue-effect | micro-rules | finding | SUG |
| word-precision | micro-rules | finding | SUG |

### Standard Mode — Loaded per scope

| Axis | Source | Type | Default Sev | Loaded when |
|------|--------|------|-------------|-------------|
| tension | scene-rules | finding | BLK | >= 1 scene |
| scene-arc | scene-rules | finding | BLK | >= 1 scene |
| scene-economy | scene-rules | finding | MAJ | >= 1 scene |
| microtension | scene-rules | finding | SUG | >= 1 scene |
| character-agency | scene-rules | finding | MAJ | >= 1 scene |
| pacing | scene-rules | finding | MAJ | >= 1 scene |
| chapter-ending | chapter-rules | finding | MAJ | >= 1 chapter |
| emotional-truth | chapter-rules | finding | BLK | >= 1 chapter |
| information-reveal | chapter-rules | finding | MAJ | >= 1 chapter |
| necessity | chapter-rules | verdict | — | >= 1 chapter |
| tonal-consistency | macro-rules | finding | MAJ | multiple chapters |
| narrative-arc | macro-rules | verdict | — | multiple chapters |
| singular-voice | macro-rules | verdict | — | multiple chapters |
| thematic-resonance | macro-rules | verdict | — | multiple chapters |
| global-engagement | macro-rules | verdict | — | multiple chapters |

### Bookends Mode

| Axis | Source | Type | Default Sev | Loaded when |
|------|--------|------|-------------|-------------|
| first-sentence-impact | opening-rules | finding | BLK | text includes opening |
| opening-contract | opening-rules | finding | BLK | text includes opening |
| entry-orientation | opening-rules | finding | MAJ | text includes opening |
| character-introduction | opening-rules | finding | MAJ | text includes opening |
| world-entry | opening-rules | finding | MAJ | text includes opening |
| information-control | opening-rules | finding | MAJ | text includes opening |
| hook-architecture | opening-rules | finding | BLK | text includes opening |
| final-sentence-resonance | closing-rules | finding | MAJ | text includes closing |
| emotional-precision | closing-rules | finding | BLK | text includes closing |
| closure-openness | closing-rules | finding | MAJ | text includes closing |
| climax-payoff | closing-rules | finding | BLK | text includes closing |
| character-arrival | closing-rules | finding | MAJ | text includes closing |
| resolution-pacing | closing-rules | finding | MAJ | text includes closing |
| last-image | closing-rules | finding | SUG | text includes closing |
| narrative-promise | promise-rules | verdict | — | opening + closing |
| genre-contract | promise-rules | verdict | — | opening + closing |
| thematic-arc | promise-rules | verdict | — | opening + closing |
| promise-fulfillment | promise-rules | verdict | — | opening + closing |
| arc-completion | promise-rules | verdict | — | opening + closing |
| surprise-inevitability | promise-rules | verdict | — | opening + closing |

---

## Default Format: Diagnostic (Standard Mode)

The developmental editor writes a report. Not line-level markup — structural analysis with directions for the author.

```markdown
## qa-reader — Diagnostic

### Context
- **Text** : [longueur, type]
- **Refs** : [fiches, docs — ou « aucune »]
- **Scope** : [rules files chargés selon le texte]
- **Mode** : standard

### First Impression
[2-3 phrases en français. Réaction de lecteur professionnel. Le texte accroche ou pas — et pourquoi.]

### Findings

| # | Loc | Passage | Axis | Sev | Issue | Direction |
|---|-----|---------|------|-----|-------|-----------|
| 1 | ¶3 | « cité ≤10 mots » | scene:tension | BLK | [≤15 mots, en français] | [≤15 mots, en français] |

> Direction column: structural direction, not rewrite. Dev editor tells WHERE to push, not HOW to rewrite.

### Patterns

| Pattern | Count | Examples | Sev | Direction |
|---------|-------|----------|-----|-----------|
| [axis] | N | « ex1 » ¶2, « ex2 » ¶7, « ex3 » ¶14 | MAJ | [direction systémique, en français] |

### Strengths

| Passage | Axis | Mechanism | Effect |
|---------|------|-----------|--------|
| « cité ≤10 mots » | [axis] | [ce que l'auteur a fait] | [pourquoi ça fonctionne] |

> Never empty. The dev editor reinforces what works.

### Verdicts

| Scope | Verdict | Justification | Suggestion |
|-------|---------|---------------|------------|
| [rules file] | Works / Weakens / Fails | [en français — une phrase] | [en français — une phrase] |

> Every verdict gets a suggestion. Even Works: « maintenir X » or « pousser Y plus loin ».

### Global Verdict
[1-2 phrases en français. La vérité.]

### Priority Fixes
1. #[N] — [action à plus fort impact, en français]

> Max 5. Impact order.
```

---

## Default Format: Assessment (Bookends Mode)

When evaluating opening/closing. Verdict-driven.

```markdown
## qa-reader — Assessment (Bookends)

### Verdict
[Réponse directe en français. 2-3 phrases. L'ouverture/la clôture fonctionne ou pas — et pourquoi.]

### Grid

| Axis | State | Note | Suggestion |
|------|-------|------|------------|
| [axis] | [state from rules] | [en français] | [en français] |

> States defined per axis in rules files.
> Every Suggestion cell filled. Even positive.

### Key Issues
[Passage-cited, with structural direction. En français.]

### Strengths
[Ce qui fonctionne. Mécanisme nommé.]

### Suggestions
[2-5 prochaines étapes concrètes, priorisées. En français.]
```

---

## Alternative: Inline

On explicit user request. Passage-by-passage notes. Dev editor gives structural direction, not rewrites.

```markdown
## qa-reader — Inline

**¶N** — « [passage cité] »
SEV axis — [problème, en français, ≤15 mots]
→ [direction structurelle, en français — pas une réécriture]

**¶N** — « [passage cité] »
✓ [ce qui fonctionne — une phrase]

**Recurring** : [axis] — [count]x — [direction systémique]

---

Chaque direction est une piste, pas une réécriture. L'auteur décide comment l'implémenter.
```

---

## Report Rules

### Direction Law
Every finding gets a structural direction. Not a rewrite — a direction.
- The dev editor says WHERE the problem is and WHY. The author decides HOW to fix.
- Directions are specific: not "improve pacing" but "la scène 3 a besoin d'un temps de respiration avant la confrontation."

### Language
- Column headers: English.
- Cell content (issues, notes, suggestions, directions): French.
- Axis names: English (technical identifiers).
- Severity codes: English (BLK/MAJ/SUG).
- Section headings in output: English.
- Closing line: French.

### Citation
1. Every finding quotes the passage. No abstract complaints.
2. Name the mechanism — not "doesn't work", WHY.
3. One direction per finding. Not options.

### Patterns
1. 3+ same axis = pattern.
2. Max 3 representative examples.
3. One systemic direction.

### Concision
- **Passage**: max 10 quoted words.
- **Issue**: max 15 words.
- **Direction**: max 15 words.
- **Axis ref**: `file:axis` in diagnostic, `axis` in inline.

### Severity Adjustment
Default severity from the registry. Adjust per context:
- A missing hook in a reflective interlude → SUG, not MAJ.
- A scene without tension at a critical plot point → BLK, not just BLK by default.
- Context governs. The default is a starting point.
