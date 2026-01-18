# E2. Approved Channels ("Kosher Tubes")

## The Channel Problem

Here's something that confuses many users:

> The same AI model, accessed through different channels, has **completely different data handling**.

Claude through an enterprise agreement is not the same as Claude through a personal web login — even though the underlying model is identical.

## Model vs. Deployment

```
┌─────────────────────────────────────────────────────────────┐
│                     THE SAME MODEL...                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────────┐     ┌─────────────────────┐       │
│  │   APPROVED CHANNEL  │     │  UNAPPROVED CHANNEL │       │
│  │                     │     │                     │       │
│  │ • Enterprise        │     │ • Personal web      │       │
│  │   agreement         │     │   interface         │       │
│  │ • Data doesn't      │     │ • May train on      │       │
│  │   train model       │     │   your inputs       │       │
│  │ • Audit logging     │     │ • No audit          │       │
│  │ • SSO/identity      │     │ • Personal          │       │
│  │ • IT/compliance     │     │   account           │       │
│  │   approved          │     │ • Shadow IT         │       │
│  │                     │     │                     │       │
│  │ e.g., Copilot,      │     │ e.g., claude.ai     │       │
│  │ Azure OpenAI,       │     │ personal login,     │       │
│  │ enterprise API      │     │ ChatGPT free tier   │       │
│  └─────────────────────┘     └─────────────────────┘       │
│                                                             │
│          Same underlying model capability                   │
│          Completely different risk profile                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## What Makes a Channel "Approved"

An approved channel typically includes:

| Requirement | What It Means |
|-------------|---------------|
| **Data Processing Agreement** | Legal terms governing how data is handled |
| **No-training clause** | Your inputs won't improve the model |
| **Audit logging** | Record of what was processed |
| **Identity management** | SSO, known users, access controls |
| **Geographic compliance** | Data processed in appropriate jurisdictions |
| **Retention controls** | Clear policies on how long data is kept |
| **Incident response** | Process if something goes wrong |

## Why This Matters

**Scenario:** An employee pastes confidential contract terms into a personal ChatGPT session to "help summarise."

**What happened:**
- Confidential data entered an unapproved system
- No audit trail exists
- Data may be used for training
- Potential compliance violation
- No recourse if data is misused

**With an approved channel:**
- Same action would be logged
- Data handling governed by agreement
- Audit trail for compliance
- Clear accountability

## The Shadow AI Problem

**Shadow AI** is like shadow IT — employees using unapproved tools because:
- Approved tools are slower to access
- Personal tools have features enterprise versions lack
- They don't understand the distinction matters
- "It's just a quick question"

**Why employees do it:**
- Approved tools require login/VPN
- Personal tools are already open
- No visible difference in capability
- Urgency ("I just need a quick answer")

**The risk:**
- Confidential data leaks
- No audit trail
- Compliance violations
- Impossible to govern what you can't see

```
QUIZ:
An employee needs to quickly summarise a client contract. They have access to an enterprise AI tool (requires SSO login) and have ChatGPT open in another tab. What should they do?

* Use ChatGPT — it's faster and the contract isn't that sensitive
* Use ChatGPT — all AI is basically the same
*! Use the enterprise tool — client contracts should only go through approved channels
* Don't use AI at all
FEEDBACK:Client contracts are confidential data. Even if using the enterprise tool is slightly slower, it's the only appropriate channel for work data.
```

## Reading the Terms

When evaluating AI channels, look for:

### Must-Haves for Enterprise Use

- [ ] **No training on inputs** — "We do not train on customer data"
- [ ] **Data processing agreement available** — Legal terms you can review
- [ ] **Clear retention policy** — How long is data kept?
- [ ] **Deletion capability** — Can you request data deletion?
- [ ] **Geographic clarity** — Where is data processed?

### Red Flags

- "We may use inputs to improve our services" (training clause)
- No DPA available
- Vague retention ("as long as necessary")
- No deletion process
- Data processed in jurisdictions that concern you

### Questions to Ask Vendors

1. Do you train on enterprise customer data?
2. Where is data processed and stored?
3. What's the retention period?
4. How do we get audit logs?
5. What's your incident response process?
6. Can we get a DPA?

## The Decision Tree

When an employee wants to use AI for a work task:

```
Is this work-related data?
├── NO → Personal tools probably fine
└── YES ↓

Is there an approved AI tool for this?
├── YES → Use the approved tool
└── NO ↓

Is this data classified as sensitive/confidential?
├── YES → Do NOT use unapproved AI; escalate need
└── NO ↓

Is this truly non-sensitive?
├── YES → Consider if AI is even needed
└── UNSURE → Treat as sensitive; escalate
```

## Building a Channel Inventory

Document your organisation's approved channels:

| Channel | Provider | Use Cases | Data Classifications Allowed | Approval Status |
|---------|----------|-----------|------------------------------|-----------------|
| Microsoft Copilot | Microsoft | Office productivity | Internal, some confidential | Approved |
| Azure OpenAI | Microsoft | Development, analysis | Per-project approval | Approved with restrictions |
| Claude.ai (enterprise) | Anthropic | Research, writing | Internal only | Approved |
| ChatGPT Free | OpenAI | N/A | None | Not approved for work |

```
EXERCISE:
Create a channel inventory for your organisation (or a hypothetical one):

1. List 3-4 AI tools employees might use
2. For each, identify: approved/unapproved, what data is allowed
3. Identify gaps: what legitimate needs have no approved channel?
```

## Addressing Shadow AI

Prohibition alone doesn't work. Address the underlying needs:

### Why Approved Tools Get Bypassed

| Reason | Solution |
|--------|----------|
| Too slow to access | Streamline SSO, reduce friction |
| Missing features | Evaluate feature requests, add tools |
| Users don't understand risk | Training and communication |
| "Everyone does it" | Clear policy, visible enforcement |

### Making Approved Channels Attractive

- Fast access (minimal login friction)
- Feature parity with consumer tools
- Clear guidance on what's allowed
- Quick response to feature requests
- Visible leadership use

## Key Takeaways

- The same model through different channels has different data handling
- Approved channels have legal agreements, no-training clauses, audit logs
- Shadow AI is a real risk — employees use unapproved tools for convenience
- Read the terms: look for training clauses, retention, DPAs
- Document your channel inventory
- Address shadow AI by making approved channels attractive, not just prohibiting alternatives

---

Next: **E3. Governance Patterns** →
