# edit-ai-fr — Spec

## Meta

| Field       | Value                                      |
| ----------- | ------------------------------------------ |
| Skill       | `edit-ai-fr`                               |
| Version     | `v2`                                       |
| Last tested | `—`                                        |
| Depends on  | `none (loads agent-edit-ai-fr persona)`    |

## Scenarios

### S01 — AI pattern detection in French prose

**Intent:** Verify the skill identifies and removes AI-generated French patterns.

**Context:** User pastes French prose containing known AI markers.

**Input:**

```
/edit-ai-fr
[paste French prose containing AI markers: "en effet", "notamment", "il est important de noter", "force est de constater", "il convient de souligner"]
```

**Expected behavior:**

- [ ] Loads agent-edit-ai-fr persona before analysis
- [ ] Identifies each AI marker with its location in the text
- [ ] Proposes removal or natural replacement for each marker
- [ ] Preserves the author's voice while eliminating mechanical patterns

**Expected output:**

- CONTAINS: identified AI markers with their locations
- CONTAINS: proposed replacement or removal for each marker
- STRUCTURE: findings are itemized, not a bulk rewrite

**Anti-patterns (must NOT happen):**

- [ ] Misses obvious AI markers
- [ ] Replaces AI patterns with other AI patterns
- [ ] Strips all formal French, confusing register with AI generation

---

### S02 — French dialogue format correction

**Intent:** Verify the skill fixes French dialogue punctuation conventions.

**Context:** User pastes French dialogue with English-style formatting.

**Input:**

```
/edit-ai-fr
[paste French dialogue with incorrect formatting — English-style quotes instead of guillemets, missing tirets for turn-taking]
```

**Expected behavior:**

- [ ] Detects incorrect dialogue formatting
- [ ] Applies French conventions (guillemets for first speaker, tirets for exchanges)
- [ ] Fixes punctuation spacing inside dialogue (espace insecable before !, ?, ;, :)
- [ ] Preserves dialogue content and voice

**Expected output:**

- CONTAINS: corrected dialogue with proper French formatting
- CONTAINS: identification of each formatting issue found
- STRUCTURE: corrections preserve original dialogue content

**Anti-patterns (must NOT happen):**

- [ ] Alters dialogue content while fixing format
- [ ] Applies English punctuation conventions
- [ ] Misses inconsistent formatting within the same passage

---

### S03 — Subtle grammar corrections

**Intent:** Verify the skill corrects French grammar without changing voice.

**Context:** User pastes French text with subtle grammatical errors.

**Input:**

```
/edit-ai-fr
[paste French text with subtle errors: accord du participe passe, subjonctif manquant, concordance des temps]
```

**Expected behavior:**

- [ ] Catches grammar errors (participle agreement, subjunctive, tense concordance)
- [ ] Corrects without altering the author's sentence structure or voice
- [ ] Reports each correction with the rule applied

**Expected output:**

- CONTAINS: each correction paired with the grammar rule applied
- STRUCTURE: corrections reported individually, not as a bulk rewrite

**Anti-patterns (must NOT happen):**

- [ ] Rewrites sentences beyond the grammar fix
- [ ] Introduces new errors while correcting existing ones
- [ ] Misses the grammar errors and only flags style

---

## Edge Cases

### E01 — Already clean French prose

**Intent:** Verify the skill handles clean text without forcing changes.

**Input:**

```
/edit-ai-fr
[paste well-written French prose with no AI markers or grammar errors]
```

**Expected behavior:**

- [ ] Reports minimal or no findings
- [ ] Does not force unnecessary changes
- [ ] Confirms the text is clean rather than inventing problems
- [ ] May note minor stylistic observations without requiring action

**Expected output:**

- CONTAINS: confirmation that text is clean or near-clean

---

## Regression Log

| Date       | Runner  | Scope | Result | Failures         |
| ---------- | ------- | ----- | ------ | ---------------- |
