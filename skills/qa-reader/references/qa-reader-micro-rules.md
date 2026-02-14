# Micro Rules — qa-reader

> Scope: micro
> Loaded when: always
> Evaluates: Sentence and paragraph level engagement — the reader's moment-to-moment experience
> Preferred output: inline

---

## Finding Axes

### hook

- **Detects**: First sentence of scene/chapter that fails to create a question, an image, or a voice. Openings that explain, set up context, describe weather, or orient before engaging.
- **Works**: The first sentence is an audition. It creates curiosity, plants an image, or establishes a voice the reader wants to follow. Not a gimmick — a promise.
- **Fails**: The scene opens with exposition, weather description, or neutral context-setting. Nothing pulls the reader forward. The first line could be cut without losing engagement.
- **Fix pattern**: Replace with a line that creates a question, plants a sensory image, or introduces a voice with attitude. Enter the scene at the point of interest.
- **Example**:
  > "Il faisait froid ce matin-là et le ciel était gris."
  > → Ouverture météo — aucune question, aucune tension, aucune voix
  > → Entrer par un geste, un détail étrange, ou une pensée qui accroche

### sentence-rhythm

- **Detects**: Monotone sentence length and structure. No variation between short and long. No fragments after complex sentences. Rhythm disconnected from content.
- **Works**: Short after long. Fragment after complex. Fast sentences for action, long for interiority, fragments for shock. The rhythm serves the content and keeps the reader's ear engaged.
- **Fails**: Five consecutive sentences of the same length. Action described in long, complex sentences. Introspection in choppy fragments. Rhythm works against content.
- **Fix pattern**: Map rhythm to content — shorten for speed, lengthen for depth, fragment for impact. Break the monotone.
- **Example**:
  > "Il courut dans le couloir qui menait à la salle principale où se trouvait la sortie de secours qu'il cherchait depuis le début."
  > → Phrase longue pour une action rapide — le rythme freine la scène
  > → Découper : phrases courtes, haletantes, qui miment la course

### density

- **Detects**: Filler sentences, throat-clearing paragraphs, sentences that repeat what the previous one said in different words. Content that can be removed without loss.
- **Works**: Every sentence earns its place. Each one advances the scene, deepens a character, or creates texture. Nothing redundant.
- **Fails**: A sentence restates the previous one. A paragraph establishes something already clear. Remove a sentence — nothing changes. That sentence shouldn't exist.
- **Fix pattern**: Cut. If the sentence adds nothing, delete it. If it adds something but weakly, merge with a stronger neighbor.
- **Example**:
  > "Le silence s'installa. Personne ne parlait. Un calme pesant régnait dans la pièce."
  > → Trois phrases pour une seule information — deux de trop
  > → Garder la plus physique, couper les deux autres

### sensory-clarity

- **Detects**: Scenes without sensory grounding. Abstract atmosphere ("the room was tense") instead of concrete detail. Missing physical reality.
- **Works**: The reader can see, hear, feel the scene. Grounded in specific sensory detail. At least two senses per scene anchor. The physical world exists.
- **Fails**: The scene happens in a void. No sound, no texture, no temperature. Characters interact in abstract space. Emotions are named but not felt through the body.
- **Fix pattern**: Add one specific sensory detail that grounds the scene. Anchor through what the POV character perceives first — hierarchy of senses reveals character.
- **Example**:
  > "La tension entre eux était devenue insupportable."
  > → Abstrait — rien de physique, rien que le lecteur puisse sentir
  > → Montrer la tension par un son, un geste, un objet déplacé

### dialogue-effect

- **Detects**: Dialogue without subtext. Characters saying exactly what they mean. No gap between words and intentions. Dialogue that only exchanges information.
- **Works**: Characters say one thing, mean another. Tension in the gap between words and intentions. Distinct voices. Dialogue advances the scene AND reveals character. This axis judges the EFFECT on the reader, not the technical format.
- **Fails**: Characters explain their feelings in dialogue. Two characters agree without friction. Every line delivers information with no undertow. The reader learns but doesn't feel.
- **Fix pattern**: Add what's unsaid. Give one character a hidden agenda. Make the surface conversation about one thing and the real conversation about another.
- **Example**:
  > "— Je suis en colère contre toi. — Je sais, et je suis désolé."
  > → Dialogue frontal — aucun sous-texte, rien entre les lignes
  > → Faire passer la colère par un sujet détourné, un refus, un silence

### word-precision

- **Detects**: Generic placeholders ("chose", "sentiment", "quelque chose"), approximate words where a specific word exists, adjective/adverb clutter where a precise noun/verb would suffice.
- **Works**: Specific, earned words. Each noun and verb carries weight. Adjectives only when they add what the noun alone can't. The right word, not the approximate word.
- **Fails**: "Il ressentit quelque chose" — what? "Un sentiment étrange" — which one? The text gestures toward meaning instead of nailing it.
- **Fix pattern**: Replace the generic with the specific. Name the thing. Find the verb that carries the meaning without an adverb. Kill the placeholder.
- **Example**:
  > "Il y avait quelque chose de bizarre dans son attitude."
  > → "Quelque chose de bizarre" — doublement vague, aucune précision
  > → Nommer : quel geste, quelle posture, quel décalage exactement
