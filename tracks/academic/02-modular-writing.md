# A2. Modular Academic Writing

## Why Modularity?

Long documents are hard to manage — for humans and for AI:

| Problem | With Monolithic Documents | With Modular Approach |
|---------|--------------------------|----------------------|
| Context window limits | Can't fit whole thesis | Each section fits |
| Focused work | Tempting to sprawl | Clear boundaries |
| Version control | Hard to see what changed | Changes isolated |
| Collaboration | Merge conflicts | Work on different files |
| AI assistance | "Work on my thesis" is vague | "Work on Methods section" is clear |

## The .qmd Architecture

Quarto (.qmd) files are Markdown with academic superpowers:
- Citations with @keys
- Cross-references
- Equations
- Figures with captions
- Render to PDF, HTML, DOCX

### Project Structure

```
thesis/
├── _quarto.yml          # Project configuration
├── references.bib       # Single source of truth for citations
├── index.qmd            # Title page, abstract
├── 01-introduction.qmd  # Chapter 1
├── 02-literature.qmd    # Chapter 2
├── 03-methods.qmd       # Chapter 3
├── 04-results.qmd       # Chapter 4
├── 05-discussion.qmd    # Chapter 5
├── 06-conclusion.qmd    # Chapter 6
└── appendices/
    ├── a-supplementary.qmd
    └── b-code.qmd
```

### _quarto.yml Configuration

```yaml
project:
  type: book

book:
  title: "Your Thesis Title"
  author: "Your Name"
  chapters:
    - index.qmd
    - 01-introduction.qmd
    - 02-literature.qmd
    - 03-methods.qmd
    - 04-results.qmd
    - 05-discussion.qmd
    - 06-conclusion.qmd
    - appendices/a-supplementary.qmd

bibliography: references.bib
csl: apa.csl  # Citation style
```

### .qmd File Template

```markdown
# Methods {#sec-methods}

## Participants

Description of participants...

As shown by @smith2023framework, this approach...

## Procedure

The procedure followed @jones2022protocol with modifications.

## Analysis

We used the method described in @sec-literature to analyse...

See @fig-procedure for the flowchart.

![Procedure flowchart](figures/procedure.png){#fig-procedure}
```

## AI-Assisted Section Writing

### Providing Focused Context

When working on one section, provide:
1. The section's current content
2. Relevant .bib entries for that section
3. Brief context about adjacent sections
4. Your outline/goals for this section

**Prompt template:**
```
I'm working on the Methods section of my thesis on [topic].

Current draft:
[paste current content]

Relevant references from my .bib:
[paste relevant entries]

Context:
- Introduction established: [brief summary]
- This section needs to: [goals]
- Discussion will cover: [brief preview]

Please help me [specific task].
Only cite references I've provided using @keys.
```

### Section-Specific Tasks

| Section | AI Can Help With |
|---------|------------------|
| **Introduction** | Framing, context setting, research question clarity |
| **Literature Review** | Organisation, synthesis, identifying themes |
| **Methods** | Clarity, completeness, standard phrasing |
| **Results** | Description structure, statistical phrasing |
| **Discussion** | Connecting to literature, limitations |
| **Conclusion** | Summarisation, implications |

```
EXERCISE:
You're working on a Discussion section. You have:
- Results showing unexpected finding X
- Three papers in your .bib that might explain X
- A need to acknowledge limitations

Write a prompt for AI assistance that:
1. Provides appropriate context
2. Constrains to your .bib
3. Asks for specific help
```

## Maintaining Coherence

### The Coherence Challenge

Modular writing risks incoherence:
- Sections contradict each other
- Terminology varies
- Arguments don't connect
- References inconsistent

### Solutions

**1. Master Outline Document**

Keep a separate document with:
- Key terms and their definitions
- Central argument thread
- How sections connect
- Consistent phrasing for recurring concepts

Include this in AI prompts for any section.

**2. Section Summaries**

At the end of each .qmd file, add a comment:
```markdown
<!--
SECTION SUMMARY (for coherence):
- Main argument: [X]
- Key terms used: [list]
- Connects to: [sections]
- Open threads: [what Discussion should address]
-->
```

**3. Cross-Reference Verification**

After AI-assisted writing:
- Check all @sec- references exist
- Check all @fig- and @tbl- references exist
- Verify forward references don't create confusion

### Coherence Check Prompt

After completing a section:
> "Review this Methods section for internal coherence. Check:
> - Consistent terminology
> - Logical flow between subsections
> - All procedures adequately explained
> - Any gaps that would confuse a reader"

## Version Control

### Git for Academic Writing

Track changes with git:
```bash
git add 03-methods.qmd
git commit -m "Expand participant description based on reviewer feedback"
```

**Benefits:**
- See what changed when
- Revert if needed
- Branch for experiments
- Collaborate without conflicts

### Meaningful Commits

**Bad commits:**
- "Updated file"
- "Changes"
- "WIP"

**Good commits:**
- "Add power analysis to Methods"
- "Revise Discussion to address Reviewer 2 concern"
- "Update citations with 2024 publications"

## Rendering and Output

### Build Commands

```bash
# Render to PDF
quarto render --to pdf

# Render to DOCX (for supervisors who want Word)
quarto render --to docx

# Render to HTML (for web sharing)
quarto render --to html
```

### Managing Outputs

Keep outputs out of version control:
```
# .gitignore
_book/
*.pdf
*.docx
```

Regenerate when needed — source .qmd files are the truth.

## Key Takeaways

- Modular .qmd files make AI assistance more tractable
- One shared .bib file for the whole project
- Provide focused context when working on each section
- Maintain coherence with master outlines and section summaries
- Use version control (git) to track changes
- Render to multiple formats from single source

---

Next: **A3. AI Peer Review** →
