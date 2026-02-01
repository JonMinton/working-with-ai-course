# E1. Trust Architecture

## The Enterprise AI Anxiety

When organisations consider agentic AI, a specific anxiety emerges that's different from previous technology concerns:

> "We've let a stranger into the office. They can open any filing cabinet, read any document, send emails as us. They're very capable but we don't really know them. They don't have a contract. They might tell others what they saw."

This anxiety is understandable. Agentic AI:
- Browses, reads, and explores (not just processes what you feed it)
- Makes decisions about what to look at
- Takes actions with consequences
- Feels like an *entity* with initiative

Previous AI tools felt like tools. Agentic AI feels like... something else.

## The Trust Architecture Framework

Every AI deployment involves decisions across four dimensions:

### 1. Access — What can the agent see?

| Level | Description | Example |
|-------|-------------|---------|
| **Everything** | Full access to all systems | Dangerous — rarely appropriate |
| **Role-scoped** | Access matching a job function | "Like a marketing assistant" |
| **Task-scoped** | Only what's needed for current task | Provided per-request |
| **Nothing persistent** | Ephemeral context only | Chat-based, no file access |

**Questions to ask:**
- What data classifications exist in our organisation?
- Which can this AI access?
- Who decides what's in scope?

### 2. Actions — What can the agent do?

| Level | Description | Risk |
|-------|-------------|------|
| **Read only** | Can view, summarise, analyse | Low |
| **Draft** | Can create outputs, human executes | Low-medium |
| **Execute with approval** | Can act, but human approves each action | Medium |
| **Autonomous execution** | Acts without per-action approval | High |

**Questions to ask:**
- What actions could cause harm if wrong?
- Which require human judgment?
- What's the blast radius of a mistake?

### 3. Retention — What happens to data after the task?

| Level | Description | Implication |
|-------|-------------|-------------|
| **Training data** | Used to improve the model | Avoid for enterprise |
| **Conversation memory** | Retained for continuity | Check policies |
| **Audit logs only** | Actions logged, content deleted | Often acceptable |
| **Immediate deletion** | Nothing persists | Most private |

**Questions to ask:**
- Does the vendor train on our data?
- What's the retention policy?
- Can we audit what was processed?
- Can we delete on demand?

### 4. Accountability — Who's responsible?

| Question | Needs Clear Answer |
|----------|-------------------|
| Who approved this AI deployment? | Management chain |
| Who reviews outputs before action? | Named individuals |
| Who's responsible if something goes wrong? | Cannot be "the AI" |
| How are incidents reported? | Process documented |

## Mapping to Existing Frameworks

Your organisation already has frameworks for managing access and accountability. AI should map to them:

| Existing Concept | AI Equivalent |
|------------------|---------------|
| Job description | System prompt defining scope and purpose |
| Access permissions | Tool availability, file system boundaries |
| Manager | Human who reviews outputs, approves actions |
| Confidentiality agreement | Data processing agreement, no-training clauses |
| Audit trail | Logging of all actions and data accessed |
| Security clearance | Tiered access levels |
| Need-to-know | Context provided per-task, not global access |
| Performance review | Assessment of output quality, error rates |
| Termination | Revoke access, delete history |

```
EXERCISE:
For an AI assistant being deployed to help your HR team with recruitment screening:

1. What access level is appropriate?
2. What actions should it be able to take?
3. What retention policy makes sense?
4. Who is accountable for its decisions?

Write out a trust architecture for this use case.
```

## The "Capable Temp" Mental Model

A useful framing for stakeholders:

> **"A very capable temp who starts fresh every day, works only with what you hand them, and shreds everything when they leave."**

This captures:
- **Capability:** More than a simple tool
- **No persistence:** Fresh each day
- **Scoped access:** Only what you provide
- **No retention:** Shreds when done

**What the temp DOESN'T have:**
- Discretion to recognise sensitive situations
- Judgment to deviate from instructions
- Memory of previous engagements
- Loyalty or employment relationship

```
QUIZ:
A colleague says: "The AI saw our salary data last week, so it probably still knows it." How do you respond?

* "Yes, we should assume it remembers everything"
* "Don't worry, AI doesn't remember anything"
*! "It depends on our deployment — let's check the retention settings and whether it was through an approved channel"
* "We should stop using AI entirely"

FEEDBACK: The answer depends on the specific deployment's persistence settings. This is why understanding trust architecture matters.
```

## Designing Trust Boundaries

### Principle: Minimum Necessary Access

The AI should have access to exactly what it needs for the current task — no more.

**Anti-pattern:** "Let's give the AI access to everything so it can help with anything"

**Better:** Task-specific context provision

### Principle: Human-in-the-Loop for Consequential Actions

Actions with significant impact should require human approval:
- Sending external communications
- Modifying production systems
- Accessing sensitive data categories
- Financial transactions

### Principle: Audit Everything

If you can't audit it, you can't govern it.
- Log what data was accessed
- Log what actions were taken
- Log who approved what
- Retain logs according to compliance requirements

### Principle: Fail Closed

When uncertain, the AI should:
- Ask rather than assume
- Refuse rather than guess
- Escalate rather than proceed

## Trust Architecture Template

For any AI deployment, document:

```
AI DEPLOYMENT: [Name/Purpose]

ACCESS:
- Data classifications accessible: [list]
- Systems accessible: [list]
- Data explicitly excluded: [list]

ACTIONS:
- Read-only: [list]
- Draft (human executes): [list]
- Execute with approval: [list]
- Autonomous: [list]

RETENTION:
- Conversation data: [policy]
- Processed documents: [policy]
- Audit logs: [policy]

ACCOUNTABILITY:
- Deployment owner: [name]
- Output reviewer: [name/role]
- Incident escalation: [process]

REVIEW SCHEDULE: [frequency]
```

## Key Takeaways

- Trust architecture makes explicit decisions about access, actions, retention, and accountability
- Map AI governance to existing organisational frameworks
- The "capable temp" mental model helps stakeholders understand scope
- Minimum necessary access, human-in-the-loop, and audit trails are foundational
- Document trust architecture for every deployment

---

Next: **E2. Approved Channels** →
