# L4. Vendor & Build Decisions

## The Buy vs. Build Framework

Every AI capability can theoretically be bought, built, or hybridised. The decision determines cost, speed, control, and risk.

### Three Approaches and Their Trade-offs

| Dimension | Buy (SaaS) | Build | Hybrid |
|-----------|---|---|---|
| **Speed to value** | Weeks to months | Months to years | Months |
| **Control** | Limited to vendor choices | Complete | Moderate |
| **Cost model** | Predictable, scaling | Unpredictable, upfront | Both patterns |
| **Maintenance** | Vendor owns it | You own it | Shared |
| **Customisation** | Limited, API-dependent | Unlimited | Good |
| **Lock-in risk** | High (data, integrations) | Low | Moderate |
| **Expertise required** | Moderate | High | Moderate-high |
| **Data residency** | Vendor determines | You control | Varies |

**When to buy:**
- Core capability is not unique to your organisation (e.g., general customer service)
- Vendor's update cycle suits your needs
- Cost is acceptable at scale
- You can tolerate vendor lock-in for this capability

**When to build:**
- Capability is central to competitive advantage
- Vendor offerings don't meet your requirements
- You have sufficient engineering talent
- You want to own the data and process
- You're prepared for the long development and maintenance timeline

**When to hybrid:**
- Buy a general capability (API), customise it for your context
- Build wrapper or orchestration around vendor tools
- Use vendor for commodity, build for differentiation

```
EXERCISE:
For your top 3 AI use cases from L1 strategic assessment:

1. Evaluate each on the buy/build decision framework
2. Document: Why this approach? What's the risk if you're wrong?
3. For "buy" — list vendors you'd evaluate
4. For "build" — estimate timeline and cost
5. For "hybrid" — define the boundary: what you buy vs. what you build
```

## Evaluating AI Vendors and Products

If you're buying, you're making a bet on a vendor. Most organisations have a poor vendor evaluation process for AI.

### Questions to Ask (Vendor-Agnostic)

**Does it work for our use case?**

- "Show us a test with our data or representative data"
- "Don't show us a demo — show us unedited performance on messy data"
- "What does failure look like? When would this not work?"
- "Benchmark against alternatives or baseline (human work)"

**What are the constraints?**

- Input/output limits (rate, size, latency)
- Data residency (where does data live? Can we choose?)
- Integration options (API, webhook, batch, UI-only)
- Customisation limits (can we fine-tune? On what terms?)
- SLA and uptime guarantees (when are they available, how responsive is support?)

**What happens to our data?**

- Retention: how long is data kept after our use?
- Training: will our data be used to improve their model?
- Access: who at the vendor can access our data?
- Deletion: can we request data deletion? How quickly?
- Compliance: do they meet our regulatory requirements? (GDPR, HIPAA, SOC 2, etc.)
- Audit: can we audit their data handling?

**What's the pricing model?**

- Tokens, API calls, seats, or fixed?
- Volume discounts or price increases?
- How's overage handled?
- Are there hidden costs (setup, support, data egress)?
- What happens if they change pricing? (Notice period, protection?)

**What's the vendor stability?**

- Funding and runway (will they still exist in 3 years?)
- Customer concentration (are they dependent on one big customer?)
- Roadmap alignment (are they building toward your needs or away?)
- Support quality (can you reach someone when needed?)
- History with customers (talk to reference customers, check honest reviews)

**What's the lock-in risk?**

- Data format: can you export in standard format?
- Integration: how deeply are you coupled to their API?
- Switching cost: if you leave, what's the effort/cost?
- Exit clause: can you leave easily if they disappoint you?

```
QUIZ:
A vendor says: "Our AI is trained on millions of documents, so it's very capable." You should:

* Trust the scale as evidence of capability
*! Ask: "What percentage of your training data is relevant to our use case?" and "Prove it works on our data, not theoretical capability"
* Assume more training data = better results
* Ask about their company funding instead

FEEDBACK: Scale is marketing, not proof of relevance. A model trained on broad internet data may perform poorly on your specific domain. Always demand proof of performance on *your* problem, not claims about training size.
```

### Red Flags in Vendor Relationships

- **Vague on data handling.** "It's secure" without specifics.
- **No trial period or no willingness to test on real data.** ("Trust us, it works.")
- **Locks you in before proving value.** (Multi-year contracts on untested tech.)
- **Won't answer your questions directly.** (Always deflects to sales.)
- **Pricing unclear or changes unexpectedly.**
- **Single point of contact** (if that person leaves, you lose support).
- **Dismisses your concerns** about bias, hallucination, or data privacy.
- **References are all in perfect situations** (ask about problems they've had).

## Avoiding Lock-In

Lock-in occurs when switching vendors becomes prohibitively expensive.

### Technical Lock-In

**The problem:** You've built so much on their API/format that switching costs a rewrite.

**How to prevent:**
- Wrapper layer: build your own interface to their API; if you switch vendors, you replace the implementation, not all your code
- Standard formats: if they're not using industry-standard formats, question why
- Modular architecture: can you swap one vendor for another without rebuilding everything?
- Data portability: insist on regular exports in standard format (not a one-time process)

### Commercial Lock-In

**The problem:** They've made the service cheaper the more you use it, so leaving is expensive. Or they've changed pricing retroactively.

**How to prevent:**
- Multi-year pricing guarantees (in writing)
- Exit clauses if pricing increases beyond X%
- No per-seat or per-user pricing that scales unpredictably
- Understand total cost of ownership, not just headline price

### Operational Lock-In

**The problem:** Your team has built workflows and skill around their specific system. Switching means retraining and disrupting work.

**How to prevent:**
- Document workflows in vendor-agnostic terms
- Train teams on principles, not specific tool mechanics
- Have a fallback (can you do the work without AI if needed?)
- Every few years, re-evaluate: "Could we switch if we wanted to?"

## Cost Models: What Leaders Need to Understand

### Tokens (Per-Use Pricing)

**How it works:** You pay for input and output "tokens" (roughly words).

**Characteristics:**
- Scales with use volume
- Transparent per-request cost
- Difficult to predict total cost (depends on usage patterns)
- Can be cheap for infrequent use, expensive for high volume

**Questions to ask:**
- Input vs. output token cost (usually output is 2–4× input)
- Are there minimums or monthly baselines?
- How do you measure tokens? (Different vendors count differently)
- Do prices change based on volume?

**When it's a good model:** Experimentation, variable workloads, starting out

**When it's a bad model:** High-volume, cost-sensitive production work (costs become unpredictable)

### Seats / Per-User

**How it works:** Fixed monthly cost per user, often with fair-use limits.

**Characteristics:**
- Predictable cost
- Encourages high usage (included in price)
- Cost per organisation is hidden (if you scale team, cost scales)

**Questions to ask:**
- Fair-use limits (what triggers overages?)
- Can seats be shared? (Can you have a team account?)
- Cost per additional user?

**When it's a good model:** Team collaboration, unlimited per-user usage

**When it's a bad model:** Large organisations with many users, or sporadic usage (paying for seats that don't use them)

### Compute / Infrastructure

**How it works:** You run the model yourself; you pay for the infrastructure (GPU/compute hours).

**Characteristics:**
- Cost depends on compute efficiency and uptime
- You control it
- Requires expertise to optimise
- Can be very expensive if not efficient

**Questions to ask:**
- What hardware is recommended?
- How many inference instances do you need?
- Cost to host 24/7?
- Scaling beyond your initial estimate?

**When it's a good model:** High security requirements, high volume, cost-optimised at scale

**When it's a bad model:** Small teams, variable workloads, no ML infrastructure expertise

### Fixed / Enterprise

**How it works:** Flat fee, often with SLA, support, and customisation included.

**Characteristics:**
- Predictable cost
- Encourages use (no variable cost)
- Supports negotiations on terms
- Often includes custom work

**Questions to ask:**
- What's included? (Users, volume, support level, SLA uptime?)
- What's outside the scope? (Custom training, consulting?)
- What happens if you exceed limits?

**When it's a good model:** Mission-critical work, large organisations, multi-year commitment

**When it's a bad model:** Uncertain use cases, small teams

### Comparison Framework

```
USE CASE: [Name]
ESTIMATED MONTHLY VOLUME: [requests, hours, users]

VENDOR A (Token-based):
- Cost: £[X] per 1M tokens
- Estimated monthly cost: £[Y] (assumptions: [list])
- Annual cost: £[Z]

VENDOR B (Per-seat):
- Cost: £[X] per user per month
- Estimated monthly: £[Y] (assumptions: [list])
- Annual cost: £[Z]

VENDOR C (Infrastructure):
- Compute cost: £[X] per hour
- Estimated monthly: £[Y] (assumptions: [list])
- Annual cost: £[Z]

SENSITIVITY:
- If volume doubles, cost changes to: [A: £Z', B: £Z', C: £Z']
- If we have 50% higher usage than forecast, cost becomes: [£X]
```

## Build: The Hidden Costs

If you're considering building, understand what you're actually committing to.

### Visible Costs
- Initial development: 6–12 months, 2–5 engineers
- Infrastructure: GPU compute, storage
- Initial investment: often £500k–£2M+ for meaningful models

### Hidden Costs (Usually Underestimated)
- **Ongoing training and fine-tuning:** Models degrade or need updating. Plan for quarterly work minimum.
- **Prompt engineering:** Writing, testing, refining prompts is continuous. This is a real cost.
- **Evaluation and monitoring:** How do you know if your model is working? Building evaluation systems is substantial.
- **Incident response:** When the model fails, you need to fix it. This isn't 9-to-5 work.
- **Team expertise loss:** If your expert leaves, you're vulnerable. Need redundancy.
- **Vendor dependencies anyway:** You're still using someone's base model (OpenAI, Anthropic, open-source). You're maintaining it, not replacing it.

### When Build Actually Makes Sense

- You have **persistent competitive advantage** from the AI (e.g., recommendation system core to your product)
- You have **existing ML expertise** in-house
- You've already tried **buying and it didn't work**
- You have **committed, multi-year funding** (not "let's see how it goes")
- You're comfortable with **high risk of failure** or timeline slippage

Build is often a strategic choice, not a cost one. If you're choosing build purely on cost, you'll likely regret it.

```
QUIZ:
You're considering whether to build a custom AI model for your product recommendation system. What's the most important question?

* "How much will it cost?"
*! "Is this a core competitive advantage where custom beats vendor, or could we buy and focus engineering on integration?"
* "Can we hire AI engineers?"
* "What's the timeline?"

FEEDBACK: The build/buy decision should start with strategy: does custom give you genuine advantage over a vendor solution? If no, buying and focusing on integration is smarter. Cost is secondary to strategic fit.
```

## Building Internal AI Capability Centre

Many organisations create an internal centre of excellence: a team that manages AI adoption across the organisation.

### What They Do

- Vendor evaluation and selection
- Pilot project support
- Training and guidance
- Risk and compliance oversight
- Incident response
- Tool and platform selection
- Cross-functional learning

### How to Fund It

**Fixed team:** 2–5 people, funded from central budget, supporting all departments

**Funding model:** Either central cost centre (departments don't directly pay) or charge-back (departments pay per use/project)

**Staffing:** Mix of domain expertise + AI expertise + business acumen

## Key Takeaways

- Buy vs. build: strategic fit matters more than cost
- Demand proof on *your* data, not vendor claims
- Understand vendor lock-in across technical, commercial, and operational dimensions
- Token pricing is transparent but hard to predict; seats are predictable but hidden cost
- Building is high-commitment; ensure you have expertise, funding, and strategic advantage
- Create an internal capability centre to manage vendors and guide adoption
- Avoid single-vendor dependency for critical capabilities

---

Congratulations! You've completed the Leadership Track.

Your organisation is now positioned to adopt AI strategically: assessing real value, building capable teams, managing risks, and making sound buy/build decisions. The remaining challenge is execution — turning these frameworks into actual decisions and actions.

Consider also:

- **Enterprise Track** — For deeper governance and compliance requirements
- **Operations Track** — For using AI in common business processes
- **Developer Track** — For understanding technical constraints of the tools your teams use
- **Academic Track** — For critical evaluation and research applications of AI
