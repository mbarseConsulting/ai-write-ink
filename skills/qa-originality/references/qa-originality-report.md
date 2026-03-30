# qa-originality — Report Format

> Editorial role: editorial scout | Default output: assessment
> Suggestion level: positioning directions — where derivative, where singular
> Output language: French content, English column headers. Axis names stay English.

---

## Axis Registry

| Axis                  | Source      | Type    | Default Sev |
| --------------------- | ----------- | ------- | ----------- |
| formulation-freshness | micro-rules | finding | blue        |
| linguistic-audacity   | micro-rules | finding | blue        |
| voice-singularity     | micro-rules | verdict | --          |
| situation-freshness   | meso-rules  | finding | blue        |
| trope-handling        | meso-rules  | finding | blue        |
| narrative-audacity    | meso-rules  | finding | blue        |
| scene-coherence       | meso-rules  | verdict | --          |
| concept-originality   | macro-rules | verdict | --          |
| arc-originality       | macro-rules | verdict | --          |
| ambition              | macro-rules | verdict | --          |
| artistic-identity     | macro-rules | verdict | --          |
| maturity              | macro-rules | verdict | --          |

Each axis is defined ONCE in its source rules file. This registry is a routing index only.

---

## Gating Summary

- voice-singularity capped by formulation-freshness (see micro-rules)
- scene-coherence capped by meso finding axes (see meso-rules)
- artistic-identity capped by concept-originality + arc-originality (see macro-rules)
- maturity capped by ambition (see macro-rules)

---

## Language Convention

- English: column headers, axis names, section headings.
- French: cell content, suggestions, directions, first impression, verdicts, closing lines.

---

## Report Rules

### Source Law

Every deja-vu NAMES the source: convention, trope, author, genre expectation. Not just "cliche" — FROM WHERE.

### Singularity Law

Every strength names WHY it's original — the mechanism that makes it irreplaceable.

### Genealogy Law

Every stock / derivative finding (red severity) MUST include creative genealogy: 2-3 works that did the same move + 1 that swerved. Non-negotiable for red. Encouraged for yellow.

---

## Format Overrides

### Assessment (default)

```markdown
## qa-originality — Assessment

### Verdict

[Reponse directe en francais. 2-3 phrases. Ce texte est-il singulier — et pourquoi, ou pourquoi pas.]

### Context
- **Refs provided**: [fiches, docs — ou "aucune"]
- **Refs missing**: [ce qui aiderait — ou "complet"]
```

Grid states: defined in each rules file. Do NOT redefine here.
Apply all Report Rules above.

### Diagnostic (on explicit request)

Header: `## qa-originality — Diagnostic` then Context block (Text, Refs provided, Refs missing, Scope) then `### First Impression` (2-3 phrases en francais).

### Inline (on explicit request)

Header: `## qa-originality — Inline`. Apply all Report Rules.
