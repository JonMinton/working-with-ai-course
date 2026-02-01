# Module 4: Verification & Quality

## The Verification Imperative

AI-generated outputs can be:
- **Correct and useful** — what you wanted
- **Plausible but wrong** — looks right, isn't
- **Obviously wrong** — easy to catch
- **Subtly wrong** — the dangerous case

The second and fourth categories are where problems hide. AI is very good at producing confident, well-structured outputs that contain errors.

**Your job is not to trust. Your job is to verify.**

## The Verification Mindset

Traditional development: Write code → hope it works → test
AI-assisted development: Specify → generate → **verify before trusting**

This isn't about distrust. It's about recognising that:
- AI makes mistakes (hallucinations, logic errors, outdated patterns)
- AI doesn't know what it doesn't know
- Verification is where human judgment is irreplaceable

## Verification Strategies by Output Type

### Code

**What can go wrong:**
- Logic errors (wrong algorithm, off-by-one, edge cases)
- Security vulnerabilities (injection, auth bypass)
- Performance issues (O(n²) when O(n) possible)
- Dependency issues (wrong versions, deprecated APIs)
- Style/convention mismatches

**Verification approaches:**

| Method | Catches | Effort |
|--------|---------|--------|
| **Read it** | Logic errors, obvious issues | Low |
| **Run tests** | Behavioural correctness | Medium |
| **Test edge cases** | Boundary conditions | Medium |
| **Code review patterns** | Security, performance | Medium |
| **Static analysis** | Style, some bugs | Low |
| **Ask another AI** | Fresh perspective | Low |

```
EXERCISE:
AI generates this function:

    def get_user_age(user_id):
        user = db.query(f"SELECT * FROM users WHERE id = {user_id}")
        if user:
            return user.age
        return 0

List at least 3 problems with this code that verification should catch.
```

### Factual Claims

**What can go wrong:**
- Hallucinated citations (made-up sources)
- Outdated information
- Plausible-sounding but false claims
- Misattributed quotes
- Wrong statistics

**Verification approaches:**

| Method | When to Use |
|--------|-------------|
| **Source check** | Any specific claim with a citation |
| **Cross-reference** | Important facts, statistics |
| **Recency check** | Anything that might have changed |
| **Plausibility check** | Numbers, dates, relationships |
| **Domain expert review** | High-stakes content |

**Red flags that demand verification:**
- Specific numbers (especially statistics)
- Direct quotes from named individuals
- Claims about recent events
- Anything that would be surprising if true

### Structured Data

**What can go wrong:**
- Schema mismatches
- Invalid relationships
- Missing required fields
- Type errors
- Inconsistent formatting

**Verification approaches:**
- Schema validation (automated)
- Spot checks (manual)
- Referential integrity checks
- Sample queries to test assumptions

### Prose/Writing

**What can go wrong:**
- Factual errors embedded in narrative
- Tone mismatches
- Unintended implications
- Logical inconsistencies
- Inappropriate content

**Verification approaches:**
- Read it (no shortcut here)
- Check any embedded facts
- Consider audience reaction
- Review for consistency with source material

## The Visual Reasoning Gap

AI has particular limitations with visual outputs:

**AI struggles with:**
- Spatial relationships ("Is A above B?")
- Visual debugging ("Why does this CSS render wrong?")
- Proportions and aesthetics ("Does this look balanced?")
- Complex visualisations (dense charts, overlapping elements)

**Implications for verification:**
- AI cannot reliably verify its own visual outputs
- You must look at rendered results
- Screenshots are your friend
- "It should look right" is a human judgment call

```
┌─────────────────────────────────────────────┐
│           THE VISUAL VERIFICATION LOOP      │
├─────────────────────────────────────────────┤
│                                             │
│  Specify visual intent (text description)   │
│              ↓                              │
│  AI generates code (CSS, HTML, SVG, etc.)   │
│              ↓                              │
│  Code renders to visual output              │
│              ↓                              │
│  YOU verify (AI cannot do this step)        │
│              ↓                              │
│  Iterate with textual feedback              │
│                                             │
└─────────────────────────────────────────────┘
```

```
EXERCISE:
You ask AI to create a landing page with "a hero section with the tagline on the left and an image on the right, taking roughly equal space."

AI generates CSS. You render it. The image is tiny and pushed to the corner.

Write feedback that will help AI fix this — remembering that AI can't see what you're seeing.
```

## Test-Driven Specification

The most robust verification: **write tests first**.

This serves two purposes:
1. Tests become your specification (verifiable acceptance criteria)
2. Tests catch regressions if you iterate

**Pattern:**
```
1. Write tests that describe desired behaviour
2. Ask AI to implement to pass the tests
3. Run tests → if failing, iterate
4. Tests document the specification permanently
```

This transforms "I'll know it when I see it" into automated verification.

## The Two-AI Pattern

Use one AI to check another:

**How it works:**
1. AI-A generates output
2. AI-B reviews output (ideally different model family)
3. Human adjudicates disagreements

**Why this helps:**
- Different models have different blind spots
- Fresh context catches assumptions
- Mimics peer review

**What to ask the reviewer AI:**
- "What errors or issues do you see in this code?"
- "What claims in this text would you want to verify?"
- "What edge cases might this not handle?"
- "What would a critical reviewer say about this?"

```
QUIZ:
You've generated a research summary using Claude. Which approach provides the best verification?

* Ask Claude to verify its own work
* Ask GPT-4 to critique it
*! Ask GPT-4 to critique it, then verify any specific claims yourself
* Assume it's correct if it looks well-written

FEEDBACK: Cross-model review catches more issues than self-review, but human verification of specific claims is still essential for anything important.
```

## Verification Checklists

**For code:**
- [ ] Does it handle edge cases? (null, empty, very large inputs)
- [ ] Are there security implications? (injection, auth, data exposure)
- [ ] Is the complexity appropriate? (not O(n²) when O(n) works)
- [ ] Does it match project conventions?
- [ ] Are dependencies correct and up-to-date?
- [ ] Do tests pass?

**For factual content:**
- [ ] Are all citations real? (check at least a sample)

**For data handling (before you paste or upload):**
- [ ] What is the data classification? (Public / Internal / Confidential / Restricted)
- [ ] Is this channel approved for that classification?
- [ ] Have identifiers been removed or masked where possible?
- [ ] Is the minimum necessary data included?
- [ ] Do we have an audit trail for this use?
- [ ] Would we be comfortable if this appeared in an incident review?
- [ ] Are statistics plausible?
- [ ] Is information current?
- [ ] Are quotes accurate?
- [ ] Are there claims that would be surprising if true?

**For visual outputs:**
- [ ] Have you actually looked at the rendered result?
- [ ] Does spacing/proportion look right?
- [ ] Does it work at different screen sizes?
- [ ] Is text readable?
- [ ] Do colours have sufficient contrast?

## Ongoing Evaluation and Drift

Verification is not only a **one‑off check**. Over time, models, tools, and prompts change.

Use lightweight evaluation to catch drift:
- **Regression prompts:** keep a small set of “known‑good” tasks and rerun them after changes
- **Output snapshots:** store example outputs for comparison
- **Error tracking:** record recurring mistakes and update prompts or guardrails
- **Scheduled review:** re‑evaluate critical workflows monthly or quarterly

**Rule of thumb:** If the workflow matters, it deserves a baseline and a periodic re‑test.

## When to Verify More Carefully

**High verification needed:**
- Production code
- Public-facing content
- Legal or compliance documents
- Financial calculations
- Health or safety information
- Anything with real-world consequences

**Lower verification (but still check):**
- Drafts and exploration
- Internal tools
- Learning exercises
- Prototypes

## Key Takeaways

- Verification is not optional — AI makes confident mistakes
- Different output types need different verification strategies
- AI cannot reliably verify visual outputs — you must look
- Test-driven specification automates verification
- Cross-model review catches more issues than self-review
- Match verification effort to stakes
- "It looks right" is not verification

---

Congratulations! You've completed the core modules.

Now choose your specialised track:
- **Enterprise Track** → Trust architecture, approved channels, governance
- **Developer Track** → Affordances, architecture, MCP tools
- **Academic Track** → Literature workflows, modular writing, AI peer review
