# L2. Building AI-Ready Teams

## The Skills Gap

When organisations adopt AI, a critical assumption is often unspoken: *people already know how to work with it*.

They don't. Not because they're incapable, but because "working effectively with AI" is a distinct set of skills that has only existed since modern chat assistants arrived in late 2022. Teams need both new hires and deliberate development in existing staff.

> "We gave everyone access to Claude. Three months later, we found out half the team thought AI just makes stuff up, so they don't use it for anything important."

The gap isn't knowledge — it's confidence paired with judgment. Knowing what AI can do. Knowing what it cannot. Knowing when to trust it.

## What to Hire For vs. What to Develop

You likely won't hire a completely "AI-ready" workforce. More realistically: recruit strategically, develop deliberately.

### New Hires: Prioritise These Signals

| Skill | What You're Actually Testing | Where It Matters |
|-------|---|---|
| **Critical thinking about tools** | Do they ask "why would I use this tool" not just "how"? | Everyone, but especially in technical and decision roles |
| **Comfort with uncertainty** | Do they prototype and iterate, or need perfect information first? | Product, strategy, analytics |
| **Domain expertise** (not AI expertise) | Do they know their field well enough to know what "wrong" looks like? | Any role where AI output requires judgment |
| **Bias awareness** | Do they think critically about training data, edge cases, failure modes? | Data roles, decision-making roles, compliance |
| **Collaborative style** | Do they help others improve their work, or just do their own? | Any role where they'll guide others on AI |
| **Documentation habits** | Can they explain decisions and processes clearly? | Anyone whose work others will review |

**What NOT to prioritise when hiring:**
- "AI experience" (if they have 2 years of ChatGPT use, they're actually learning outdated patterns)
- Certifications (mostly marketing)
- Ability to write prompts (easily developed, not a core skill)

### Existing Staff: Developing Core Capabilities

Most of your team will already be in place. They need development in specific areas:

#### Tier 1: Foundation (Everyone)
- What AI actually is (and isn't) — core Module 1 (How AI Actually Works) covers this ground
- Where it's genuinely useful vs. hyped
- When to use it (and when not to)
- Basic hands-on practice
- Understanding of risk (bias, hallucination, data privacy)

**Investment:** 2–4 hours structured training + ongoing access to tools

#### Tier 2: Practitioner (Domain-Specific Users)
- How to work with AI in *your* field specifically
- What outputs to trust vs. verify
- How to frame problems for AI to solve
- How to evaluate AI output quality
- Integration with existing workflows

**Investment:** 1–2 day workshop + 4 weeks of guided practice + access to expert for Q&A

#### Tier 3: Specialist (5–10% of organisation)
- Deep technical understanding of how models work
- Ability to assess new tools and vendors
- Building internal processes and guidelines
- Training others
- Architecture decisions (buy vs. build, vendor selection)

**Investment:** Formal course or hire specialist externally

```
EXERCISE:
Map your team against the three tiers:

1. Who are your Tier 1 (everyone) priority groups? (Estimate: 50–80% of staff)
2. Who are your Tier 2 (domain practitioner) candidates? (Estimate: 15–35% of staff)
3. Who are your Tier 3 (specialist) candidates? (Estimate: 5–10% of staff, possibly hire?)

For Tier 2 and 3, design a development plan:
- What specific capability do they need?
- By when?
- Measured how?
- Who trains them?
```

## The T-Shaped AI Team

The T-shaped model describes team composition:

```
      [Depth]
        ▲
        │
    [D] │ D D D D
        │ │ │ │ │
    [B] └─┴─┴─┴─┴─────────────────► [Breadth]
```

- **Vertical bar (depth):** Specialists with deep expertise in AI and your domain
- **Horizontal bar (breadth):** Everyone else with working knowledge of how to use AI responsibly

**Why this shape works:**
- Specialists solve novel problems, set standards, review high-stakes uses
- Broad knowledge means most work can be done well by domain experts using AI assistance
- Specialists aren't bottlenecks for routine use

### Building Your T-Shaped Team

**The specialists (vertical bar):**
- 1–3 people depending on organisation size
- Deep AI knowledge + deep domain knowledge (hard to hire, often grown internally)
- Responsibilities: vendor evaluation, architecture decisions, training, incident response
- They're not doing day-to-day AI work; they're building the systems others use

**The practitioners (horizontal bar):**
- Your existing teams, given working knowledge
- Don't need PhD-level understanding
- Need clear guidelines and guardrails
- Need access to specialists for edge cases

**Avoiding the T-shaped trap:**
- All specialists, no practitioners = AI tools sit unused ("needs expert permission")
- All practitioners, no specialists = governance gaps, people making risky decisions unsupervised

```
QUIZ:
You're building an AI capability centre. Your budget allows for one person to dedicate 50% time. You should:

* Hire someone full-time to write AI prompts for the organisation
*! Find someone with deep domain expertise and give them 50% time to define processes, train teams, and manage vendor relationships
* Buy a managed service and don't hire anyone internal
* Hire a recent AI bootcamp graduate to train everyone

FEEDBACK: The specialist role is about governance, evaluation, and enabling others — not day-to-day tool use. Deep domain expertise matters more than pure AI expertise; they're evaluating tools for *your* context.
```

## Shifting Organisational Culture

The biggest barrier to AI readiness isn't capability — it's culture.

### Belief 1: "AI Will Replace Me"

**What you hear:**
- "If we automate this, I'll lose my job"
- Resistance to tools, reluctance to engage
- People doing work manually rather than with AI

**The leader's response:**
- **Honest:** "AI changes what you do, not whether we need you"
- **Specific:** "This tool handles [X], which means you'll spend more time on [Y]" (where Y is usually higher-value)
- **Evidence-based:** Share stories of people who upskilled rather than left
- **Structural:** Show that organisation is growing, not shrinking

**What works:**
- Early involvement: include sceptical people in pilots
- Transparency: involve them in use-case selection
- Skills investment: pay for training, give time to learn
- Career pathways: show how AI skills improve careers

### Belief 2: "AI is a Magic Solution"

**What you hear:**
- "Let's just use AI for everything"
- Overconfidence in outputs without verification
- Decisions made on AI recommendations without human judgment

**The leader's response:**
- **Honest:** "AI is powerful and limited simultaneously"
- **Specific:** Show failure cases (hallucinations, biases, confidentiality breaches)
- **Structured:** Define when AI input is sufficient vs. when human judgment is required
- **Measured:** Show quality metrics (% of outputs that need rework)

**What works:**
- Training that includes failure modes explicitly
- Examples of what went wrong (anonymised, local if possible)
- Clear policies: "AI can do [X], but [Y] requires human decision"
- Celebration of people catching AI errors (not shame, celebration)

### Belief 3: "This Doesn't Apply to My Role"

**What you hear:**
- Finance teams: "Numbers are too precise for AI"
- Legal: "Too risky; I can't use AI"
- Compliance: "Audit trail problems"

**The leader's response:**
- **Honest:** "You're right about the risks; here's how to mitigate them"
- **Concrete:** Show use cases from *your* domain (not generic examples)
- **Structured:** Define constraints that make sense for your function
- **Partnership:** Involve compliance/legal in defining boundaries, not just saying no

**What works:**
- Function-specific training (not generic AI literacy)
- Pilot projects that start in low-risk areas
- Policy developed with the function, not imposed by IT
- Recognition that some functions will have stricter policies (fine; that's design, not failure)

## Training Investment Decisions

Three decisions: How much? For whom? When?

### How Much Budget?

| Approach | Cost | Outcome |
|----------|------|---------|
| **Minimal** (online courses, self-service) | £0–2k per person | Uneven adoption, many don't complete |
| **Moderate** (structured training + practice) | £2–5k per person | 60–70% adopt effectively, need reinforcement |
| **Comprehensive** (training + coaching + projects) | £5–10k+ per person | 80%+ adopt effectively, embedded in culture |

There's no universal "right" answer, but:
- If you're betting the organisation on AI adoption, cost per person is small relative to the stakes
- If this is "nice to explore," cheaper approach is fine
- **Sunk cost warning:** Cheap training that doesn't stick costs more in opportunity cost than investments in the right level

### For Whom?

**Tier 1 (everyone):** Mandatorily, measured by completion + basic knowledge test

**Tier 2 (practitioners):** Mandatory for people in roles where they'll use it frequently; optional for others

**Tier 3 (specialists):** Very selective; high investment per person

Track completion and learning outcomes. Don't pretend training happened if it didn't.

### When?

**Early adoption trap:** Train everyone before they have tools or permission to use them. They forget.

**Better approach:**
1. Identify initial use cases (from L1 strategic assessment)
2. Train people directly involved in those uses
3. Expand training as new uses come online
4. Reinforce periodically (don't assume knowledge sticks)

```
QUIZ:
Your CFO says: "I'll do the online AI course." You should:

* Support the decision; they're taking initiative
* Suggest they also do the function-specific training for finance use cases
*! Both support their choice and make sure they understand what they *won't* learn online, then arrange finance-specific follow-up
* Skip function-specific training; generic training is enough

FEEDBACK: Self-directed learning is great, but most online courses don't cover domain-specific risks and opportunities. Finance roles have specific concerns (audit trails, data sensitivity, compliance). Don't assume generic training covers those.
```

## Knowledge Retention and Reinforcement

Training is not one-time. People forget. Context changes. New tools arrive.

**Simple approach:**
- Quarterly refreshers (30 minutes, focusing on lessons learned from pilots)
- Monthly examples: "Here's how teams are using AI effectively"
- Incident reviews: "When something went wrong, here's what happened and what we learned"
- Success stories: "This team saved 15 hours per week and improved quality; here's how"

Make it normal for learning to continue.

## Key Takeaways

- Hiring for critical thinking and domain expertise, not AI credentials
- Develop existing staff in three tiers: foundation (everyone), practitioner (domain-specific), specialist (5–10%)
- Build T-shaped teams: deep specialists, broad practitioner knowledge
- Shift culture from "AI replaces me" to "AI changes what I do"
- Training decisions balance budget, breadth, and timing
- Learning doesn't end after initial training; reinforce regularly

---

Next: **L3. Risk & Reputation** →
