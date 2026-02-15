# Typography Rules — edit-final

> Scope: micro
> Loaded when: always
> Evaluates: French typography conventions — the visual layer
> Does NOT evaluate: spelling/grammar (→ grammar-rules), manuscript consistency (→ consistency-rules)
> Preferred output: inline

---

## Finding Axes

### dialogue-dashes

- **Detects**: Incorrect dialogue formatting. Guillemets where tirets cadratins are expected (or vice versa, unless author's explicit convention). Mixed conventions. Missing dashes for new speakers. Incises not properly enclosed.
- **Works**: French dialogue uses tirets cadratins consistently. New speaker = new dash. Incises properly enclosed in dashes. No mixing of dialogue conventions unless explicitly requested.
- **Fails**: A dialogue section uses guillemets, then switches to dashes. A new speaker starts without a dash. An incise opens with a dash but doesn't close.
- **Fix pattern**: Establish the convention (dashes by default) and align all dialogue formatting.
- **Example**:
  > "« Je pars demain. » Il se leva. — Et moi ? dit-elle."
  > → Typographie : mélange guillemets et tirets dans le même dialogue
  > → Harmoniser : tout en tirets cadratins (convention par défaut)

### dialogue-format

- **Detects**: Dialogue lines not wrapped in markdown blockquote syntax. Tiret cadratin lines appearing as plain text instead of `> —`.
- **Works**: Every dialogue line (starting with tiret cadratin) is wrapped in a blockquote (`> —`). Consistent throughout.
- **Fails**: Some dialogue lines use `> —` and others are plain `— text`. Or dialogue is never in blockquotes.
- **Fix pattern**: Wrap all dialogue lines in blockquote syntax. Narration stays as plain paragraphs.
- **Example**:
  > `— Je pars demain.`
  > → Format : dialogue sans blockquote
  > → `> — Je pars demain.`

### french-spacing

- **Detects**: Missing or incorrect spaces around French punctuation. Non-breaking spaces before : ; ! ? and around guillemets. Thin non-breaking spaces where applicable.
- **Works**: Non-breaking spaces placed correctly before : ; ! ? and around guillemets. No breaking space where non-breaking is required. These are non-negotiable French typography standards.
- **Fails**: A colon without preceding non-breaking space. A question mark stuck to its word. Guillemets without internal spaces.
- **Fix pattern**: Add the correct space type. Non-breaking before double punctuation. Non-breaking inside guillemets.
- **Example**:
  > "Pourquoi? Il ne comprenait pas:c'était absurde."
  > → Espaces : manquantes avant "?" et avant ":"
  > → "Pourquoi ? Il ne comprenait pas : c'était absurde."

### formatting-consistency

- **Detects**: Inconsistent use of italics, bold, caps, or other formatting markers. Internal thoughts sometimes in italics, sometimes not. Chapter headings with varying formats. Scene breaks with different markers.
- **Works**: Formatting conventions are established and maintained throughout. Italics for thoughts (if that's the convention) — consistently. Chapter headings follow one format. Scene breaks use one marker.
- **Fails**: Internal thoughts are italicized in chapters 1-5 and not in chapters 6-10. Chapter headings alternate between numbered and named. Scene breaks use "***" and then "---".
- **Fix pattern**: Establish the convention from the dominant usage and align all occurrences.
- **Example**:
  > Ch.3 (thoughts in italics) ... Ch.8 (thoughts without italics, same narrative distance)
  > → Formatage : italique pour les pensées incohérent entre chapitres
  > → Fixer la convention (italique ou non) et appliquer uniformément
