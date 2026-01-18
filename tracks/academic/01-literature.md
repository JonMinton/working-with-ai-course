# A1. Literature Workflows

## The Citation Integrity Problem

AI can hallucinate citations. It might generate:
- Fake papers that don't exist
- Wrong authors for real papers
- Incorrect publication details
- Plausible-sounding but invented references

In academic work, this is catastrophic. A single fabricated citation can destroy credibility.

**The solution:** Treat your .bib file as the **single source of truth**. AI can only reference what exists in your curated bibliography.

## The .bib-First Workflow

```
┌─────────────────────────────────────────────────────────────┐
│                   LITERATURE WORKFLOW                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. HUMAN: Identify relevant literature                     │
│     └── Search databases, follow citations, expert recs     │
│                                                             │
│  2. HUMAN: Curate into .bib file                           │
│     └── Verify each entry exists and is correct            │
│                                                             │
│  3. AI: Works ONLY with provided .bib                       │
│     └── Summarise, compare, find connections               │
│                                                             │
│  4. HUMAN: Verify all citations trace to .bib              │
│     └── Any citation not in .bib is suspect                │
│                                                             │
│  5. OUTPUT: .qmd files with proper @citation keys           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Key Principle

> **AI never invents references. All citations come from human-curated .bib.**

If AI suggests a reference, ask: "Is this in my .bib?" If not, verify it exists before adding.

## Building Your .bib File

### Sources for References

| Source | How to Export |
|--------|---------------|
| Google Scholar | Click cite → BibTeX |
| Zotero | Right-click → Export as BibTeX |
| Mendeley | File → Export → BibTeX |
| Publisher sites | Usually "Cite" or "Export" button |
| CrossRef | DOI lookup → BibTeX |

### .bib Entry Structure

```bibtex
@article{smith2023framework,
  author = {Smith, Jane and Jones, Bob},
  title = {A Framework for Understanding AI Collaboration},
  journal = {Journal of AI Studies},
  year = {2023},
  volume = {15},
  number = {3},
  pages = {112--145},
  doi = {10.1234/jais.2023.001}
}
```

Key fields:
- **Unique key:** `smith2023framework` — used for @citations
- **Author:** In "Last, First and Last, First" format
- **Year:** Publication year
- **DOI:** If available, aids verification

### Verification Checklist

Before adding to .bib:
- [ ] Paper exists (found via DOI, URL, or database)
- [ ] Authors are correct
- [ ] Year is correct
- [ ] Journal/venue is correct
- [ ] BibTeX key is unique and meaningful

```
EXERCISE:
You're writing a literature review. AI suggests: "According to Chen et al. (2022), transformer architectures improve..."

1. How do you verify this reference?
2. What do you do if it doesn't exist?
3. What do you do if it exists but with different details?
```

## AI-Assisted Literature Tasks

### What AI Can Do Well

| Task | How to Use AI | Verification Needed |
|------|---------------|---------------------|
| **Summarise a paper** | Provide full text or abstract | Check summary accuracy |
| **Compare papers** | Provide both texts + your .bib | Ensure comparisons are fair |
| **Find themes** | Provide collection of abstracts | Verify themes match content |
| **Draft lit review sections** | Provide .bib + your outline | Check every @citation |
| **Suggest search terms** | Describe your topic | Use terms to search yourself |

### What AI Cannot Do Reliably

| Task | Why It's Risky |
|------|----------------|
| **Find new papers** | May hallucinate citations |
| **Cite from memory** | Training data citations may be wrong |
| **Assess paper quality** | Can't verify methodology |
| **Determine novelty** | Doesn't know all literature |

## Prompting for Literature Work

### Providing Context

**Bad prompt:**
> "What does the literature say about AI in education?"

**Good prompt:**
> "Based on the following abstracts from my .bib file, summarise the main themes in research on AI in education. Only cite papers I've provided using their @keys."
> [Paste abstracts with their keys]

### Enforcing .bib Discipline

Include in your prompts:
> "Only cite sources I have provided. Use @citationkey format. Do not invent any references."

### Example Workflow

1. Export relevant entries from your .bib
2. Include them in your prompt context
3. Ask AI to work with those sources
4. Verify every @citation in the output maps to your .bib

```
QUIZ:
AI drafts a paragraph with five citations. Three use @keys from your .bib, two use keys you don't recognise. What do you do?

* Accept it — AI probably knows more papers
* Reject everything — AI can't be trusted
*! Keep the three verified citations, investigate the two unknown ones before including them
* Remove all citations to be safe
FEEDBACK:Verified citations are valuable. Unknown citations need verification — they might be real papers (add to .bib after verifying) or hallucinations (remove).
```

## Organising Literature with AI

### Thematic Organisation

Prompt:
> "Given these paper abstracts, suggest a thematic organisation for a literature review. Group papers by theme and suggest section headings."

Then: Use the organisation as a starting point, refine based on your knowledge.

### Gap Analysis

Prompt:
> "Based on these papers, what topics in [your field] appear under-represented? What questions aren't addressed?"

Then: Verify gaps by searching databases — AI might not know about papers outside the provided set.

### Connection Finding

Prompt:
> "What connections or contradictions exist between [Paper A] and [Paper B]? Quote specific passages."

Then: Verify quotes, check context, ensure fair representation.

## Key Takeaways

- AI hallucinates citations — your .bib is the source of truth
- Human finds and verifies; AI works with curated collection
- Always include citation keys with source material
- Verify every @citation in AI output maps to your .bib
- Use AI for synthesis and organisation, not discovery
- When in doubt, check the original source

---

Next: **A2. Modular Academic Writing** →
