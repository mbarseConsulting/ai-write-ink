# qa-originality — Report Format

> Editorial role: editorial scout / reader
> Default output: assessment
> Suggestion level: positioning directions — where the work is derivative and where it's singular
> Output language: French content, English column headers. Axis names and severity codes stay English.

---

## Severity

| Code | Level | Meaning |
|------|-------|---------|
| `BLK` | Blocking | Derivative to the point of damage. |
| `MAJ` | Major | Unoriginal element weakening the work. |
| `SUG` | Suggestion | Could push further. Author decides. |

## Verdict Scale

| Verdict | Meaning |
|---------|---------|
| **Works** | Original. Say WHY — name the mechanism. |
| **Weakens** | Familiar without compensation. Say WHAT and WHERE to push. |
| **Fails** | Derivative. Say WHY and PROPOSE where to find singularity. |

---

## Axis Registry

| Axis | Source | Type | Default Sev |
|------|--------|------|-------------|
| formulation-freshness | micro-rules | finding | SUG |
| linguistic-audacity | micro-rules | finding | SUG |
| voice-singularity | micro-rules | verdict | — |
| situation-freshness | meso-rules | finding | SUG |
| trope-handling | meso-rules | finding | SUG |
| narrative-audacity | meso-rules | finding | SUG |
| scene-coherence | meso-rules | verdict | — |
| concept-originality | macro-rules | verdict | — |
| arc-originality | macro-rules | verdict | — |
| ambition | macro-rules | verdict | — |
| artistic-identity | macro-rules | verdict | — |
| maturity | macro-rules | verdict | — |

---

## Default Format: Assessment

The editorial scout writes a reader's report. Verdict-driven: is this work singular?

```markdown
## qa-originality — Assessment

### Verdict
[Réponse directe en français. 2-3 phrases. Ce texte est-il singulier — et pourquoi, ou pourquoi pas.]

### Grid

| Axis | State | Note | Suggestion |
|------|-------|------|------------|
| formulation-freshness | fresh / mixed / stock | [en français] | [en français] |
| linguistic-audacity | daring / competent / timid | [en français] | [en français] |
| voice-singularity | distinctive / emerging / competent / generic | [en français] | [en français] |
| situation-freshness | surprising / familiar-with-swerve / stock | [en français] | [en français] |
| trope-handling | transcended / subverted / followed / unaware | [en français] | [en français] |
| narrative-audacity | bold / some risks / safe | [en français] | [en français] |
| scene-coherence | unified / mostly coherent / assembled / fractured | [en français] | [en français] |
| concept-originality | genuinely new / fresh combination / familiar with texture / derivative | [en français] | [en français] |
| arc-originality | surprising-inevitable / some surprises / predictable / formulaic | [en français] | [en français] |
| ambition | ambitious / competent / safe / timid | [en français] | [en français] |
| artistic-identity | irreplaceable / memorable / competent / interchangeable | [en français] | [en français] |
| maturity | masterful / confident / developing / uncontrolled | [en français] | [en français] |

> Every Suggestion cell filled. Even positive: « maintenir » or « pousser plus loin ».

### Key Issues
[Passage-cited. Nommer la source du déjà-vu : quel trope, quelle convention, quel auteur. En français.]

### Strengths
[Ce qui est singulier. Nommer POURQUOI c'est original. En français.]

### Suggestions
[2-5 directions pour amplifier la singularité. En français.]
```

---

## Alternative: Diagnostic

On explicit user request. Full structured originality report.

```markdown
## qa-originality — Diagnostic

### Context
- **Text** : [longueur, type]
- **Refs** : [fiches, docs — ou « aucune »]
- **Scope** : [rules files chargés]

### First Impression
[2-3 phrases en français. Première réaction de scout : ce texte se distingue ou pas.]

### Findings

| # | Loc | Passage | Axis | Sev | Issue | Direction |
|---|-----|---------|------|-----|-------|-----------|
| 1 | ¶5 | « cité ≤10 mots » | micro:formulation-freshness | SUG | [en français — nommer la source] | [en français — où pousser] |

> Issue column must NAME the source: quel trope, quelle convention, quel précédent.
> Direction column: where to find singularity.

### Patterns

| Pattern | Count | Examples | Sev | Direction |
|---------|-------|----------|-----|-----------|
| [axis] | N | « ex1 » ¶2, « ex2 » ¶7 | SUG | [direction, en français] |

### Strengths

| Passage | Axis | Mechanism | Effect |
|---------|------|-----------|--------|
| « cité ≤10 mots » | [axis] | [ce qui est original] | [pourquoi ça fonctionne] |

> The scout names what's IRREPLACEABLE. Not just "good" — singular.

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

On explicit user request. Passage-by-passage originality notes.

```markdown
## qa-originality — Inline

**¶N** — « [passage cité] »
SUG axis — [ce qui est dérivé et d'où — nommer la source]
→ [direction : où trouver la singularité ici]

**¶N** — « [passage cité] »
✓ [ce qui est singulier et pourquoi — une phrase]

**Recurring** : [axis] — [count]x — [direction systémique]

---

Chaque constat nomme la source du déjà-vu. Chaque direction pointe vers la singularité.
```

---

## Report Rules

### Source Law
Every finding of déjà-vu NAMES the source: the convention, the trope, the author, the genre expectation. Not just "cliché" — FROM WHERE.

### Singularity Law
Every strength names WHY it's original — the mechanism that makes it irreplaceable.

### Language
- Column headers: English.
- Cell content: French.
- Axis names: English.
- Severity codes: English (BLK/MAJ/SUG).
- Section headings in output: English.

### Citation
1. Every finding quotes the passage.
2. Name the source of the déjà-vu.
3. One direction per finding: where to push.

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
- A stock metaphor in an otherwise singular voice → SUG.
- A derivative central concept → BLK regardless of default.
- Context governs. The default is a starting point.
