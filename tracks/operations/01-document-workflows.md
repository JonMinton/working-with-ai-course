# O1. Document Workflows

## The Daily Reality

Most knowledge work involves documents:
- Drafting emails, reports, proposals
- Summarising meetings, articles, data
- Editing for clarity, tone, length
- Formatting and reformatting
- Translating between contexts and audiences

AI can help with all of this — but the skill is knowing when and how.

## Drafting Patterns

### Pattern 1: The Skeleton Draft

Start with structure, fill in later:

> "Create an outline for a project proposal with these sections: Executive Summary, Problem Statement, Proposed Solution, Timeline, Budget, Risks. Just headers and 1-sentence placeholders for now."

Then expand section by section. This keeps you in control of structure.

### Pattern 2: The Brain Dump Draft

Pour out ideas, let AI organise:

> "Here are my rough notes from the meeting: [paste messy notes]. Turn this into a structured summary with clear action items."

Good for when you have content but not coherence.

### Pattern 3: The Template Draft

Use proven structures:

> "Write a [type of document] following this template:
> - Opening: [structure]
> - Body: [structure]
> - Close: [structure]"

Templates reduce AI's creative latitude — which is often what you want for routine documents.

```
QUIZ:
You need to write a project status update. You know the key points but don't have time to write it properly. Which approach is most efficient?

* Write it yourself — AI will take longer to explain
*! Give AI your bullet points and ask it to expand into professional prose
* Ask AI to write a generic status update and edit heavily
* Skip the update this week

FEEDBACK: When you have the content but need professional prose, giving AI your key points to expand is usually the fastest path to a good result.
```

## Summarisation Patterns

### Know Your Summary Type

Different purposes need different summaries:

| Type | Length | Focus | Example Use |
|------|--------|-------|-------------|
| **TL;DR** | 1-2 sentences | Core takeaway | Email preview |
| **Executive summary** | 1 paragraph | Key points + implications | Leadership briefing |
| **Detailed summary** | 1 page | Comprehensive coverage | Reference document |
| **Action summary** | Bullet list | Decisions + next steps | Meeting follow-up |

Always specify which you need:

> "Summarise this 20-page report as:
> 1. A 2-sentence TL;DR
> 2. A 5-bullet executive summary
> 3. A list of action items with owners"

### Summarising for Different Audiences

The same content needs different summaries for different readers:

> "Summarise this technical analysis for:
> 1. The engineering team (technical details matter)
> 2. The executive sponsor (business impact matters)
> 3. The client (benefits and timeline matter)"

Specify the audience, get a relevant summary.

### The Verification Problem

AI summaries can miss important details or misrepresent content. Always:
- Scan the original for key points
- Check that nothing important was omitted
- Verify any numbers or specific claims

```
EXERCISE:
Take a recent long email thread or document. Ask AI to produce:
1. A TL;DR (2 sentences)
2. An action-focused summary (bullet list)
3. A summary for someone unfamiliar with the context

Compare: What did each version emphasise? What got left out?
```

## Editing Patterns

### Clarity Editing

> "Make this paragraph clearer. Simplify complex sentences, remove jargon, keep the same meaning."

Specify what "clear" means for your context.

### Tone Editing

> "Adjust the tone of this email from 'frustrated' to 'professional but firm.' Keep the same requests."

Be specific about the direction:
- Formal ↔ Casual
- Direct ↔ Diplomatic
- Urgent ↔ Routine
- Confident ↔ Tentative

### Length Editing

> "Reduce this from 500 words to 200 words. Keep the three main points; cut the examples."

Or the reverse:

> "Expand this bullet list into full paragraphs. Add context and explanation, but don't add new information."

### Structure Editing

> "Reorganise this document. Currently it's chronological — make it problem-solution-result instead."

AI is good at restructuring once you specify the target structure.

## Email Patterns

### The Reply Helper

> "Here's an email I received: [paste email]
>
> Draft a reply that:
> - Confirms the meeting time
> - Asks for the agenda in advance
> - Notes I'll be 10 minutes late
> - Keeps it brief and professional"

Bullet points in, prose out.

### The Difficult Email

> "I need to decline this request without damaging the relationship. The reasons are [X, Y, Z] but I don't want to go into detail. Draft something diplomatic."

AI can help navigate tricky communication — but always review carefully.

**Warning:** Never send an AI-drafted email without reading it through first — you are responsible for every word that goes out under your name.

### The Follow-Up Tracker

> "Here are 5 emails I'm waiting on responses to. Draft brief, polite follow-ups for each. Reference the original topic and make it easy to reply."

Batch processing for efficiency.

```
QUIZ:
You need to send a difficult email declining a request from a senior colleague. What's the safest approach?

* Let AI write it and send directly — saves time
* Write it yourself — too sensitive for AI
*! Have AI draft it, then carefully review and edit before sending
* Avoid email and have the conversation in person

FEEDBACK: AI can help draft difficult communications, but sensitive emails need careful human review. The stakes are too high for unreviewed AI output.
```

## Meeting Documentation

### Before: Agenda Creation

> "I'm meeting with [person/team] to discuss [topic]. Draft an agenda that:
> - Covers the key decisions we need to make
> - Allocates time appropriately (1 hour total)
> - Starts with context-setting, ends with action items"

### During: Real-Time Notes

If your tool supports it, AI can transcribe and structure notes in real-time.

If not, take rough notes and process after:

> "Here are my raw meeting notes. Turn them into structured minutes with:
> - Attendees
> - Key discussion points
> - Decisions made
> - Action items (who, what, when)"

### After: Follow-Up Communication

> "Based on these meeting notes, draft a follow-up email that:
> - Thanks attendees
> - Summarises key decisions
> - Lists action items with owners
> - Confirms next meeting"

## Format Conversion

### Between Document Types

> "Convert this Word document content into:
> 1. A PowerPoint outline (one slide per section)
> 2. A bulleted brief (one page)
> 3. An FAQ format"

### Between Audiences

> "Rewrite this technical documentation for:
> 1. A non-technical stakeholder
> 2. A new team member
> 3. An external client"

### Between Tones

> "Convert this internal casual Slack message into a formal external email."

## Building Document Templates

For repeated document types, create templates:

```markdown
# [Document Type] Template

## Purpose
What this document is for

## Structure
1. Section 1: [what goes here]
2. Section 2: [what goes here]
3. Section 3: [what goes here]

## Tone
[Formal/casual, audience assumptions]

## Length
[Target word count or page count]

## Example
[A good example of this document type]
```

Then use: "Write a [document type] using this template: [paste template]"

## Key Takeaways

- Drafting patterns: skeleton (structure first), brain dump (organise chaos), template (proven structures)
- Specify summary type: TL;DR, executive, detailed, action-focused
- Always verify AI summaries against original content
- Editing: clarity, tone, length, structure — be specific about direction
- Email: use AI for drafting, always review before sending (especially sensitive)
- Meeting flow: agenda → notes → follow-up
- Format conversion: AI excels at reorganising content for different contexts
- Build templates for repeated document types

> **📚 Further Reading**
> For guidance on deploying AI in enterprise document workflows, see **Microsoft 365 Copilot training** in **Resources & Further Reading**. For real-world examples of organisations transforming operations with agentic AI, see the Goldman Sachs example on the **Case Studies** page (a separate page in the course navigation).

---

Next: **O2. Data Wrangling** →
