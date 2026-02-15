# qa-characters — Report Format

> Editorial role: character consultant
> Default output: assessment
> Suggestion level: psychological directions — where the character needs work and why
> Output language: French content, English column headers. Axis names and severity codes stay English.

---

## Severity

| Code | Level | Meaning |
|------|-------|---------|
| `BLK` | Blocking | Must fix. The character is not credible. |
| `MAJ` | Major | Should fix. The character is weakened. |
| `SUG` | Suggestion | Could deepen. Author decides. |

## Verdict Scale

| Verdict | Meaning |
|---------|---------|
| **Works** | Psychologically coherent. Say WHY. |
| **Weakens** | Credibility undermined. Say WHAT, WHERE, and HOW TO FIX. |
| **Fails** | Not credible. Say WHY, name the mechanism, PROPOSE DIRECTION. |

---

## Axis Registry

| Axis | Source | Type | Default Sev |
|------|--------|------|-------------|
| contradiction-credibility | depth-rules | finding | MAJ |
| defense-mechanisms | depth-rules | finding | MAJ |
| monologue-credibility | depth-rules | finding | MAJ |
| want-need-gap | depth-rules | verdict | — |
| wound-coherence | depth-rules | verdict | — |
| inner-lie | depth-rules | verdict | — |
| relational-patterns | evolution-rules | finding | SUG |
| evolution-credibility | evolution-rules | finding | BLK |
| arc-completion | evolution-rules | verdict | — |
| relationship-credibility | dynamics-rules | finding | MAJ |
| character-distinctiveness | dynamics-rules | finding | BLK |
| secondary-depth | dynamics-rules | finding | SUG |
| cast-balance | dynamics-rules | verdict | — |
| antagonist-logic | dynamics-rules | verdict | — |

---

## Default Format: Assessment

The character consultant evaluates psychology and credibility. Verdict-driven, not line-by-line.

```markdown
## qa-characters — Assessment

### Verdict
[Réponse directe en français. 2-3 phrases. Le personnage est crédible ou pas — et pourquoi.]

### Grid

| Axis | State | Note | Suggestion |
|------|-------|------|------------|
| contradiction-credibility | coherent / strained / broken | [en français] | [en français] |
| defense-mechanisms | consistent / inconsistent / absent | [en français] | [en français] |
| monologue-credibility | authentic / stiff / narrated | [en français] | [en français] |
| want-need-gap | clear and exploited / present but passive / absent | [en français] | [en français] |
| wound-coherence | drives behavior / surfaces occasionally / decorative / absent | [en français] | [en français] |
| inner-lie | governing / present / unclear / absent | [en français] | [en français] |
| relational-patterns | intentional / accidental / absent | [en français] | [en français] |
| evolution-credibility | shown / declared / absent | [en français] | [en français] |
| arc-completion | arrived / partial shift / static / regressed | [en français] | [en français] |
| relationship-credibility | human / functional / flat | [en français] | [en français] |
| character-distinctiveness | unique / similar / interchangeable | [en français] | [en français] |
| secondary-depth | independent / functional / cardboard | [en français] | [en français] |
| cast-balance | balanced / skewed justified / skewed unjustified / thin | [en français] | [en français] |
| antagonist-logic | fully realized / comprehensible / thin / cardboard | [en français] | [en français] |

> Every Suggestion cell filled. Even positive: « maintenir » or « pousser plus loin ».

### Key Issues
[Passage-cited, with psychological direction. En français.]

### Strengths
[Ce qui fonctionne. Mécanisme psychologique nommé. En français.]

### Suggestions
[2-5 prochaines étapes concrètes pour le personnage. En français.]
```

---

## Alternative: Diagnostic

On explicit user request. Full structured report.

```markdown
## qa-characters — Diagnostic

### Context
- **Text** : [longueur, type]
- **Character(s)** : [nom(s) évalué(s)]
- **Refs** : [fiches personnages, docs — ou « aucune »]
- **Scope** : [rules files chargés]

### First Impression
[2-3 phrases en français. Réaction instinctive sur le personnage. Crédible ou pas — et pourquoi.]

### Findings

| # | Loc | Passage | Axis | Sev | Issue | Direction |
|---|-----|---------|------|-----|-------|-----------|
| 1 | ¶5 | « cité ≤10 mots » | depth:contradiction-credibility | MAJ | [≤15 mots, en français] | [≤15 mots, en français] |

> Direction: psychological direction, not rewrite. Where the character needs work.

### Patterns

| Pattern | Count | Examples | Sev | Direction |
|---------|-------|----------|-----|-----------|
| [axis] | N | « ex1 » ¶2, « ex2 » ¶7 | MAJ | [direction systémique, en français] |

### Strengths

| Passage | Axis | Mechanism | Effect |
|---------|------|-----------|--------|
| « cité ≤10 mots » | [axis] | [ce que l'auteur a fait] | [pourquoi ça fonctionne] |

### Verdicts

| Scope | Verdict | Justification | Suggestion |
|-------|---------|---------------|------------|
| [rules file] | Works / Weakens / Fails | [en français] | [en français] |

### Priority Fixes
1. #[N] — [action à plus fort impact, en français]

> Max 5. Impact order.
```

---

## Alternative: Inline

On explicit user request. Passage-by-passage psychological notes.

```markdown
## qa-characters — Inline

**¶N** — « [passage cité] »
SEV axis — [problème psychologique, en français, ≤15 mots]
→ [direction : ce dont le personnage a besoin ici]

**¶N** — « [passage cité] »
✓ [ce qui fonctionne psychologiquement — une phrase]

**Recurring** : [axis] — [count]x — [direction systémique]

---

Chaque direction est psychologique, pas stylistique. L'auteur décide comment l'implémenter dans la prose.
```

---

## Report Rules

### Direction Law
Every finding gets a psychological direction. Not a rewrite — a direction.
- The character consultant says WHAT doesn't work psychologically and WHY.
- Directions reference the character's established psychology (wound, lie, defense).

### Language
- Column headers: English.
- Cell content: French.
- Axis names: English.
- Severity codes: English (BLK/MAJ/SUG).
- Section headings in output: English.

### Citation
1. Every finding quotes the passage.
2. Name the psychological mechanism — not "not credible", WHY.
3. One direction per finding.

### Patterns
1. 3+ same axis = pattern.
2. Max 3 representative examples.
3. One systemic direction.

### Concision
- **Passage**: max 10 quoted words.
- **Issue**: max 15 words.
- **Direction**: max 15 words.
- **Axis ref**: `file:axis` in diagnostic, `axis` in inline/assessment.

### Severity Adjustment
Default severity from the registry. Adjust per context:
- A minor inconsistency in a secondary character → SUG, not MAJ.
- Interchangeable voices in a critical dialogue scene → BLK.
- Context governs. The default is a starting point.
