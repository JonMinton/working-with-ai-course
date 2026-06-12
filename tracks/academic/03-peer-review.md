# A3. AI Peer Review

## The Adversarial Critique Pattern

One of the most powerful uses of AI in academic work: **using one AI to critique work produced with another**.

```
┌─────────────────────────────────────────────────────────────┐
│              ADVERSARIAL AI PEER REVIEW                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  AGENT A (e.g., Claude)          AGENT B (e.g., GPT)       │
│  ┌─────────────────┐             ┌─────────────────┐       │
│  │                 │             │                 │       │
│  │  Writes draft   │────────────▶│  Critiques:     │       │
│  │                 │             │  • Logic gaps   │       │
│  │                 │             │  • Weak claims  │       │
│  │                 │◀────────────│  • Missing refs │       │
│  │  Revises based  │             │  • Alt views    │       │
│  │  on critique    │             │                 │       │
│  └─────────────────┘             └─────────────────┘       │
│           │                                                 │
│           ▼                                                 │
│  ┌─────────────────┐                                       │
│  │     HUMAN       │                                       │
│  │                 │                                       │
│  │ • Adjudicates   │                                       │
│  │ • Final judgment│                                       │
│  │ • Quality call  │                                       │
│  └─────────────────┘                                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Why Different Model Families?

- Same model critiquing itself may share blind spots
- Different training data → different perspectives
- Cross-family review catches more issues
- Mimics actual peer review (different minds)

One caveat: different models are trained on overlapping data and can share blind spots too. Cross-model review reduces the risk of missed problems, but it does not eliminate it — which is one more reason the human stays in charge.

### The Human Role

AI critique is input, not judgment. You:
- Evaluate whether criticisms are valid
- Decide which to address
- Maintain scholarly responsibility
- Make final quality call

## Prompting for Critique

### The Critical Reviewer Prompt

> "Act as a critical peer reviewer for [journal/venue]. Review this [section type] and identify:
>
> 1. **Logical gaps:** Where does the argument skip steps?
> 2. **Unsupported claims:** What statements lack evidence?
> 3. **Alternative interpretations:** What other explanations exist for these findings?
> 4. **Missing literature:** What important perspectives aren't addressed?
> 5. **Methodological concerns:** What could a sceptical reviewer question?
>
> Be specific. Quote the text when identifying issues."

### Discipline-Specific Review

Tailor to your field:

**For empirical research:**
> "Review this Methods section as if you were Reviewer 2 (the tough one). Question:
> - Sample size justification
> - Control conditions
> - Confounds not addressed
> - Statistical approach appropriateness
> - Replicability concerns"

(If you're new to the term: Reviewer 2 is a long-running academic in-joke — the notoriously harsh anonymous reviewer that every author dreads.)

**For theoretical work:**
> "Review this argument as a philosopher would. Identify:
> - Unstated assumptions
> - Logical fallacies
> - Counterexamples not addressed
> - Conceptual ambiguities
> - Alternative frameworks"

**For literature reviews:**
> "Review this literature review for:
> - Gaps in coverage
> - Outdated perspectives
> - Over-reliance on particular sources
> - Balance of viewpoints
> - Synthesis vs. mere summary"

```
EXERCISE:
Write a critique prompt tailored to your discipline and current work. Include:
- The type of document being reviewed
- 5+ specific questions for the reviewer to address
- Instructions on how to format critique
```

## Running the Review Process

### Step 1: Draft with Agent A

Use one AI to help draft or refine a section.
Ensure citations are from your .bib.

### Step 2: Critique with Agent B

Switch to a different model family.
Provide the draft + critique prompt.

**Example switch:**
- Draft with one model family (e.g. Claude)
- Critique with another (e.g. GPT)

Ideally the two agents come from different model families. Either direction works.

### Step 3: Analyse Critiques

Review what Agent B identified:
- Which critiques are valid?
- Which are misunderstandings?
- Which reveal real weaknesses?
- Which are stylistic preferences?

### Step 4: Revise (Human or Agent A)

Address valid critiques:
- You can revise yourself
- Or prompt Agent A: "Address these specific criticisms: [list]"

### Step 5: Verify

Check that revisions actually address the issues.
Consider another round of critique if substantial changes.

```
QUIZ:
Agent B critiques your Methods section, saying your sample size is too small for the claimed statistical power. What do you do?

* Ignore it — the AI isn't a statistician
* Automatically add more participants to your description
*! Verify the calculation yourself, and either defend your choice or acknowledge the limitation
* Ask Agent A to argue against the critique

FEEDBACK: AI critique surfaces potential issues; you verify and make the judgment. If the critique is valid, address it honestly. If it's wrong, you should be able to articulate why.
```

## What to Ask the Critic

### For Logic and Argument

> "What claims in this text are not supported by the evidence provided?"
> "Where does this argument rely on unstated assumptions?"
> "What counterarguments should be addressed?"

### For Literature Coverage

> "What important perspectives are missing from this review?"
> "Which claims need additional citations?"
> "Are any sources over-relied upon?"

### For Methods

> "What methodological weaknesses would a sceptical reviewer identify?"
> "What alternative explanations for these results aren't addressed?"
> "What threats to validity exist?"

### For Writing Quality

> "Where is this text unclear or ambiguous?"
> "What jargon needs definition for a general academic audience?"
> "Where does the argument lose momentum?"

## Managing Critique Overload

AI critics can generate extensive feedback. Triage:

### Priority 1: Validity Threats
Issues that undermine the core contribution.
**Must address.**

### Priority 2: Logic Gaps
Missing steps that lose the reader.
**Should address.**

### Priority 3: Coverage Gaps
Missing literature or perspectives.
**Address if space allows.**

### Priority 4: Style
Writing quality, clarity improvements.
**Address in polish phase.**

### Priority 5: Preferences
Things that aren't wrong, just different.
**Ignore unless you agree.**

## Documenting AI Use

Academic norms increasingly require transparency about AI use.

### What to Document

- Which sections used AI assistance
- What kind of assistance (drafting, editing, critique)
- What models were used
- How outputs were verified

### Sample Disclosure

> "AI tools (e.g. Claude and GPT) were used in the preparation of this manuscript for: generating initial draft text for specific sections, critiquing drafts to identify weaknesses, and improving clarity. All AI-generated content was reviewed and substantially revised by the authors. All citations were verified against original sources. [Author] takes full responsibility for the final content."

### Where to Disclose

Check your target venue's policy:
- Some require disclosure in Methods
- Some in Acknowledgments
- Some have specific AI use statements
- Some prohibit certain uses

## Key Takeaways

- Adversarial review: one AI writes, another critiques
- Different model families catch different issues
- Human adjudicates — AI critique is input, not judgment
- Tailor critique prompts to your discipline
- Triage critiques by importance
- Document AI use transparently

---

Next: **A4. Reproducibility & Documentation** →
