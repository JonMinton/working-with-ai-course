# L3. Risk & Reputation

## The Failure Taxonomy

AI can fail in many ways. Leaders need to know the category of failure before deciding how to respond.

### Hallucination

**What it is:** AI generates plausible-sounding but false information with confidence. (Core Module 1: How AI Actually Works explains why this failure mode is inherent to how language models generate text.)

**Characteristics:**
- Facts sound right but aren't (wrong dates, invented sources, fabricated quotes)
- Often more elaborate than the true information would be
- AI doesn't "know" it's wrong

**Real-world example:**
- AI generates contract summary citing a clause that doesn't exist
- Customer service AI invents product features that don't exist
- Report includes references to studies that aren't real

**Organisational harm:**
- Low immediate visibility (person reads it, uses it, doesn't fact-check)
- Medium-term realisation ("Wait, did we have that feature?")
- Reputational if it's external-facing

**How to mitigate:**
- Use AI for drafting, not final product (for anything fact-dependent)
- Train teams: "verify any specific claim — don't assume AI is accurate"
- Audit trail: "Who approved this output as factually correct?"
- Higher-stakes use = stricter verification

### Bias and Discrimination

**What it is:** AI decisions systematically advantage or disadvantage groups.

**Characteristics:**
- Often invisible (looks like "objective" data or standard criteria)
- May reflect historical discrimination in training data
- May emerge from subtle feature interactions
- Can be amplified through automation (applied at scale without review)

**Real-world example:**
- Hiring AI screens out candidates from certain backgrounds
- Loan approval AI has different acceptance rates by ethnicity (unintentionally)
- Customer service AI prioritises certain customer segments
- Content recommendations create filter bubbles

**Organisational harm:**
- Regulatory (discrimination law violations)
- Reputational (when discovered)
- Operational (losing talented applicants, offending customers)
- Ethical (if your values matter)

**How to mitigate:**
- Test for bias before deployment (not after discovery)
- Maintain human review for decisions affecting people: hiring, lending, admission, benefits
- Audit outcomes: *Is the AI decision distribution what we'd expect?*
- Transparency: if AI is involved in a consequential decision, people should know
- Proportional response: low-stakes recommendation = light review; high-stakes decision = rigorous audit

```
EXERCISE:
You're deploying AI to screen job applications. What human review process makes sense?

1. Define what "bias" would look like in your context (what would be concerning?)
2. How will you detect it? (What data will you track?)
3. Who reviews screening results before decisions?
4. How often do you audit for unexpected patterns?
5. What triggers a pause/investigation?
```

### Data Leakage and Confidentiality Breach

**What it is:** Sensitive information is exposed through AI systems (to the vendor, other users, the AI's training data, or publicly).

**Characteristics:**
- May happen silently (you don't know data was transmitted)
- Vendor may retain or use your data
- Data persists in logs or training datasets
- May be required for AI to work (API calls with data content)

**Real-world example:**
- Engineer pastes code containing database credentials into ChatGPT to debug
- Team shares customer data with an AI tool to analyse patterns
- Internal meeting transcripts fed to AI summarisation service
- Sensitive information included in AI-generated documents sent externally

**Organisational harm:**
- Regulatory (GDPR, industry-specific data protection)
- Financial (penalties, notification costs)
- Reputational (if clients discover their data was shared)
- Operational (leaked credentials, data theft)

**How to mitigate:**
- Data handling policy: "What data can be shared with which tools?"
- Training: real examples of what data is sensitive (not just "don't share secrets")
- Vendor agreements: explicit data retention and usage terms
- Technical controls: proxy/gateway to inspect what's being sent
- Process: create "clean" versions of data for AI (remove PII/secrets before sending)
- Incident response: know how to revoke access and assess exposure

(If your organisation needs to build these controls out properly, the Enterprise track covers them in depth: **E2. Approved Channels** for channel-level data handling and **E4. Monitoring, Compliance & Continuous Evaluation** for redaction patterns and compliance auditing. As a leader, your job is to ensure someone owns this — not to design it yourself.)

### Model/Vendor Failure

**What it is:** The AI service or vendor fails — downtime, quality degradation, vendor shutdown.

**Characteristics:**
- Beyond your control (vendor decision)
- May happen suddenly
- May degrade gradually (quality drops over time)
- May be regional (some areas affected, others not)

**Real-world example:**
- AI service has extended outage; your workflow stalls
- Vendor changes pricing dramatically or limits usage
- Vendor goes out of business
- Vendor is acquired and discontinues the product

**Organisational harm:**
- Operational (can't do the work you've built around AI)
- Financial (sunk investment in integration, retraining)
- Reputational (if you've promised customers or partners the capability)

**How to mitigate:**
- Avoid single-vendor dependency (use multiple providers for critical functions)
- Require data portability (can you export and move easily?)
- Maintain fallback process (can you do the work without AI if needed?)
- Contract terms: what happens if service degrades or they change pricing?
- Monitor vendor health and product roadmap

### Brand/Reputational Damage

**What it is:** AI actions or statements damage your organisation's reputation.

**Characteristics:**
- Often unexpected (you didn't anticipate that would cause a problem)
- Public visibility (customers, media, regulators notice)
- Hard to control once public (can't unsay or undo easily)

**Real-world example:**
- AI-written customer response sounds dismissive or offensive
- Chatbot makes a political statement
- AI recommendation system excludes or demeans a group
- AI tool is used unethically and organisation is blamed

**Organisational harm:**
- Media coverage and social media backlash
- Customer churn
- Partner and employee relations
- Regulatory scrutiny

**How to mitigate:**
- Tone and values training: AI should reflect your organisation's voice
- External-facing AI: stricter review and safety testing
- Escalation path: if something "feels wrong," it gets reviewed before going public
- Clear accountability: who approved this going public?
- Response plan: if something goes wrong publicly, who responds, how, when?

## Risk Proportionality: Not Everything Needs Enterprise Controls

A common mistake: applying the same risk controls to low-stakes and high-stakes uses.

### Three Levels of Risk Response

| Dimension | Low Stakes | Medium Stakes | High Stakes |
|-----------|-----------|----------|----------|
| **Use case** | Brainstorming, draft generation, internal summaries | Customer-facing content, hiring support, financial analysis | Legal decisions, medical advice, regulatory decisions, public statements |
| **Verification** | Quick human scan | Formal review process | Rigorous audit, possibly third-party review |
| **Approval** | Individual user decides | Manager or team lead | Director or legal/compliance |
| **Vendor control** | Self-service tools acceptable | Contractual data protections | Enterprise agreement, stricter terms |
| **Audit trail** | Basic logging | Structured logging | Full audit trail, retention policy |
| **Timeline** | Days | Days to weeks | Weeks to months |

```
QUIZ:
You need to deploy AI for customer service replies to inbound email. This is:

* Low stakes (just communication)
*! Medium to high stakes (public-facing, affects customer relationship)
* Low stakes (it's internal automation)
* Decision depends on response types; let's categorise first

FEEDBACK: Customer-facing communication is medium-to-high stakes. It's public-facing and affects customer relationships. Some email types might be truly low-stakes (automated acknowledgment), others high-stakes (resolving complaints). Calibrate controls by category.
```

## Incident Preparedness

Most organisations focus on incident *response* (what to do *after* something goes wrong). Incident *preparedness* means being ready *before* it happens.

(For the governance-level incident categories and the monitoring that detects incidents, see the Enterprise track: E3. Governance Patterns and E4. Monitoring, Compliance & Continuous Evaluation. This module covers the leadership view: preparedness and public communication.)

### Incident Preparedness Checklist

**Identify** — What counts as an incident?

- Document scenarios: "If AI gives wrong medical advice" / "If customer data is leaked" / "If chatbot says something offensive"
- Define severity levels: Critical (immediate brand damage, legal exposure), Major (affects operations, some customer impact), Minor (easily reversed, low impact)
- Assign owners: Who notices first? Who makes the call?

**Contain** — How do you stop the harm spreading?

- Kill switch: How do you take the AI system offline if needed?
- Data: How do you limit exposure (e.g., stop it from sending to customers)?
- Comms: Who tells whom, and when?

**Investigate** — How do you understand what happened?

- Logs: Do you have detailed logs of what the AI did, when?
- Data: Can you retrieve examples of the failure?
- Timeline: Do you have system monitoring that shows when things changed?

**Communicate** — How do you tell stakeholders?

- First 24 hours: Internal (leadership, affected teams)
- 24–48 hours: Customers/partners (if appropriate)
- Ongoing: Transparent updates on what you've done
- Public statement: Consider tone, honesty, and next steps

**Learn** — How do you prevent recurrence?

- Root cause: What specifically went wrong? (Not "AI failed" — *how*?)
- System failure: Did your process miss this? (E.g., no one reviewed the output, no one noticed it was deployed)
- Vendor failure: Did the tool behave as expected? Should you have tested this?

### A Simple Incident Response Template

```
INCIDENT: [Name/Date]

SEVERITY: [Critical / Major / Minor]

TIMELINE:
- [Time]: Incident detected by [who/how]
- [Time]: Escalation to [role]
- [Time]: System taken offline / action taken
- [Time]: Customer communication

ROOT CAUSE:
- AI failure: [specific failure mode]
- Process failure: [what did we not catch]
- Vendor responsibility: [if applicable]

CONTAINMENT:
- Steps taken to limit harm: [list]
- Affected parties: [scope]

RESOLUTION:
- What we did to stop it happening
- What we're monitoring going forward

COMMUNICATION:
- Internal: [what we said to staff]
- Customer: [what we told customers]
- Public: [if any public statement]

LEARNING:
- System change: [process or control added]
- Training: [if relevant]
- Policy change: [if needed]
```

## Public Communication When AI Goes Wrong

How you talk about an incident matters enormously.

### Principles

**1. Honest.** Don't minimise or deflect. "We made a mistake" lands better than "the system had a minor edge case."

**2. Specific.** Name what happened, not abstractions. "Our AI gave bad medical advice on a specific condition" not "the AI experienced a hallucination event."

**3. Accountable.** Own it. "We should have tested this more thoroughly" not "the vendor's model was imperfect."

**4. Action-oriented.** What are you doing to fix it? What are you doing to prevent it happening again?

**5. Transparent.** If you don't know something, say so. "We're still investigating" is better than guessing.

### Example (Good)

> "On [date], our customer service AI incorrectly quoted a product feature that doesn't exist in our product. This affected [number] customers. We've taken the following steps:
>
> 1. Reviewed and corrected all instances
> 2. Retrained the AI with our actual product specification
> 3. Added a verification step for product feature claims
> 4. Informed affected customers with a [credit/apology]
>
> This was our error. We should have tested this more thoroughly before deployment. We're committed to preventing this in future."

### Example (Poor)

> "A customer service AI experienced a hallucination event affecting a small number of customer interactions. The system is working as designed. We have engaged our vendor partners to investigate."

(Defensive, vague, passes blame)

```
QUIZ:
An AI-written marketing email from your company contains a factually false claim that gets posted on social media. You should:

* Hope it doesn't spread and avoid drawing attention to it
* Issue a statement saying AI is "experimental" and not representative
*! Acknowledge the error quickly, explain how it happened, describe the fix, and commit to preventing it
* Blame the vendor publicly

FEEDBACK: Quick acknowledgment and transparency builds trust. Defensive responses or deflection amplify the problem. People forgive honest mistakes handled well; they don't forget defensiveness or spin.
```

## Key Takeaways

- Know your failure modes: hallucination, bias, data leakage, vendor failure, brand damage
- Apply risk controls proportionally (low-stakes brainstorming ≠ high-stakes medical advice)
- Prepare for incidents before they happen, not after
- Document incident procedures: identify, contain, investigate, communicate, learn
- Communicate honestly and specifically when things go wrong
- Build audit trails so you can understand what happened

---

Next: **L4. Vendor & Build Decisions** →
