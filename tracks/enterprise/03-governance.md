# E3. Governance Patterns

## The AI-as-Employee Framing

Organisations already know how to manage workers with access to sensitive information. The AI-as-employee framing applies existing governance concepts to AI:

| Employee Concept | AI Equivalent |
|------------------|---------------|
| Job description | System prompt defining scope and purpose |
| Hiring/onboarding | Deployment and configuration |
| Access permissions | Tool availability, data boundaries |
| Manager oversight | Human review of outputs |
| Confidentiality agreement | Data processing agreement |
| Audit trail | Action and access logging |
| Performance review | Quality assessment, error tracking |
| Termination | Access revocation, data deletion |

This framing helps stakeholders understand AI governance using concepts they already know.

## Governance Patterns

### Pattern 1: Tiered Access

Different AI deployments for different sensitivity levels:

```
┌─────────────────────────────────────────────────────────────┐
│                    TIERED AI ACCESS                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  TIER 1: Public/General                                     │
│  ├── Access: Public information only                        │
│  ├── Actions: Read, summarise, draft                        │
│  └── Example: General research assistant                    │
│                                                             │
│  TIER 2: Internal                                           │
│  ├── Access: Internal documents, non-sensitive              │
│  ├── Actions: Read, draft, some automation                  │
│  └── Example: Team productivity assistant                   │
│                                                             │
│  TIER 3: Confidential                                       │
│  ├── Access: Confidential data with approval                │
│  ├── Actions: Read only, human executes all actions         │
│  └── Example: Legal document review assistant               │
│                                                             │
│  TIER 4: Restricted                                         │
│  ├── Access: Case-by-case, fully isolated environment       │
│  ├── Actions: Heavily constrained, full audit               │
│  └── Example: M&A due diligence (air-gapped)               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Pattern 2: Human-in-the-Loop Gates

Define which actions require human approval:

**Always autonomous (no approval needed):**
- Reading provided documents
- Generating summaries
- Answering questions about provided content
- Drafting internal documents

**Approval required:**
- Sending external communications
- Modifying shared documents
- Accessing additional data sources
- Taking actions in other systems

**Never autonomous (human must execute):**
- Financial transactions
- Legal commitments
- Personnel decisions
- Production system changes

```
EXERCISE:
For an AI assistant helping with customer support:

1. List 5 actions it might take
2. Categorise each as: autonomous / approval required / human executes
3. What's the criteria you used to decide?
```

### Pattern 3: Separation of Duties

Different AI instances for different functions:

| Function | AI Configuration | Rationale |
|----------|-----------------|-----------|
| Research | Read-only, broad access | Needs to explore |
| Drafting | Write access, narrow scope | Needs to create |
| Review | Read-only, critical eye prompt | Independence |
| Execution | Action access, narrow scope | Controlled impact |

This prevents a single AI deployment from having excessive capability.

### Pattern 4: Time-Bounded Access

Access that expires:

- **Project-based:** AI can access project files only during project
- **Session-based:** Access revoked at session end
- **Approval-based:** Each access requires fresh approval

Useful for sensitive projects (M&A, investigations, audits).

### Pattern 5: Audit and Review Cycles

Regular assessment of AI deployments:

| Frequency | Review |
|-----------|--------|
| Continuous | Automated logging and alerting |
| Weekly | Sample review of AI actions |
| Monthly | Usage patterns, error rates |
| Quarterly | Policy review, access audit |
| Annually | Full governance assessment |

## The Compliance Conversation

When advocating for AI use in risk-averse organisations:

### Frame It Right

**Don't say:** "AI is safe, don't worry"
**Do say:** "Here's how we'll govern AI use to meet our compliance requirements"

**Don't say:** "Everyone's using it"
**Do say:** "Here's our risk assessment and mitigation plan"

**Don't say:** "Trust me"
**Do say:** "Here's how we'll audit and verify"

### Common Compliance Concerns and Responses

| Concern | Response |
|---------|----------|
| "Where does the data go?" | "Here's our data flow diagram and DPA" |
| "What if it makes a mistake?" | "Here's our human review process and escalation path" |
| "How do we audit it?" | "Here's our logging configuration and review schedule" |
| "What about regulations?" | "Here's how we map to [specific regulation] requirements" |
| "Who's responsible?" | "Here's our RACI matrix for AI governance" |

### Building the Business Case

1. **Identify the need:** What legitimate business problem does AI solve?
2. **Assess the risk:** What's the worst case? How likely?
3. **Design controls:** How do we mitigate those risks?
4. **Document everything:** Trust architecture, channel selection, review process
5. **Propose a pilot:** Limited scope, full governance, clear metrics
6. **Review and expand:** Evidence-based scaling

```
QUIZ:
Your compliance team is concerned about AI accessing customer data. Which approach is most likely to succeed?

* Argue that AI is safe and they're being overly cautious
* Wait for them to approve AI without addressing concerns
*! Propose a pilot with full audit logging, human review, and clear boundaries
* Use AI anyway and ask forgiveness later
FEEDBACK:A well-governed pilot with clear controls addresses concerns directly and builds trust through evidence.
```

## Incident Response

What happens when something goes wrong?

### AI Incident Categories

| Category | Example | Response |
|----------|---------|----------|
| **Data exposure** | AI output included confidential data | Assess scope, notify stakeholders, review access |
| **Incorrect action** | AI sent wrong email | Correct the action, review approval process |
| **Hallucination harm** | AI provided false information acted upon | Assess impact, strengthen verification |
| **Compliance breach** | Data processed in wrong jurisdiction | Legal review, vendor escalation |
| **Shadow AI discovery** | Employee used unapproved tool | Assess exposure, reinforce training |

### Incident Response Process

1. **Detect:** How was the incident identified?
2. **Contain:** Stop ongoing harm
3. **Assess:** What happened? What's the impact?
4. **Remediate:** Fix the immediate problem
5. **Review:** What governance gap allowed this?
6. **Improve:** Update controls to prevent recurrence
7. **Document:** Record for future reference

## Governance Documentation

### Minimum Documentation Set

1. **AI Use Policy** — What's allowed, what's not
2. **Channel Inventory** — Approved tools and their boundaries
3. **Trust Architecture** — Per-deployment access/action/retention/accountability
4. **Review Schedule** — When and how AI use is audited
5. **Incident Response** — What to do when things go wrong
6. **Training Materials** — How employees should use AI

### Policy Template Outline

```
AI USE POLICY

1. PURPOSE
   Why we have this policy

2. SCOPE
   Who and what this covers

3. APPROVED CHANNELS
   List of approved AI tools and their use cases

4. DATA CLASSIFICATION
   What data can be used with AI, by classification

5. PROHIBITED USES
   What you must not do with AI

6. HUMAN OVERSIGHT REQUIREMENTS
   When human review is required

7. INCIDENT REPORTING
   How to report AI-related concerns

8. RESPONSIBILITIES
   Who's responsible for what

9. REVIEW AND UPDATES
   How often this policy is reviewed
```

## Key Takeaways

- The AI-as-employee framing makes governance intuitive
- Tiered access matches AI capability to data sensitivity
- Human-in-the-loop gates control consequential actions
- Regular audit cycles catch drift and issues
- Frame compliance conversations around controls, not reassurance
- Document everything: policy, architecture, incidents
- Incident response should be planned before you need it

---

Congratulations! You've completed the Enterprise Track.

Consider also:
- **Developer Track** — If you're building AI integrations
- **Academic Track** — If you do research or literature-heavy work
