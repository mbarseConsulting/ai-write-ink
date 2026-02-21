# story-arch — Structure Rules

> Loaded by: story-arch in `--report` mode for any synopsis or outline
> Scope: macro structure — acts, inciting incident, midpoint, central conflict, thematic throughline, narrative promises, reversals
> Default output: Diagnostic

---

## Axes

### act-breaks

**What it looks at:** Position of act breaks. Timing of the inciting incident. Quality of act transitions.

**Failure modes:**
- Inciting incident arrives too late (after 25% of the narrative)
- Act transitions don't mark genuine reversals — mere event accumulation
- Act 2 lacks a midpoint split that reorients the protagonist's strategy
- Act 3 is not triggered by the protagonist's lowest point

**States:**
- `solid` — breaks at the right positions, marking genuine reversals
- `misplaced` — breaks exist but at the wrong moment
- `absent` — acts are not structurally distinguishable

**Default sev:** MAJ

---

### midpoint

**What it looks at:** What changes at the structural center. Whether it genuinely reverses the dynamic.

**Failure modes:**
- Midpoint is an action peak without a change in the protagonist's strategy
- Midpoint doesn't reverse the power balance or the protagonist's perception
- False peak: things improve superficially before declining, without a genuine intermediate transformation

**States:**
- `reversing` — genuinely changes the narrative dynamic
- `weak` — action peak without change of direction
- `absent` — no structural pivot at the center

**Default sev:** MAJ

---

### central-conflict

**What it looks at:** The protagonist's external desire. Its clarity. Its persistence across acts.

**Failure modes:**
- External desire shifts between acts without narrative justification
- Central conflict is vague or multiple (protagonist wants A then B then C)
- Antagonists / obstacles don't directly oppose the established desire

**States:**
- `clear and persistent` — established early, maintained, everything opposes it
- `vague` — present but insufficiently defined
- `absent` — protagonist reacts to events without a driving desire

**Default sev:** BLK

---

### thematic-throughline

**What it looks at:** Presence of the theme in major structural beats, not just subtext.

**Failure modes:**
- Theme is declared in dialogue but invisible in structural choices
- Major beats (inciting incident, midpoint, climax) don't crystallize the theme
- Theme shifts or dilutes across acts

**States:**
- `visible and anchored` — present in the structural beats
- `present but passive` — declared, not structured
- `absent` — no identifiable thematic thread

**Default sev:** MAJ

---

### promise-delivery

**What it looks at:** What chapter 1 / the opening promises. What the ending delivers or betrays.

**Failure modes:**
- Genre promise (thriller = tension, romance = emotional resolution) is not honored
- Act 1 establishes a tone / style the climax abandons
- Resolution of the central conflict doesn't flow from elements established in the opening

**States:**
- `honored` — the ending delivers what the opening promised
- `partial` — some promises kept, others betrayed
- `betrayed` — the ending contradicts the structural promises of the opening

**Default sev:** BLK

---

### reversal-credibility

**What it looks at:** Whether turning points are prepared or pulled from nowhere.

**Failure modes:**
- A major reversal arrives without setup in the preceding acts
- Twists depend on information withheld from the reader without narrative logic
- Setup-to-payoff ratio is unbalanced: absent setup or disproportionate payoff

**States:**
- `prepared` — reversal elements are established beforehand
- `partially prepared` — reversal has grounding but insufficient
- `pulled from nowhere` — no identifiable setup

**Default sev:** MAJ

---

## Loading rules

- Always loaded in `--report` mode when a synopsis or outline is provided.
- Can operate without arc-rules if no arc material is provided.
- Priority: `central-conflict` and `promise-delivery` — if both are absent, everything else is secondary.
