# Case Studies: Agentification in Practice

Real-world examples of organisations adopting AI agents at scale. Each illustrates concrete implementation choices and lessons transferable to your own track.

**A note in the spirit of Module 5 (Verification):** the examples below are based on public reporting by the organisations themselves or by major business press, mostly from 2023–2025. Vendor-reported and self-reported figures tend to be flattering — they describe early adopters' best outcomes, not averages. We've kept quantitative claims to what was publicly reported, marked them as *reported*, and dropped examples we couldn't trace to a source. Treat every number here as a claim to weigh, not a fact to repeat — and treat that habit as part of the course.

---

## A&O Shearman × Harvey: Lawyers Directing Agents

**Who:** A&O Shearman (formerly Allen & Overy), a global law firm, was one of the earliest large firms to deploy Harvey — a legal AI platform — at scale, starting in late 2022 and expanding through the merger years.

**What they did:** Rather than simply automating document review, the firm used Harvey for first-pass work across research, drafting, and due diligence, with lawyers shifting from *doing* the first pass to *directing and checking* it. Output enters a human review gate before anything reaches a client.

**What was reported:** Meaningful weekly time savings per lawyer, broad adoption across practice areas, and expansion rather than retrenchment of the programme over time.

**Lessons:**
- Agentic AI doesn't remove professional judgment — it relocates it to specification and review.
- Lawyer-as-director-of-agents proved more sustainable than lawyer-versus-AI framings.
- Specialised, domain-tuned AI found traction in a regulated profession faster than generic chat tools did.

**Relevant tracks:** Enterprise, Leadership

---

## Goldman Sachs: A Firmwide AI Assistant

**Who:** Goldman Sachs, with tens of thousands of employees, rolled out its proprietary GS AI Assistant firmwide in 2025 after a large-scale pilot.

**What they did:** The assistant integrates with internal systems — documents, email, compliance tooling — and handles routine drafting, summarisation, and retrieval inside the firm's security boundary, rather than employees pasting material into external chat tools.

**What was reported:** Rapid, near-universal adoption, and large reductions in time spent on routine administrative and drafting tasks.

**Lessons:**
- Firmwide adoption followed deep integration with internal systems — not a chatbot bolted on the side.
- An *approved channel* that's genuinely convenient is the most effective shadow-AI prevention there is (compare Enterprise module E2).
- Pilot first, at meaningful scale: feedback from thousands of users shaped the firmwide rollout.

**Relevant tracks:** Operations, Enterprise, Leadership

---

## Morgan Stanley: Assistants for Advisors

**Who:** Morgan Stanley's wealth management division, with thousands of financial advisors, deployed OpenAI-based assistants from 2023: first a knowledge-base assistant, then *Debrief*, which drafts meeting summaries and follow-ups.

**What they did:** The assistant connects to the firm's internal research corpus, so advisors query decades of institutional knowledge conversationally. Debrief turns client-meeting recordings into draft notes and actions — with advisor review before anything is filed or sent.

**What was reported:** Very high adoption among advisor teams — described as among the fastest tool uptakes in the firm's history — and substantially faster document retrieval and meeting follow-up.

**Lessons:**
- Agents aimed at a *specific, painful bottleneck* (search, meeting notes) see faster adoption than general-purpose tools.
- Retrieval from a curated internal corpus (rather than the model's training data) is what made answers trustworthy enough to use — the weights-vs-context distinction from core Module 1, applied at firm scale.
- Human review gates stayed in place even at high adoption.

**Relevant tracks:** Operations, Enterprise

---

## Commonwealth Bank of Australia: Making AI Tools Standard Kit

**Who:** CBA, Australia's largest bank, ran one of the larger enterprise Copilot deployments from 2024, spanning Microsoft 365 Copilot and GitHub Copilot across thousands of staff.

**What they did:** Deployed AI tooling across multiple functions simultaneously — engineering, operations, compliance — treating it as standard kit rather than an experiment, with internal integration so tools could work against bank systems and data under governance controls.

**What was reported:** A large majority of participating staff said they wouldn't want to work without the tools; shorter code-review cycles; faster resolution of routine queries.

**Lessons:**
- Deploying across *diverse* functions at once created network effects a single-team pilot can't.
- "Mandatory-feeling" adoption arrived when the tools reduced friction in several workflows simultaneously.
- Governance and enablement were run together, not sequentially.

**Relevant tracks:** Developer, Operations, Leadership

---

## The Big 4: Redefining Junior Roles Around Agents

**Who:** The major accounting firms (PwC, KPMG, Deloitte, EY) have each made major, publicly announced AI investments and are restructuring early-career work around AI tooling.

**What they did:** Repositioned junior accountants from performing routine sampling, reconciliation, and variance work towards directing and validating AI-assisted versions of those tasks, and rebuilt training accordingly — recruitment messaging now emphasises AI collaboration skills.

**What was reported:** Substantially shorter cycle times on routine audit tasks, and a deliberate strategy of upskilling rather than headcount reduction in audit teams — though the long-term shape of entry-level roles remains genuinely contested and is worth watching rather than assuming.

**Lessons:**
- The entry-level question — "if agents do the junior work, how do juniors learn?" — is live in every professional field; the Big 4 answer is to make agent direction and verification *the* junior skill.
- Public commitments accelerate internal adoption by making reversal expensive.

**Relevant tracks:** Enterprise, Leadership

---

## Ethan Mollick: Giving the Field Its Vocabulary

**Who:** Ethan Mollick, a Wharton professor, became one of the most-read voices on practical AI through his research, his book *Co-Intelligence*, and the "One Useful Thing" newsletter.

**What he did:** With collaborators, proposed clear working frameworks for AI in learning and work — including describing distinct roles AI can play for a learner (tutor, coach, mentor, teammate, tool, simulator, student) — and tested them in real classrooms, publishing accessible guidance alongside academic work.

**What happened:** His frameworks became common vocabulary in educational AI; institutions worldwide drew on them when redesigning curricula and policy.

**Lessons:**
- Clear mental models beat vague "AI can help" assertions — naming distinct roles changes how people design their use of AI.
- Publishing in accessible venues moved practice faster than journal-only publication.
- One person with hands-on experiments and clear writing can shape a field's thinking.

**Relevant tracks:** Education, Leadership

**Further reading:** [One Useful Thing](https://www.oneusefulthing.org/)

---

## GitHub Copilot: Agent Adoption at Ecosystem Scale

**Who:** GitHub Copilot is the largest-scale deployment of AI assistance in software development; GitHub reported passing 20 million users in 2025, with adoption across most of the largest enterprises.

**What they did:** Evolved Copilot from line-by-line code completion into an agent ecosystem: assigning whole issues to coding agents, agent-driven code review, and integration with the native development workflow (pull requests, issues, CI) so agent work lands through the same review gates as human work.

**What was reported:** Faster pull-request cycles, improved review coverage, and shorter onboarding for new developers — alongside an industry-wide debate, still unresolved, about long-term effects on code quality and junior skill development.

**Lessons:**
- Agent work succeeded by entering through *existing* review gates, not around them.
- Software development is the leading indicator (Ring 0 in core Module 7): the patterns here — spec-driven work, human review gates, agents as colleagues with permissions — are previews of other fields' near future.
- Scale brings genuine open questions as well as benefits; honest accounts include both.

**Relevant tracks:** Developer, Leadership

---

## Reading These as a Set

Across every case: the organisations that got value **integrated AI inside their trust boundary, kept human review gates, aimed at specific bottlenecks, and treated adoption as an organisational change project** rather than a software purchase. Not one of them succeeded by telling staff "go use a chatbot."

And one meta-lesson: when this page was first drafted (by an AI, as it happens), it included a vivid, detailed case study that turned out to be unverifiable — so it was removed. The fluency of a story is not evidence that it happened. That is Module 5 in a sentence.
