# A4. Reproducibility & Documentation

## The Reproducibility Challenge

AI-assisted research introduces new reproducibility concerns:

- **Non-determinism:** Same prompt, different outputs
- **Model evolution:** The model you used today won't exist in two years
- **Opacity:** "I used AI to help" doesn't let others replicate your process
- **Versioning:** Which version of GPT-4? What temperature? What system prompt?

If a colleague or reviewer can't understand what you did with AI, they can't evaluate or replicate it.

## What to Document

### The Minimum Documentation Set

For any AI-assisted research task, record:

| Element | What to Capture | Why It Matters |
|---------|-----------------|----------------|
| **Model** | Name, version, provider | Models change; behaviour varies |
| **Timestamp** | When the interaction occurred | Models update frequently |
| **Prompt** | Exact text sent to AI | The "method" you used |
| **Parameters** | Temperature, max tokens, etc. | Affects output variability |
| **Output** | What AI returned | The data you worked with |
| **Your modifications** | How you changed AI output | Distinguishes AI from human contribution |

### The Extended Documentation Set

For high-stakes or publishable work, also capture:

- **System prompt** (if accessible)
- **Conversation context** (prior turns that influenced output)
- **Alternative outputs** (if you regenerated multiple times)
- **Selection criteria** (why you chose this output over alternatives)
- **Verification steps** (how you checked accuracy)

## Documentation Patterns

### Pattern 1: The Prompt Log

A structured record of AI interactions:

```markdown
## AI Interaction Log

### Session: Literature Theme Analysis
- **Date:** 2024-01-15
- **Model:** Claude 3 Sonnet (claude-3-sonnet-20240229)
- **Temperature:** Default (not specified)

#### Prompt 1
**Input:**
> Based on the following abstracts, identify common themes...
> [abstracts provided]

**Output:**
> The abstracts cluster around three main themes...

**Notes:** Output used as starting point for thematic analysis.
Themes were refined through manual review of full papers.
```

### Pattern 2: The Annotated Transcript

For complex multi-turn interactions:

```markdown
## Transcript: Methods Section Drafting

**Context:** Drafting participant description for Methods section.
**Model:** GPT-4 (gpt-4-0613)
**Date:** 2024-01-15

---

**[HUMAN]:** I need to describe our participant recruitment...

**[AI]:** Here's a draft of the participant section...

**[HUMAN - NOTE]:** AI's description was accurate for inclusion criteria
but missed exclusion criterion 3. Added manually.

**[HUMAN]:** The exclusion criteria are incomplete. We also excluded...

**[AI]:** Here's the revised version...

**[HUMAN - NOTE]:** This version used verbatim with minor edits for tense.
Final version in manuscript differs at lines 45-48.
```

### Pattern 3: The Diff Log

For editing and revision tasks:

```markdown
## AI-Assisted Revision Log

### Document: Discussion Section v2 → v3
### AI Used: Claude 3 Opus

**Change 1:**
- Original: "The results suggest..."
- AI suggestion: "The results demonstrate..."
- Final: "The results indicate..." (my modification — "demonstrate" too strong)

**Change 2:**
- Original: [paragraph on limitations]
- AI suggestion: [restructured paragraph]
- Final: AI version accepted with minor edits (added hedge in sentence 3)
```

```
EXERCISE:
You've used AI to help identify gaps in a literature review.

1. What minimum documentation would you need?
2. What would a reviewer need to evaluate your process?
3. How would you format this for a methods section?
```

## Storage and Organisation

### Folder Structure

```
project/
├── paper/
│   ├── manuscript.qmd
│   └── references.bib
├── ai-logs/
│   ├── 2024-01-15-theme-analysis.md
│   ├── 2024-01-18-methods-draft.md
│   └── 2024-01-20-discussion-revision.md
├── prompts/
│   ├── literature-synthesis.md
│   └── critique-request.md
└── README.md (describes AI use)
```

### What to Archive

For reproducibility, archive:

1. **Prompt templates** — The reusable prompts you developed
2. **Interaction logs** — Timestamped records of actual use
3. **Outputs** — Raw AI outputs before your modifications
4. **Final versions** — What actually went into the paper

Consider: Could someone reproduce your AI-assisted process from these files?

## Methods Section Reporting

### Current Norms (Evolving)

Reporting standards vary by venue. Check your target journal's policy. In absence of specific guidance:

**Minimal disclosure:**
> AI tools were used in the preparation of this manuscript.

**Standard disclosure:**
> AI tools (specifically, [model name]) were used to assist with [specific tasks]. All AI-generated content was reviewed and substantially revised by the authors.

**Detailed disclosure:**
> Claude 3 (Anthropic, claude-3-sonnet-20240229) was used to assist with literature synthesis and manuscript revision. Prompts and interaction logs are available in the supplementary materials. AI suggestions were evaluated against primary sources and modified as needed. The authors take full responsibility for the final content.

### What to Include

At minimum, disclose:
- That AI was used
- What tasks it assisted with
- That humans verified/revised the output
- Who takes responsibility for the content

Consider including:
- Which model(s) were used
- Availability of prompts/logs
- Verification procedures

```
QUIZ:
A journal asks you to describe AI use in your methods section. Which is most appropriate?

* "AI wrote the literature review"
* "No AI was used" (even though you used it for drafting)
*! "AI tools assisted with drafting; all content was verified against sources and substantially revised by the authors"
* "GPT-4 was used with temperature 0.7 and top_p 0.9"
FEEDBACK:Be honest about AI use, but frame it accurately — AI assisted, humans verified and take responsibility. Excessive technical detail (temperature, top_p) is usually unnecessary unless methodologically relevant.
```

## Verification Documentation

Document how you verified AI outputs:

### Citation Verification Log

```markdown
## Citation Verification

### Session: Literature Review Citations
### Verified by: [Your name]
### Date: 2024-01-16

| Citation | In .bib? | Exists? | Details correct? | Notes |
|----------|----------|---------|------------------|-------|
| @smith2023 | ✓ | ✓ | ✓ | Verified via DOI |
| @jones2022 | ✓ | ✓ | Year wrong (2021) | Fixed in .bib |
| @chen2024 | ✗ | ✗ | N/A | Hallucinated — removed |
```

### Fact-Check Log

```markdown
## Fact Verification

### Section: Background (paragraphs 2-3)
### Verified by: [Your name]

| Claim | Source | Status | Notes |
|-------|--------|--------|-------|
| "AI market $150B by 2025" | Needed verification | ✓ Verified | Gartner report, updated figure |
| "Transformers introduced 2017" | General knowledge | ✓ Correct | Vaswani et al. |
| "GPT-4 has 1T parameters" | AI generated | ✗ Unverified | Removed — OpenAI hasn't confirmed |
```

## Handling Non-Determinism

### The Regeneration Problem

If you regenerated AI output multiple times and picked the "best" one:

1. **Document it:** "Generated 3 versions, selected based on [criteria]"
2. **Archive alternatives:** Keep the versions you didn't use
3. **Justify selection:** Why was this one better?

### The Reproducibility Caveat

Be honest about what's reproducible:

> "Exact outputs may vary due to model non-determinism. The prompts and procedures are documented in Appendix B."

This is acceptable. Perfect reproducibility of AI outputs isn't possible — but reproducibility of your *process* is.

## Ethical Considerations

### Authorship and Attribution

AI cannot be an author (it can't take responsibility for content). Current consensus:
- Humans take authorship and responsibility
- AI use is disclosed in methods/acknowledgments
- Degree of AI contribution is described honestly

### Avoiding Misrepresentation

**Don't:**
- Claim AI-generated text as entirely your own
- Hide AI use when journals require disclosure
- Use AI to fabricate data or citations (obviously)
- Over-claim what AI contributed (also problematic)

**Do:**
- Disclose accurately
- Distinguish AI contribution from human contribution
- Take responsibility for verification
- Follow venue-specific policies

```
EXERCISE:
You used AI to help rewrite paragraphs for clarity in your discussion section.

Draft:
1. A methods section disclosure statement
2. An acknowledgments mention
3. A brief entry for your AI interaction log
```

## Long-Term Archival

### The Model Obsolescence Problem

The model you used will eventually:
- Be deprecated
- Change behaviour
- Become unavailable

**What this means:**
- Your exact process may not be replicable in 5 years
- But your documentation lets others understand what you did
- And apply equivalent methods with contemporary tools

### Archival Recommendations

1. **Use DOI-style versioning** where available (claude-3-sonnet-20240229)
2. **Timestamp everything** — dates matter for reproducibility
3. **Archive outputs, not just prompts** — the output is your data
4. **Use open formats** — Markdown, plain text, not proprietary formats
5. **Include in supplementary materials** — where journals allow

## Checklist: AI-Assisted Research Documentation

Before submission:

- [ ] AI use disclosed in methods/acknowledgments
- [ ] Models and versions documented
- [ ] Prompts/procedures available (supplementary or on request)
- [ ] Verification procedures described
- [ ] All citations verified against actual sources
- [ ] Human modifications distinguished from AI output
- [ ] Journal's AI policy checked and followed
- [ ] Authorship responsibility clear (humans, not AI)

## Key Takeaways

- AI-assisted research requires new documentation practices
- Capture: model, timestamp, prompt, parameters, output, modifications
- Create prompt logs and annotated transcripts for complex work
- Report AI use honestly in methods sections
- Document verification procedures — this is your quality control
- Archive for reproducibility of process, not exact outputs
- Follow evolving journal and venue policies
- Take responsibility — AI assists, humans author

---

Congratulations! You've completed the Academic Track.

Consider also:
- **Enterprise Track** — For AI governance context
- **Developer Track** — For building research tools
