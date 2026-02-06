# L1. Strategic Assessment

## The Capability-Reliability Gap

Most AI conversations skip a critical distinction: what AI *can do* vs. what you can *depend on it doing*.

A language model can generate remarkably coherent text on almost any topic. It can also hallucinate with conviction, confabulate sources, or miss the obvious. Both of these are true simultaneously.

> "We've bought AI tools, but 30% of what they produce we discard or rewrite. That's not productivity — it's theatre."

This tension defines the leadership challenge: distinguishing genuine value creation from hype-driven projects that consume budget without return.

## The Value Creation Framework

Not every task is a good fit for AI. Good strategic assessment asks: *where does AI create asymmetric value?*

### Three Zones of AI Utility

| Zone | Characteristics | Example | Leader's Role |
|------|---|---|---|
| **High Confidence** | Routine, repetitive, clearly defined output, easy to verify | Categorising customer inquiries, extracting structured data from documents | Deploy with confidence, automate approval workflows |
| **Medium Confidence** | Semi-structured, human judgment required, output needs review | Drafting policy documents, brainstorming campaign angles, summarising research | Deploy with review gates, invest in evaluation processes |
| **Low Confidence** | Novel problems, high stakes, hard to verify, creative judgment central | Strategic decisions, novel product design, hiring decisions | Pilot only, human retains full authority, use as input not output |

**Questions to ask your teams:**
- Which tasks in your function are genuinely routine?
- Which ones are "routine-feeling but actually require judgment"?
- For each high-confidence use case, what's the actual time saving? (Not estimated — measured.)

```
QUIZ:
Your marketing team wants to use AI for: "Writing product descriptions from specifications." What's the main risk?

* AI can't write compelling marketing copy
*! Product descriptions need brand voice and benefit framing — the AI might be technically accurate but miss what makes your product unique
* AI is too fast and will make the team redundant
* Marketing is too creative for any AI use

FEEDBACK: AI works best when the output is directly verifiable or when human judgment is applied afterward. Brand voice isn't verifiable by the AI itself; it requires human judgment.
```

## Avoiding "AI Washing"

AI washing occurs when organisations announce AI adoption to satisfy investor or board expectations, without genuine business logic.

### Symptoms of AI Washing

- "We're using AI" is announced before *what* problem is solved
- No clear metrics for success (time saved, quality improved, cost reduced)
- The AI tool replaces actual process improvement conversations
- Vendors are selected based on brand, not capability fit
- Team members aren't trained on when to trust vs. verify outputs
- Budget is assigned to "AI initiatives" without connected ROI

### The Strategic Assessment Discipline

Before any deployment, document:

```
USE CASE: [Name]

CURRENT STATE:
- Time per instance: [X minutes/hours]
- Volume: [Y instances per month/year]
- Cost of error: [£/reputational/other]
- Current process: [brief description]

AI CAPABILITY:
- What specifically will AI do? [Not "help with" — *exactly what*]
- Who verifies/reviews outputs? [Must be named, not "someone"]
- When would the AI output be wrong? [Specific failure modes]

SUCCESS METRICS:
- Time saved per instance: [measured, not estimated]
- Quality maintained or improved: [specific measure]
- Cost change: [actual, not theoretical]

ROLLBACK PLAN:
- If AI underperforms, what reverts?
- How quickly can you go back?

TIMELINE:
- Pilot: [dates]
- Measurement period: [dates]
- Go/no-go decision: [date]
```

## High-Value Use Case Identification

Where does AI create *asymmetric* value — disproportionate impact for relatively modest investment?

### Look for These Patterns

**Volume × Routine:** Tasks done frequently with predictable outcomes
- Customer service categorisation
- Document intake and field extraction
- Repetitive data transformation
- Meeting note standardisation

**Gatekeeping:** Tasks that slow down other work
- Proposal reviews and feedback
- First-pass analysis before expert review
- Summarisation of lengthy inputs
- Initial screening and triage

**Context synthesis:** Pulling together information someone needs
- Briefing documents from multiple sources
- Competitive analysis summaries
- Regulatory update compilation
- Knowledge base queries

**Quality improvement:** Where AI helps humans do better work
- Proofreading and clarity feedback
- Research literature synthesis
- Scenario planning (exploring more cases than humans would)
- Bias-checking on important decisions

```
EXERCISE:
Map your organisation's workflows:

1. List 5–10 common tasks in your domain that take significant time
2. For each, estimate: frequency, duration, error cost, skill required
3. Assess which have the characteristics above (routine, gatekeeping, synthesis, quality improvement)
4. Pick the top 2 that seem highest-value and lowest-risk
5. Document your strategic assessment for each (see template above)
```

## Common Pitfalls and How Leaders Prevent Them

### Pitfall 1: Premature Scaling

**The trap:** Successful pilot on 50 cases → immediate rollout to 5,000 cases → discovers AI underperforms at scale.

**Why it happens:**
- Pilot team is motivated and careful (they review everything)
- Real scale has lower discipline (people get faster, lazier)
- Edge cases appear at volume that weren't visible in pilot

**How to prevent it:**
- Measure pilot quality rigorously; don't rely on "feels good"
- Run shadow mode: AI outputs in parallel with human process for longer than you think necessary
- Establish explicit quality gates (% of outputs requiring human correction, time to review)
- Only scale when quality gates are met at 10× the pilot volume

### Pitfall 2: Ignoring Change Management

**The trap:** "We have a great AI tool" → people don't use it, or misuse it → tool sits unused while team does work manually.

**Why it happens:**
- Tool requires changing established habits
- People distrust AI; they've been burned before
- Tool solves a technical problem but creates a human one (now who decides which AI suggestion to use?)

**How to prevent it:**
- Involve the team *during* selection, not after
- Train explicitly on *when not* to trust the tool
- Build in friction for the wrong path (make the old way harder than the new way)
- Assign clear ownership: "This person decides whether to accept AI recommendations"
- Measure adoption, not just tool capability

### Pitfall 3: Wrong Vendor or Tool

**The trap:** Choose tool based on brand or demo → it underperforms on your specific data/use case → sunk cost keeps it in place longer than it should stay.

**How to prevent it:**
- Require vendors to prove capability on your data (or representative data) before purchase
- Insist on a genuine pilot period, not just "30-day free trial then buy"
- Have an explicit go/no-go decision date
- Never let a pilot become permanent due to inertia
- Plan the exit from day one (data portability, API access, export capability)

### Pitfall 4: Misaligned Expectations

**The trap:** Board expects 50% time saving, team discovers 15%, budget allocated based on 50% saving.

**How to prevent it:**
- Communicate *capability*, not fantasy (AI can help with X, with Y level of human review needed)
- Show the measurement process to stakeholders upfront
- Define success before pilot, not after
- Be willing to say "this particular use case isn't a good fit"

## Risk-Adjusted ROI Framing

Leaders think in trade-offs. Use this framing when evaluating AI:

| Dimension | Conservative Estimate | Realistic Estimate | Optimistic Estimate |
|-----------|---|---|---|
| **Time saved per instance** | 25% | 40% | 60% |
| **% of outputs needing rework** | 30% | 15% | 5% |
| **Adoption rate in team** | 40% | 60% | 80% |
| **Cost of tool + training + oversight** | £[X] | £[X] | £[X] |
| **Net benefit (conservative)** | 25% × (1 − 30%) × 40% × £volume − cost | ... | ... |

Most AI ROI discussions jump to optimistic. Force the conservative calculation and ask: *is it still worth doing?*

If yes, you have margin for error. If no, you might be AI washing.

```
QUIZ:
A vendor claims their AI tool will save 60% of customer service time. You should:

* Accept the claim and begin implementation
*! Challenge it with: "Show us your data, what % of outputs actually need human correction, and who defines success?"
* Ask for a reference customer
* Require a 6-month pilot before deciding

FEEDBACK: All of these are reasonable, but the most important step is making your success criteria explicit and measurable before you decide. Vendor claims should inform, not determine, your assessment.
```

## Key Takeaways

- Distinguish between capability and reliability: AI can do something ≠ you can depend on it
- Map use cases into high/medium/low confidence zones based on routine nature and verification difficulty
- Avoid AI washing by defining success metrics *before* implementation
- Premature scaling, poor change management, and misaligned expectations are the main failure modes
- Use risk-adjusted ROI framing (conservative, realistic, optimistic) to ground discussions
- Measure pilots rigorously and be willing to say no to deployments that don't deliver

---

Next: **L2. Building AI-Ready Teams** →
