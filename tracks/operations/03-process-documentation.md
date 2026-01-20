# O3. Process Documentation

## The Documentation Problem

Every organisation has processes that:
- Live in people's heads
- Are described differently by different people
- Aren't written down (or docs are outdated)
- Break when the person who knows them leaves

AI can help capture, document, and improve processes.

## Capturing Tribal Knowledge

### The Interview Approach

> "I'm going to describe how we handle customer refunds. Ask me clarifying questions as I go, then compile it into a step-by-step procedure.
>
> [Describe the process roughly]"

AI prompts you for details you might skip:
- "What happens if the receipt is missing?"
- "Who approves refunds over £100?"
- "How long does each step typically take?"

### The Observation Approach

After doing a process:

> "Here's everything I did to complete this task: [detailed narration]. Turn this into a documented procedure someone else could follow."

You describe what you did; AI structures it.

### The Gap-Finding Approach

> "Here's our current documented process for [X]. Here's how I actually do it. What's different? What's missing from the documentation?"

Identifies where docs have drifted from reality.

```
EXERCISE:
Choose a process you do regularly that isn't well documented.

1. Describe it to AI in rough terms
2. Let AI ask clarifying questions
3. Have AI compile it into a documented procedure
4. Review: Is anything missing or wrong?
```

## Documentation Formats

### Step-by-Step Procedures

For tasks with a clear sequence:

```markdown
## Procedure: Processing Customer Refund

**Purpose:** Process refund requests within 48 hours

**Prerequisites:**
- Access to billing system
- Refund approval authority (or access to approver)

**Steps:**

1. **Verify the request**
   - Check order number in system
   - Confirm purchase within refund window (30 days)
   - If outside window → Escalate to Manager

2. **Check refund eligibility**
   - Product condition: unused, original packaging
   - Reason code: Select from dropdown
   - If unclear → Contact customer for clarification

3. **Process the refund**
   - Enter refund amount
   - Select refund method (original payment method)
   - Add internal note with reason
   - Click "Submit"

4. **Notify the customer**
   - Send confirmation email (use template: Refund Confirmation)
   - Note expected processing time (3-5 business days)

**Exceptions:**
- Refunds over £100 require manager approval
- Damaged goods require photos before processing

**Related Documents:**
- Refund Policy
- Escalation Procedures
```

### Decision Trees

For processes with many branches:

> "Convert this process into a decision tree format. At each decision point, show the question and the paths for Yes/No."

```
Start: Customer requests refund
    ↓
Within 30-day window?
    → Yes → Product unopened?
              → Yes → Process standard refund
              → No → Check damage policy
    → No → Eligible for exception?
              → Yes → Manager approval required
              → No → Decline with explanation
```

### Checklists

For processes where order is flexible but completeness matters:

```markdown
## Checklist: New Employee Onboarding

**Before First Day:**
- [ ] Laptop ordered and configured
- [ ] Email account created
- [ ] Access cards prepared
- [ ] Desk/workspace assigned
- [ ] Manager notified of start date

**First Day:**
- [ ] Welcome meeting with HR
- [ ] System access verified
- [ ] Building tour completed
- [ ] Team introductions done
- [ ] First week schedule shared

**First Week:**
- [ ] Required training modules assigned
- [ ] Regular check-in scheduled
- [ ] Goals discussion with manager
```

```
QUIZ:
You're documenting a process that has 12 steps when everything goes well, but 5 different exception paths. What format works best?

* A simple numbered list
*! A decision tree or flowchart showing the main path and branches
* A checklist
* Just describe it in prose
FEEDBACK:Complex processes with many exceptions are clearer as decision trees or flowcharts. Linear lists get confusing when there are many "if X, then do Y instead" branches.
```

## Improving Processes

### Finding Inefficiencies

> "Here's our current process for [X]. Identify:
> - Redundant steps
> - Unnecessary approvals
> - Points where delays commonly occur
> - Steps that could be automated"

AI can spot patterns you've become blind to.

### Simplification

> "This process has 15 steps. The goal is [Y]. What's the minimum number of steps to achieve that goal? What would we lose by cutting each step?"

Forces evaluation of whether each step adds value.

### Comparison

> "Here's how Team A does this process. Here's how Team B does it. Compare: What's different? Which approach is better for what situations?"

Useful after mergers or when standardising.

## Writing for Different Audiences

### For Practitioners

The person doing the task:
- Focus on how, step by step
- Include tips and shortcuts
- Note common mistakes
- Keep it scannable

### For New Starters

Someone learning the process:
- Add more context (why each step matters)
- Include background information
- Define jargon
- Link to training resources

### For Managers

Someone overseeing but not doing:
- Focus on outcomes and metrics
- Include exception handling
- Note approval points
- Summarise time and resources

> "Rewrite this procedure for three audiences:
> 1. Someone doing it daily (quick reference)
> 2. Someone learning it for the first time (training doc)
> 3. A manager who needs to understand it (overview)"

## Keeping Documentation Current

### The Update Trigger

> "Add a header to this document: 'Last updated: [date]. Review trigger: Review if any of these change: [list of dependencies]'"

Makes it clear when docs need updating.

### Version Notes

> "Add a changelog section to track what changed and when:
> - v1.0 (Jan 2024): Initial version
> - v1.1 (Mar 2024): Added exception for international orders"

Prevents confusion about which version is current.

### The Annual Review Prompt

> "Here's our process documentation from last year. Here's how things actually work now. What needs updating?"

Schedule regular comparisons between docs and reality.

## Compliance and Audit Documentation

For regulated processes:

### Required Elements

> "This process needs to be audit-ready. Add:
> - Who is responsible for each step
> - What evidence/records are created
> - What approvals are required
> - How long records must be retained"

### The Audit Trail View

> "Reformat this process to show the audit trail: What record exists after each step? Where is it stored? Who can access it?"

## Process Documentation Templates

For consistent documentation across your organisation:

```markdown
# Process Documentation Template

## Process Name
[Clear, searchable name]

## Purpose
[What this process achieves and why it matters]

## Scope
[What's included and excluded]

## Roles
[Who does what]

## Prerequisites
[What's needed before starting]

## Procedure
[Step-by-step instructions]

## Exceptions
[How to handle unusual cases]

## Related Documents
[Links to related procedures, policies, forms]

## Revision History
[When updated and what changed]

## Owner
[Who maintains this document]
```

## Key Takeaways

- AI helps capture tribal knowledge through interview and observation approaches
- Match format to process: procedures for sequences, decision trees for branches, checklists for completeness
- AI can identify inefficiencies, redundant steps, and improvement opportunities
- Write for your audience: practitioners want quick reference, learners need context, managers need overview
- Build in update triggers and version tracking
- For compliance: document responsibilities, evidence, approvals, retention
- Use templates for consistency across documentation

---

Next: **O4. Communication & Meetings** →
