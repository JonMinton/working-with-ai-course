# Module 7: The Agentification Shockwave

## What is Agentification?

Agentification is the expansion of AI agent capabilities outward from software development to other fields. It's not about replacement — it's about a fundamental shift in what becomes valuable within a field: the bottom 90% of routine work becomes less valuable (or automatable), whilst the top 10% of judgment, verification, and direction-setting becomes *more* valuable.

You've seen this in software development already. AI hasn't eliminated developers — it's made it so that developers who can't specify clearly, verify rigorously, and iterate effectively become less valuable, whilst developers who can orchestrate AI and catch its mistakes become more valuable.

This shift is spreading outward, field by field, in a somewhat predictable pattern. Understanding when and how your field will experience agentification is the point of this module.

## The Six Dimensions of Adjacency

Why does agentification spread from software development outward? Because certain characteristics make a field "adjacent" to software development — characteristics that make it easier for AI to do substantial chunks of the work.

These six dimensions predict how soon agentification will affect a field:

### 1. Text/Code as Primary Medium

**Does the work happen in text that AI can read and write?**

If your work product is code, prose, structured text, or symbolic notation, AI can directly produce it. If your work happens in physical space, visual judgment, or embodied cognition, AI's contribution is more limited.

**High adjacency:** Code, technical writing, legal documents, academic papers
**Low adjacency:** Surgical procedures, dance choreography, architecture (where judgment involves physical constraints)

### 2. Machine-Verifiable Outputs

**Can you check correctness programmatically?**

If correctness can be verified by running tests, checking numerical precision, validating against a known schema, or comparing to an objective standard, then you can close the feedback loop automatically. If correctness requires human judgment ("Is this well-written?" "Is the design elegant?"), the loop requires human effort.

**High adjacency:** Code (tests pass/fail), financial models (numerical precision), data pipelines (validation rules)
**Low adjacency:** Copywriting, art direction, therapeutic advice

### 3. Digital Environment

**Is the work done entirely on computers?**

Work that happens in digital tools can be measured, recorded, and iterated on quickly. Work that requires physical presence, site visits, or real-time human presence is slower to agentify.

**High adjacency:** Data analysis, software engineering, accounting, CAD design
**Low adjacency:** Clinical diagnosis, plumbing, emergency response

### 4. Tight Feedback Loops

**Can you test ideas and get results quickly?**

If you can iterate in minutes, AI can be highly productive. If each iteration takes weeks (waiting for regulatory approval, clinical trials, construction), agentification happens more slowly.

**High adjacency:** Software development, data science, technical writing
**Low adjacency:** Drug development, infrastructure planning, medicine

### 5. Explicit Specification

**Are requirements articulable in advance?**

If you can specify what you want before work starts — acceptance criteria, constraints, expected outputs — AI can be precisely guided. If the specification emerges through exploration and conversation, AI is less effective at independent work.

**High adjacency:** "Build a login system with these requirements" (clear spec)
**Low adjacency:** "Develop a therapy approach for this unique patient" (emerges through interaction)

### 6. Modular Decomposition

**Can work be broken into independent sub-tasks?**

If a project naturally breaks into discrete tasks that can be done separately, AI can tackle each piece. If the work requires deep coupling between tasks, or requires holding an entire system in mind simultaneously, agentification is slower.

**High adjacency:** Testing (independent), documentation (independent), data pipeline stages
**Low adjacency:** Collaborative sense-making, cross-domain integration, emergency coordination

---

## The Five Rings of Agentification

These dimensions create expanding "rings" of fields, ordered by how soon (and how forcefully) agentification hits each one.

```
╭──────────────────────────────── RING 4 · Distant ─────────────────────────────────╮
│               medicine · skilled trades · therapy · performing arts               │
│   ╭────────────────────── RING 3 · Moderately adjacent ───────────────────────╮   │
│   │          consulting · journalism · education · HR · architecture          │   │
│   │   ╭───────────────────── RING 2 · Near-adjacent ──────────────────────╮   │   │
│   │   │  law · accounting · academic research · UX · marketing analytics  │   │   │
│   │   │   ╭────────────── RING 1 · Immediately adjacent ──────────────╮   │   │   │
│   │   │   │ data science · DevOps · quant finance · technical writing │   │   │   │
│   │   │   │       ╭────── RING 0 · SOFTWARE DEVELOPMENT ──────╮       │   │   │   │
│   │   │   │       │ the epicentre — already deeply agentified │       │   │   │   │
│   │   │   │       ╰───────────────────────────────────────────╯       │   │   │   │
│   │   │   ╰───────────────────────────────────────────────────────────╯   │   │   │
│   │   ╰───────────────────────────────────────────────────────────────────╯   │   │
│   ╰───────────────────────────────────────────────────────────────────────────╯   │
╰───────────────────────────────────────────────────────────────────────────────────╯
```

**A note on timelines.** Earlier versions of frameworks like this attached confident year ranges to each ring. The inner rings have largely played out as predicted — software development and data work agentified first and fastest. The outer rings are forecasts, and forecasts about AI have a short shelf life in both directions. Treat the rings as an *ordering* (what gets hit sooner vs. later, and why) rather than a calendar.

### Ring 0: Software Development (Already Deeply Agentified)

Software development sits at the centre because it maxes out all six dimensions:

- **Text/code as primary medium:** Yes (code is text)
- **Machine-verifiable outputs:** Yes (tests prove correctness)
- **Digital environment:** Yes (100% computer-based)
- **Tight feedback loops:** Yes (build/test in seconds)
- **Explicit specification:** Yes (requirements, test cases)
- **Modular decomposition:** Yes (tests, functions, modules)

The shift is now thoroughly visible: the AI-assisted developer who can verify AI output and iterate effectively is more valuable than the developer who can't; mechanical coding without verification commands less and less of a premium.

**What's been agentified:**
- Code generation (starting from specs)
- Testing & test generation
- Debugging (with AI helping identify issues)
- Documentation
- Infrastructure automation

**What's still precious:**
- Architectural decisions
- Specification and requirements work
- Verification (knowing when AI is wrong)
- Integration across systems
- Trade-off analysis

---

### Ring 1: Immediately Adjacent (Well Advanced)

These fields share most of Ring 0's characteristics, and agentification here is no longer a forecast — it's the working reality for many practitioners.

#### Data Science & Analytics

All six dimensions score high:
- Outputs are code (SQL, Python, R) plus text (reports)
- Correctness is machine-verifiable (data validation, statistical tests)
- Entirely digital
- Tight feedback loops (notebooks, immediate visualisation)
- Requirements can be explicit (metrics, audience)
- Tasks decompose naturally (exploratory → modelling → production)

**What's being agentified:** Data exploration, hypothesis generation, standard analyses, report writing, pipeline code.

**What's becoming more valuable:** Knowing which questions to ask, designing good experiments, catching statistical errors, communicating uncertainty.

#### DevOps & Infrastructure

- Code-based (Infrastructure as Code)
- Verifiable outputs (deployment succeeds/fails, monitoring shows health)
- Digital environment
- Feedback loops of minutes (test deployment, rollback if needed)
- Explicit specs (desired infrastructure state)
- Modular (each service, each environment)

**What's being agentified:** Configuration generation, deployment scripts, monitoring setup, infrastructure troubleshooting.

**What's becoming more valuable:** Architectural trade-offs, capacity planning, disaster recovery design, security decisions.

#### Quantitative Finance & Economics

- Output is code and mathematical notation
- Correctness is numerically verifiable (backtests, P&L accuracy)
- Digital environment
- Feedback loops of minutes to hours (model runs, strategy testing)
- Explicit specs (trading rules, risk constraints)
- Modular (risk model, pricing model, execution engine)

**What's being agentified:** Model implementation, routine analysis, backtesting, report generation.

**What's becoming more valuable:** Mathematical insight, risk intuition, understanding novel market conditions, identifying which models actually matter.

#### Technical Writing & Documentation

- Pure text output
- Verifiable: accuracy (facts correct?), completeness (all steps covered?), structure (follows template?)
- Digital environment
- Feedback loops of minutes (review, revise)
- Explicit specs (audience, structure, scope)
- Modular (chapters, sections, examples)

**What's being agentified:** First drafts, standard documentation templates, code examples, FAQ generation.

**What's becoming more valuable:** Information architecture, knowing what users actually need to know, finding the gaps in what exists, clarity and precision.

---

### Ring 2: Near-Adjacent (Accelerating Now)

These fields are structured enough that agentification is well underway, but they face specific challenges from lower scores on one or two dimensions.

#### Legal Research & Contract Drafting

**Strengths:** Text output, structured arguments, precedent-based reasoning, searchable case law, explicit legal specs.

**Challenges:** Requires human judgment about nuance, risk, and context. Machine-verifiable outputs are limited (correctness of a legal argument isn't "pass/fail" — it's "well-reasoned in jurisdictional context").

**What's being agentified:** Legal research (finding relevant cases), contract templating, due diligence document review, regulatory compliance checking, first-draft document generation.

**What's becoming more valuable:** Judgment about novel situations, negotiation strategy, client communication, understanding what the law should accomplish (not just what it says).

#### Accounting & Audit

**Strengths:** Numerically verifiable, rule-based, modular (each account, each transaction type), tight feedback loops (test runs, reconciliation checks).

**Challenges:** Human judgment required for estimates, judgement calls, and interpretation of ambiguous transactions.

**What's being agentified:** Transaction coding, audit trail generation, standard journal entries, reconciliation procedures, compliance report generation, tax form preparation.

**What's becoming more valuable:** Judgment calls (valuation estimates, risk assessment), fraud detection (pattern recognition beyond rules), interpretation of ambiguous transactions, client advisory.

#### Academic Research

**Strengths:** Text-heavy, citation-based, structured arguments, modular (literature review, methods, results, discussion).

**Challenges:** Novelty is hard to verify. "Correctness" of a novel argument requires domain expertise and peer review. Tight feedback loops are slower (peer review, experiments).

**What's being agentified:** Literature summarisation, method documentation, data analysis, results writeup, draft generation from raw analysis.

**What's becoming more valuable:** Research direction (which questions matter?), novel framing, experimental design, identifying the boundaries of existing knowledge, synthesis across domains.

#### UX/Product Design

**Strengths:** Increasingly digital tools, can generate wireframes and flows, requirements can be explicit.

**Challenges:** Subjective aesthetic judgment, user testing isn't fully machine-verifiable, embodied understanding of how humans interact.

**What's being agentified:** Low-fidelity prototyping, user flow documentation, accessibility audit, copy generation, design system documentation, usability pattern libraries.

**What's becoming more valuable:** User research and synthesis, aesthetic direction, knowing which trade-offs matter, emotional resonance and branding.

#### Marketing Analytics

**Strengths:** Data-driven, code-based analysis, numerical metrics, large datasets, clear specs (increase X metric).

**Challenges:** Feedback loops are slow (campaigns run for weeks), causality is hard to verify (did the marketing change work, or did the market shift?).

**What's being agentified:** Data pipeline setup, attribution modelling, report generation, A/B test analysis, audience segmentation, standard analytics.

**What's becoming more valuable:** Campaign strategy (which initiatives matter?), connecting customer understanding to metrics, identifying what's actually driving behaviour, creative direction.

---

### Ring 3: Moderately Adjacent (Gathering Pace)

These fields will experience significant agentification over the coming years, but they face more substantial barriers. Typically, one or two dimensions score *much lower*.

#### Management Consulting

**Challenge:** Primary outputs are analysis + persuasion. The analysis part is very amenable to agentification (data work, frameworks, structure). The persuasion part requires judgment, client relationships, and credibility.

**What's being agentified:** Initial data gathering, framework application, benchmarking, report structure and first drafts, presentation organisation.

**What's becoming more valuable:** Client relationship and trust, identifying the real problem (not the stated one), creative solution synthesis, ability to persuade.

#### Journalism

**Challenge:** Requires access to sources, verification of facts, and editorial judgment about newsworthiness and narrative.

**What's being agentified:** Structural reporting (fact-gathering, organising information), routine coverage (earnings analysis, data journalism), summary writing.

**What's becoming more valuable:** Access to sources and trust relationships, editorial judgment and story framing, investigative capability (persistence, following threads), identifying what matters.

#### Education & Curriculum Design

**Challenge:** Highly contextual. What works depends on specific students, institutional constraints, and learning objectives that are fuzzy to specify.

**What's being agentified:** Content generation, explanation writing, problem set creation, assessment rubric design, curriculum structure templates.

**What's becoming more valuable:** Understanding how specific learners think, adapting to context, motivation and engagement, assessment and feedback strategy.

#### HR & Recruitment

**Challenge:** High-stakes judgment (hiring decisions affect people's lives), but work is text-heavy and structured.

**What's being agentified:** Resume screening, job description writing, interview question generation, offer letter drafting, employment law compliance checking.

**What's becoming more valuable:** Judgment about cultural fit and potential, understanding what the role actually needs, candidate experience, retention strategy.

#### Architecture

**Challenge:** Digital tools are increasingly capable, but physical constraints, aesthetic judgment, and building codes require embodied understanding.

**What's being agentified:** CAD generation, specification writing, code compliance checking, parametric design, documentation.

**What's becoming more valuable:** Aesthetic direction, spatial reasoning (how will this actually feel?), site-specific constraints, coordinating across trades and regulations.

---

### Ring 4: Distant (The Long Tail)

These fields will experience agentification *slowly*, if at all, in the near term. They score *very* low on multiple dimensions — often including "digital environment" or "text as primary medium." AI assists at the edges (documentation, scheduling, decision support) while the core of the work stays human.

#### Medicine & Clinical Work

**Challenge:** Requires physical examination, real-time decision-making with stakes, regulatory oversight, and embodied judgment.

**What AI can do:** Decision support (providing evidence), documentation, research summaries, administrative work.

**What AI cannot do:** Direct patient care, diagnosis requiring physical examination, treatment decisions with liability, ethical judgments about what's right for this patient.

**Likely future:** AI assistants that support doctors (better documentation, faster literature review, decision support) rather than replace them. The doctor's judgment becomes *more* valuable because verification becomes harder.

#### Social Work & Therapy

**Challenge:** Relational, emotional, high-stakes. Correctness isn't verifiable. The relationship itself is the intervention.

**What AI can do:** Administrative work, documentation, resource recommendation, psychoeducation.

**What AI cannot do:** Therapeutic relationship, assessing safety and risk, moment-to-moment adaptation.

#### Skilled Trades (Plumbing, Electrical, HVAC)

**Challenge:** Physical, spatial, dealing with hidden state (you can't see inside the walls). Feedback loops require troubleshooting on-site. Geoffrey Hinton has famously suggested plumbing is among the work *least* exposed to AI — precisely because it's embodied, varied, and full of novel physical situations.

**What AI can do:** Design of systems, troubleshooting guides, code compliance, documentation.

**What AI cannot do:** Diagnosis of hidden problems, adaptation to unexpected physical constraints, quality control requiring hands-on inspection.

#### Performing Arts

**Challenge:** Real-time, embodied, audience-responsive. The performance is the product. Feedback loop is immediate (audience reaction).

**What AI can do:** Composition assistance, choreography inspiration, set design, lighting design, documentation.

**What AI cannot do:** Performance itself (timing, presence, connection with audience).

#### Emergency Services

**Challenge:** Unpredictable, time-critical, physical, life-or-death stakes with incomplete information.

**What AI can do:** Dispatch routing, resource allocation, post-incident analysis.

**What AI cannot do:** On-scene decision-making, physical response, real-time triage.

---

## Key Nuances

### Not Replacement, Reshuffling

This isn't about jobs disappearing — it's about which *skills* become valuable within fields.

In software development today:
- Writing basic CRUD endpoints is far less valuable than it was a decade ago
- Knowing how to specify clearly and verify rigorously is *more* valuable
- The number of people who can build software is larger (lower barrier to entry), but the skill distribution shifts

The same will happen in other fields. A legal researcher who can't verify AI-generated case summaries will be less valuable. A legal researcher who understands how to use AI to accelerate research whilst catching errors will be more valuable.

### Non-Uniform Progress Through Rings

Fields don't move through rings uniformly. *Specific tasks* within a field may agentify long before the field overall.

For example:
- **Accounting:** Tax return preparation (highly structured, rule-based) will agentify faster than audit (requires judgment).
- **Medicine:** Triage protocols (structured decision trees) will agentify before diagnosis (requires judgment).
- **Journalism:** Earnings analysis (data-driven) will agentify before investigative reporting (requires access and judgment).

### The Rings Get More Crowded As They Widen

Software development employs tens of millions of people worldwide. Each successive ring — data and technical work, then the regulated professions, then education, consulting and administration, then care, trades, and the physical economy — contains far more workers than the one inside it.

So as agentification spreads outward, the number of people affected *grows*, not shrinks. The disruption gets larger as you move away from the epicentre. This is why thinking about agentification *now* is important for nearly everyone — including people whose fields feel far from software.

### The "Capable Temp" Becomes More Useful As Work Is More Structured

Remember the "capable temp" mental model from Module 4? An AI agent is like a very capable temp who arrives with no memory, works from the briefing you give, and leaves at the end of the day.

That metaphor works well in Ring 0 and Ring 1, where work is highly structured and verifiable. It works less well in Ring 4, where work requires relationship, presence, and embodied judgment. A temp can help with infrastructure; a temp cannot substitute for a therapist.

---

## What This Means For Your Skills

The structure of this course — specification, understanding, verification, iteration, and now understanding the broader context — is calibrated to what becomes valuable *across all rings* as agentification spreads.

**Understanding the machine** (Module 1): Knowing *why* AI fabricates, flatters, and varies — not just that it does — lets you predict where it will fail in your field before it does.

**Specification** (Module 2): The more fields agentify, the more that knowing *what you want* precisely becomes the bottleneck. You can't delegate effectively to AI (or to people) if you can't specify.

**Understanding the system** (Module 4): The "capable temp" mental model is universally useful. Whether you're in software development (Ring 0) or management consulting (Ring 3), you need to understand what the AI system actually *is* and what it can't do.

**Verification** (Module 5): This becomes *more* important, not less, as you move outward through the rings. Ring 0 has tests; Ring 4 has human judgment. But in *every* ring, you need to be able to check whether the AI's output is actually right for your context.

**Iteration** (Module 6): The feedback loop is the same everywhere. Give clear feedback, know when to refine vs. restart, manage context degradation. These are universal skills.

**Understanding adjacency** (this module): Knowing when agentification will hit your field, which skills will become valuable, and which will become less valuable, is information you need to make decisions about what to learn and what to automate.

---

## Specialisation Tracks

This is the last core module. From here, you choose one or more specialised tracks based on your field:

- **Enterprise Track:** Trust architecture, approved channels, governance, monitoring
- **Developer Track:** Affordances, architecture, MCP tool design, testing AI systems
- **Academic Track:** Literature workflows, modular writing, AI peer review, reproducibility
- **Creative Track:** Voice and style, creative iteration, visual collaboration, attribution
- **Operations Track:** Document workflows, data wrangling, process documentation, communication
- **Education Track:** AI-resistant assessment, AI as learning partner, personalisation, AI literacy
- **Leadership Track:** Strategic assessment, AI-ready teams, risk and reputation, vendor decisions

These tracks take what you've learned about how AI works, specification, verification, and iteration — and show you how they apply *specifically* in your field.

---

```
QUIZ:
You work in management consulting. Your firm is starting to experiment with having AI generate first drafts of reports. Which of these statements is most accurate?

* Consultants will be replaced by AI within 5 years
*! The skills that become more valuable are client relationship, identifying the real problem, and creative solution synthesis
* Management consulting is in Ring 0, so agentification is already complete
* AI can't help much with consulting because it requires judgment

FEEDBACK: Management consulting is in Ring 3 — moderately adjacent. The analysis part (data gathering, framework application, report structure) is agentifiable. The persuasion, client relationship, and creative problem-solving parts are not. The same consultant who couldn't use AI effectively to accelerate the analysis would be less valuable; the consultant who could would be more valuable.
```

---

```
QUIZ:
A hospital is exploring AI for clinical decision support. What's the realistic timeline for this?

* Immediate — doctors will be replaced by AI doctors
* 2-3 years — AI will do most clinical work
*! Gradual — AI will keep improving decision support and reducing documentation burden, but clinical judgment remains central
* Never — AI can't help with medicine

FEEDBACK: Medicine is in Ring 4 — distant from software development. AI improves support (literature access, decision trees, documentation) but doesn't replace clinical judgment. The verification requirement is *higher*, not lower — a human has to interpret AI's suggestions for this specific patient.
```

---

```
EXERCISE:
Choose a field you work in or are interested in. For that field:

1. Where does it sit on the ring map? (Be specific — which dimension is the biggest gap?)
2. What tasks within your field are most agentifiable right now?
3. What skills will become more valuable as those tasks agentify?
4. What would you need to learn to be effective as those changes happen?

(This exercise is worth returning to periodically as your field evolves.)
```

---

```
EXERCISE:
You're advising someone entering your field. Given where your field sits on the ring map, what skills should they prioritise learning?

Consider:
- Which tasks will likely be agentified in the next 5 years?
- Which tasks require judgment that AI is bad at?
- How should they spend their limited learning time?

(This is the essence of career planning in an age of agentification.)
```

---

## Key Takeaways

- Agentification is spreading outward from software development in a predictable pattern based on six dimensions: text/code, verifiability, digital environment, feedback loops, explicit specification, and modularity.
- The five rings (Ring 0 through Ring 4) predict how soon each field will experience significant agentification.
- This isn't about replacement — it's about which *skills* become valuable. Routine work becomes less valuable; judgment, verification, and direction-setting become more valuable.
- Fields move through rings unevenly. Specific tasks agentify faster than others.
- Verification becomes *more* important as you move outward through the rings, not less.
- The skills taught in this course (specification, understanding, verification, iteration) are universally valuable across all rings.
- You are at the beginning of a shift that will affect billions of people. The time to understand it and prepare is now.

---

Choose your specialised track →
