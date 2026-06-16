# E4. Monitoring, Compliance & Continuous Evaluation

## From One-Off Verification to Continuous Assurance

The previous modules covered deployment and governance. But AI doesn't stay stable. Models drift, prompts evolve, usage patterns change unexpectedly. One-off verification at deployment time isn't enough.

Enterprise AI governance requires **continuous evaluation**: monitoring output quality, tracking data usage, detecting drift, and keeping incident response ready.

This module addresses two critical gaps:
1. **Ongoing evaluation and monitoring** — beyond initial verification
2. **Data classification and risk models** — practical redaction and handling patterns

## Part One: Continuous Evaluation and Monitoring

### Why Continuous Monitoring Matters

| Risk | One-Off Verification | Continuous Monitoring |
|------|----------------------|----------------------|
| Model drift | Missed | Detected |
| Prompt degradation | Missed | Tracked |
| Unexpected usage patterns | Missed | Alerted |
| Data handling slippage | Missed | Caught |
| Gradual accuracy decline | Missed | Trended |

Once deployed, AI systems experience continuous pressure to degrade:
- Models are updated or replaced
- Prompts are tweaked by teams
- Usage shifts to edge cases
- Data distributions change
- Competitive models emerge with different behaviour

```
EXERCISE:
List three ways an AI deployment might degrade after 6 months of production use, without any code changes.
```

### Evaluation Cadences

Define how often you evaluate and what you check:

| Cadence | What | Owner | Threshold |
|---------|------|-------|-----------|
| **Per-session** | Automated structure validation | System | 100% valid |
| **Daily** | Sampled output quality checks | Alert system | >5 failures per 1000 |
| **Weekly** | Error rate trending, edge case discovery | Team review | Baseline ±10% |
| **Monthly** | Data usage compliance, usage patterns | Audit team | Policy adherence |
| **Quarterly** | Prompt regression testing, model evaluation | Governance team | Go/no-go decision |
| **Annually** | Full architecture review, update policies | Leadership | Renewal or sunset |

### Benchmarking and Regression Testing

Create a benchmark dataset of reference cases:

```
BENCHMARK DATASET FOR CUSTOMER SUPPORT AI

Case 1 (Basic): Customer asks for order status
├── Input: "Where's my order? Order #12345"
├── Must contain: Order number, status
├── Must not contain: Customer credit card, phone
└── Similarity to approved response: >0.7

Case 2 (Sensitive): Customer reports billing error
├── Input: "I was charged twice for order #67890"
├── Must contain: Acknowledgment, next steps
├── Must not contain: Other customer's data
└── Tone: Empathetic and professional

Case 3 (Edge case): Malformed/unclear input
├── Input: "hjkl;qwer zxcv"
├── Must: Gracefully decline, offer help
├── Must not contain: Frustrated response
└── Length: <200 words
```

Test against this benchmark:
- Weekly: sample 10 random cases from benchmark, check properties
- After any prompt change: full benchmark suite must pass
- Monthly: expand benchmark with new edge cases discovered in production

### Drift Detection Patterns

Monitor for shifts in output characteristics:

| Metric | How to Track | Alert Threshold |
|--------|-------------|-----------------|
| **Refusal rate** | % of requests AI declines | >2% increase |
| **Hallucination rate** | % outputs with unsupported claims | >5% |
| **Latency** | Time per response (p95) | >20% increase |
| **Token usage** | Avg tokens per response | >15% increase |
| **User satisfaction** | Sample ratings on outputs | >0.1 point drop |
| **Data exposure** | Sensitive data in outputs | Any incident |

```python
# Simple drift detection pattern
class EvaluationTracker:
    def __init__(self, baseline_metrics):
        self.baseline = baseline_metrics
        self.history = []

    def check_drift(self, current_metrics):
        for metric, value in current_metrics.items():
            baseline = self.baseline[metric]
            pct_change = abs(value - baseline) / baseline

            if pct_change > 0.2:  # 20% threshold
                alert(f"{metric} drifted {pct_change:.1%}")

            self.history.append({
                'metric': metric,
                'value': value,
                'baseline': baseline,
                'timestamp': now()
            })
```

### Incident Detection and Response

Link monitoring to incident response (from E3):

**Automated detection triggers:**
- Data exposure in output → Immediate containment alert
- Refusal rate spike → Manual review batch
- Unrecognised data classification in output → Escalation
- Model version mismatch → Review requested

**Investigation checklist:**
1. When was it first detected?
2. What was the AI asked to do?
3. What did it output/do?
4. What governance boundary was crossed?
5. Did our monitoring systems catch it, or did a user report it?

**Prevention logic:**
- If monitoring failed to catch it: improve monitoring
- If it was caught too late: lower thresholds
- If it shouldn't have happened: audit the access/action policy

### Audit Logging Requirements

To enable continuous monitoring and incident response, you need comprehensive audit trails.

**Minimum logging for any AI deployment:**

```
AUDIT LOG ENTRY

timestamp: 2025-02-06T10:23:14Z
deployment_id: customer-support-ai-v3
session_id: sess_92847629...
user_id: support_agent_47

REQUEST:
  scope: [customer_order_summary]
  data_classification: [internal, pii_masked]
  content_hash: a7f3e2...

RESPONSE:
  tokens_used: 342
  response_time_ms: 1847
  content_hash: 2b9f4c...
  includes_classifications: [internal]
  flagged_issues: none

REVIEW:
  human_reviewed: true
  reviewed_by: sarah.chen
  approved: true
```

Log what data was accessed, what the AI output, whether it was approved, and any issues flagged. This is essential for:
- Reconstructing incidents
- Trending quality metrics
- Detecting abuse
- Proving compliance

```
QUIZ:
An AI deployment's error rate has increased from 2% to 8% over the past month. What should you do first?

* Immediately shut down the deployment
* Check if a model update happened or prompts changed
*! Check logs for what changed, review sampled outputs, compare to benchmark cases
* Wait to see if it stabilises
* Increase human review to 100%

FEEDBACK: Investigate the cause before deciding on response. The increase might be due to prompt changes, different usage patterns, or legitimate model improvements. Understanding causation guides the right fix.
```

### Testing Prompts for Regression

When prompts change, regression test the new version:

**Before deploying a prompt change:**
1. Run full benchmark suite against new prompt
2. Compare output properties to baseline (length, tone, refusal rate)
3. Sample human review of 10-20 outputs
4. A/B test in production (if low-risk task) or staged deployment

**Document the change:**
```
PROMPT VERSION: 3.2

CHANGE: Expanded instruction to handle billing disputes
RATIONALE: Support team reported 15% of escalations were missed billing issues

REGRESSION TESTING:
├── Benchmark cases: 98/100 pass (2% improvement in accuracy)
├── Edge cases: No new failures, 1 new success case
├── Human review: 18/20 improved or unchanged
├── Rollout: Staged 10% → 50% → 100% over 1 week

MONITORING: Daily refusal rate, weekly full evaluation
```

---

## Part Two: Data Classification and Risk Handling

### The Data Classification Framework

Organisations typically use four classifications — Public, Internal, Confidential, Restricted. The canonical table mapping each class to allowed channels is in **E2. Approved Channels** (see the Data Classification and Routing section); we won't repeat it here.

What this module adds is the operational layer: **what can go into the prompt, who approves it, what gets logged, and how long anything is retained.** Those rules are defined per tier in the Risk Tiers and Handling Rules table below. First, though, the practical question teams actually face: how to redact data so it becomes safe to use.

### Building a Redaction Decision Tree

When someone says "Can we send this to AI?", use a decision tree:

```
DATA CLASSIFICATION DECISION TREE

START: "I want to send [DATA] to AI"
│
├─ Is it public information?
│  └─ YES → Approve. Log the use.
│  └─ NO → Continue
│
├─ Is it already approved in policy for AI use?
│  └─ YES → Approve. Log and audit.
│  └─ NO → Continue
│
├─ Can it be redacted to remove sensitive elements?
│  └─ YES → Redact. Log what was removed. Approve.
│  └─ NO → Continue
│
├─ Does the AI need the sensitive parts, or is abstract enough?
│  └─ YES (abstract OK) → Abstract (e.g., "Customer A", "$X amount")
│  │                      Approve. Log.
│  └─ NO (needs specifics) → Continue
│
├─ Is this a one-time manual task with full audit?
│  └─ YES → Approval required from [role]. Full logging.
│  └─ NO → Continue
│
└─ REJECT: This data should not go to AI.
```

### Practical Redaction Patterns

**Pattern 1: PII Masking**
```
BEFORE:
"Customer Sarah Chen (ID: C-47291) from seattle@example.com reports billing issue.
Card ending in 2847 was charged twice for order #PO-2025-891."

AFTER (for support categorisation):
"Customer [NAME] (ID: [CUST_ID]) reports billing issue.
Payment method [MASKED] was charged twice for order [ORDER_ID]."

REDACTED: Name, email, card number (only last 4 digits used elsewhere)
KEPT: Customer ID (needed for lookup), issue category (support's own assessment)
```

**Pattern 2: Anonymisation for Analysis**
```
BEFORE:
"Q4 revenue by customer:
- Acme Corp: $2.4M
- TechStart Inc: $890K
- Global Industries: $12.3M"

AFTER:
"Q4 revenue by customer:
- Customer A: $2.4M
- Customer B: $890K
- Customer C: $12.3M"

REDACTED: Company names
KEPT: Amount (needed for trend analysis), rank order
```

**Pattern 3: Aggregation and Generalisation**
```
BEFORE:
"Sales team members: John (closed $4.2M), Sarah (closed $3.1M),
Marcus (closed $1.8M). Top prospect: TechCorp, $8M deal closing March."

AFTER:
"Sales team performance: Top performer closed $4.2M, others $3.1M and $1.8M.
Largest pipeline: ~$8M, closing Q1."

REDACTED: Names, company name, exact close date
KEPT: Performance levels (needed to discuss team), deal size scale
```

**Pattern 4: Abstraction for Examples**
```
BEFORE:
"Employee complained about manager Tom Davis refusing remote work requests.
Last occurrence: Jan 15, she asked about Mondays working from home."

AFTER:
"Employee requested accommodation (work flexibility). Manager declined request.
Last request was dated [MONTH], regarding specific schedule request."

REDACTED: Names, specifics of request, date precision
KEPT: Issue type, recency indicator
```

### Risk Tiers and Handling Rules

Define how each tier of data can be handled. These tiers deliberately mirror the Tiered Access pattern in **E3. Governance Patterns**: E3's tiers govern what an AI *deployment* may access and do; the table below governs how the *data itself* must be handled — approval, logging, and retention.

| Tier | Data Type | AI Access | Approval Required | Audit Logging | Retention |
|------|-----------|-----------|-------------------|---------------|-----------|
| **Tier 1** | Public, internal non-sensitive | Unrestricted | None | Routine | Standard |
| **Tier 2** | Internal, low-sensitivity PII masked | Approved tools only | Per-deployment | Enhanced | Standard |
| **Tier 3** | Confidential, redacted, anonymised | Specific approval per use | Escalation path | Detailed | Limited (30 days) |
| **Tier 4** | Restricted, highly sensitive | Air-gapped only | Executive | Complete | Immediate deletion |

### Data Handling Governance Policy

When drafting your AI use policy (E3), add a data handling section:

```
DATA HANDLING RULES FOR AI

TIER 1 (PUBLIC):
- No restrictions
- Example: Press releases, public documentation

TIER 2 (INTERNAL, MASKED):
- Approved tools only
- PII must be masked/anonymised
- Example: Anonymised support tickets, redacted internal memos

TIER 3 (CONFIDENTIAL, REDACTED):
- Requires explicit approval
- All sensitive details removed or abstracted
- Audit logging mandatory
- Example: Redacted contracts, de-identified financial reports

TIER 4 (RESTRICTED):
- Prohibited in cloud AI
- Air-gapped systems only (if at all)
- Executive approval, case-by-case
- Complete audit trail and immediate deletion
- Example: Personal health data, trade secrets, unreleased financial results

REDACTION RESPONSIBILITY:
- User/team providing data is responsible for identifying what needs redaction
- Data owner must approve before AI use
- If in doubt, treat as Confidential and escalate
- Document what was redacted and why

INCIDENT RESPONSE FOR DATA BREACHES:
- AI output contains unredacted sensitive data → Immediate containment (P1)
- Assess exposure: Who saw it? For how long?
- Review access controls and audit trail
- Notify affected parties if required by regulation
- Update redaction checklist to prevent recurrence
```

```
EXERCISE:
You're asked to let an AI draft responses to customer complaints. Sample complaints include:

1. "Customer Maria Rodriguez says the shipment of her order (tracking #TRK-8834) arrived damaged."
2. "VP of Sales David Chen needs approval for $400K sponsorship deal with TechConf."
3. "Employee Jake reports he wasn't selected for the marketing manager role he interviewed for."

For each, decide:
- What classification is this data?
- What can/can't the AI see?
- What redaction is needed?
- Would you approve this use?
```

### Monitoring Data Compliance

Just as you monitor output quality, monitor data handling compliance:

**Monthly data compliance audit:**
- Sample 50 AI sessions
- Check: Was data redacted appropriately?
- Check: Was access logged?
- Check: Was approval obtained?
- Flag: Any unredacted sensitive data in output

**Questions to ask:**
- Did the AI receive data it shouldn't have?
- Did the AI output data that should have been redacted?
- Are employees using approved channels or shadow tools?
- Are logs being retained according to policy?

---

## Tying It Together: The Continuous Assurance Cycle

```
CONTINUOUS ASSURANCE CYCLE

┌─────────────────────────────────────────────────┐
│                   DEPLOY                        │
│  ✓ Trust architecture set                       │
│  ✓ Approved channel selected                    │
│  ✓ Governance patterns applied                  │
│  ✓ Data redaction rules configured              │
│  ✓ Benchmarks and baselines established         │
└────────────────────┬────────────────────────────┘
                     │
         ┌───────────┴───────────┐
         ▼                       ▼
    MONITOR DAILY         MONITOR MONTHLY
    ┌─────────────┐       ┌──────────────────┐
    │ Automate:   │       │ Manual audit:    │
    │ • Errors    │       │ • Data handling  │
    │ • Structure │       │ • Access logs    │
    │ • Basics    │       │ • Incident log   │
    └─────────────┘       │ • Usage patterns │
         │                └──────────────────┘
         │                       │
         └───────────┬───────────┘
                     ▼
         ┌───────────────────────┐
         │  DRIFT DETECTED?      │
         └───────┬───────────────┘
                 │
         ┌───────┴────────┐
         │ YES            │ NO
         ▼                ▼
    ┌────────────┐    ┌──────────┐
    │ INVESTIGATE│    │CONTINUE  │
    │ • Review   │    │MONITORING│
    │ • Test     │    │Every 90  │
    │ • Decide   │    │days:     │
    └─┬──────────┘    │Full      │
      │               │evaluation│
      └───────┬───────┴──────────┘
              ▼
    ┌─────────────────────────┐
    │  INCIDENT OR            │
    │  IMPROVEMENT NEEDED?    │
    └────────┬────────────────┘
             │
    ┌────────┴─────────┐
    │ YES              │ NO
    ▼                  ▼
INCIDENT RESPONSE  CONTINUE
(from E3)          OPERATION
└────────────────────┘
```

```
QUIZ:
You're monitoring an AI customer support agent. One month in, you notice the refusal rate has increased from 1.2% to 4.8%. Your benchmark tests all pass. What's the most likely explanation?

* The model degraded overnight
* Usage patterns shifted to harder questions
*! Usage patterns shifted; benchmark doesn't cover new use cases
* You should immediately shut it down
* The logging system is broken

FEEDBACK: Passing benchmarks with rising refusal rate suggests the AI is facing questions outside the benchmark's scope. Investigate production logs to see what's being asked, and add new cases to the benchmark to cover the shift.
```

---

## Practical Monitoring Stack

Most organisations need:

| Component | Purpose | Example |
|-----------|---------|---------|
| **Logging** | Record all AI activity | Structured logs to S3/CloudWatch |
| **Metrics** | Track key indicators over time | Refusal rate, error rate, latency |
| **Dashboards** | Visualise trends | Weekly trend charts for stakeholders |
| **Alerts** | Notify on anomalies | Slack alert if error rate >5% |
| **Retention** | Keep logs for compliance | 90 days hot, 7 years cold storage |

You don't need a complex system. Start simple: structured JSON logs, basic dashboards, alert rules on key thresholds.

---

## Key Takeaways

**Continuous Evaluation:**
- One-off verification isn't sufficient — monitor continuously
- Establish evaluation cadences: per-session, daily, weekly, monthly, quarterly, annual
- Create benchmark datasets and regression test against them
- Track drift in output quality, latency, refusal rates, and data handling
- Link monitoring to incident response from E3

**Data Classification and Risk:**
- Classify data by sensitivity and define what can go to AI
- Build redaction decision trees so teams know when to escalate
- Implement practical redaction patterns: masking, anonymisation, abstraction
- Define risk tiers with clear approval and logging requirements
- Monitor data compliance monthly

**Continuous Assurance:**
- Deploy with full governance and monitoring configured
- Automate daily monitoring of errors and structure
- Monthly manual audits of data handling and access
- Investigate drift, update benchmarks, improve controls
- Close the loop: incidents inform policy, policy prevents incidents

---

## Case Study: A&O Shearman × Harvey AI

Global law firm A&O Shearman (Allen & Overy Shearman Sterling) has thousands of lawyers across dozens of jurisdictions. From late 2022, it became one of the earliest large law firms to deploy Harvey AI at scale — and the deployment has since become one of the most widely cited examples of legal AI adoption.

**The Results:**

The firm has publicly reported meaningful weekly time savings per lawyer and substantially faster contract review. More tellingly, it has scaled beyond initial use cases to deploy agentic AI for work such as antitrust filing, cybersecurity review, fund formation, and loan review.

**Why It Worked:**

The governance framework in this module wasn't theoretical for A&O Shearman. The firm applied three principles from the outset:

1. **Clear trust boundaries, not open-ended access.** The AI didn't get blanket permission to handle all firm data. Instead, scoped access controlled what the system could see and do.

2. **Governance first, wide deployment second.** Formal policies were established before rolling out to many lawyers, not bolted on after problems emerged.

3. **Monitoring built in from day one.** The firm established metrics, audit trails, and continuous evaluation from deployment, not added later.

This disciplined approach let them scale from pilot to firm-wide deployment successfully.

**Key Takeaway:** Enterprise AI governance succeeds when you start with trust boundaries, establish formal policies before scaling, and make monitoring a first-class concern — exactly what this module covers.

Learn more: https://www.harvey.ai/

---

## Case Study: Big 4 Accounting Firms and Agentic AI

The Big 4 accounting firms have all made major, publicly announced AI investments: retraining junior staff to work as "managers of agents", pushing audit workflows towards heavy AI automation, and rolling out AI tax and advisory tooling across workforces of tens of thousands.

These aren't theory. These firms are building the exact monitoring and compliance frameworks you've learned in this module. They're establishing governance policies, setting evaluation cadences, handling sensitive data responsibly, and integrating continuous monitoring into their operational rhythm.

**Key Takeaway:** The enterprise monitoring and compliance frameworks in this module are what leading firms are deploying now. This isn't future-state practice — it's the current state of advanced AI governance in professional services.

Learn more: https://www.icaew.com/technical/technology/artificial-intelligence

---

Congratulations! You've completed the Enterprise Track.

You now have a comprehensive framework for governing AI in enterprise environments:
- **E1** — Define trust boundaries (access, actions, retention, accountability)
- **E2** — Choose approved channels and manage shadow AI risk
- **E3** — Apply governance patterns and prepare incident response
- **E4** — Monitor continuously and handle data responsibly

Consider also:
- **Developer Track** — If you're building AI integrations
- **Academic Track** — If you do research or writing-heavy work
- **Operations Track** — If you support AI deployments at scale
