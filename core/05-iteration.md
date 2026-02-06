# Module 5: Iteration & Refinement

## The Feedback Loop

You've learned to specify clearly (Module 1) and verify rigorously (Module 4). But what happens in between — when the output isn't quite right?

This is the **iteration loop**:

```
┌─────────────────────────────────────────────────────────────┐
│                    THE ITERATION LOOP                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Specify → Generate → Evaluate → [Decision Point]          │
│                                       │                     │
│                          ┌────────────┼────────────┐        │
│                          ▼            ▼            ▼        │
│                       Accept      Refine       Restart      │
│                                      │                      │
│                                      └──→ Back to Generate  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

Most AI interactions aren't one-shot. The skill is knowing how to move through this loop efficiently.

## The Three Responses to Imperfect Output

When AI output doesn't meet your needs, you have three options:

### 1. Accept (Good Enough)

Sometimes "not quite what I wanted" is actually fine:
- The output achieves the goal, just differently than imagined
- Fixing it manually is faster than another iteration
- You've learned something that changes what you want

**The trap:** Accepting too early because iteration feels like failure. It's not — it's the normal process.

### 2. Refine (Iterate)

Give feedback and try again:
- Point out specific issues
- Clarify what was misunderstood
- Add constraints that were implicit

**The trap:** Endless refinement when the approach is fundamentally wrong.

### 3. Restart (Fresh Context)

Start over with a different approach:
- The conversation has accumulated too much confusion
- You've realised you were asking for the wrong thing
- The AI is stuck in a pattern that feedback isn't fixing

**The trap:** Restarting too early, losing valuable context and progress.

```
QUIZ:
AI has generated three versions of a function. Each is closer to what you want, but version 3 still has a subtle bug you've explained twice. What should you do?

* Keep refining — you're making progress
* Accept version 3 and fix the bug manually
*! Consider restarting with a clearer specification that addresses the bug upfront
* Give up on AI for this task

FEEDBACK: After multiple iterations on the same issue, the conversation context may be working against you. A fresh start with better specification often works faster than continued refinement.
```

## Effective Feedback

The quality of your feedback determines iteration efficiency.

### Bad Feedback Patterns

**Too vague:**
> "This isn't right"
> "Make it better"
> "That's not what I meant"

**Too emotional:**
> "This is completely wrong!"
> "Why can't you understand?"

**Assuming AI remembers:**
> "Like I said before..."
> "Remember the thing about..."

### Good Feedback Patterns

**Specific and actionable:**
> "The function returns a string, but I need it to return an object with 'value' and 'unit' properties"

**Shows the gap:**
> "Current: button is blue. Expected: button is green (#16a34a)"

**Includes context:**
> "This will be called with user input, so we need to handle the case where the string is empty"

**Acknowledges what's right:**
> "The structure is correct. The issue is in the date formatting — it should be DD/MM/YYYY, not MM/DD/YYYY"

### The Feedback Template

A reliable structure for iteration:

> **What's working:** [acknowledge correct parts]
>
> **What's not working:** [specific issue]
>
> **What I expected:** [concrete description]
>
> **Additional context:** [anything that might help]

```
EXERCISE:
AI generated a landing page, but:
- The hero text is too small
- The call-to-action button is below the fold
- The colour scheme is right

Write feedback using the template above that will help AI fix this efficiently.
```

## When to Refine vs. Restart

### Signs You Should Keep Refining

- Each iteration is getting closer
- The AI understands the goal, just missing details
- You're adding new information, not repeating yourself
- The conversation context is still useful

### Signs You Should Restart

- You're repeating the same feedback
- The AI keeps reverting to earlier mistakes
- The conversation has become confused or contradictory
- You've realised your original specification was wrong
- The context window is getting full (long conversation)

### The "Three Strikes" Heuristic

> If you've given the same feedback three times and it's not sticking, restart.

This isn't a hard rule, but it's a useful signal. Continued refinement after three failed attempts rarely succeeds — the conversation context is probably the problem.

## Context Degradation

Long conversations accumulate problems:

**Context window limits:** Old messages may be truncated or summarised, losing important details.

**Contradictory instructions:** Your feedback from turn 3 might conflict with your feedback from turn 15.

**Anchoring:** Early mistakes can anchor the AI's interpretation, making it hard to shift approach.

**Your own fatigue:** You start accepting worse outputs because you're tired of iterating.

### Managing Context Over Sessions

**For complex tasks:**
1. Break into subtasks that can be done in separate conversations
2. Summarise progress at natural breakpoints
3. Start fresh sessions with explicit context rather than continuing indefinitely

**For ongoing projects:**
1. Use instruction files (CLAUDE.md, etc.) for persistent context
2. Keep a "project state" document you can paste into new sessions
3. Don't rely on AI "remembering" — restate what matters

```
QUIZ:
You've been working with AI on a complex refactoring task for 45 minutes. The conversation is 30+ turns. AI's responses are getting less accurate. What's the most likely cause?

* The AI is getting tired
* The AI is being stubborn
*! Important context from early in the conversation may be getting truncated or lost
* The task is too hard for AI

FEEDBACK: AI doesn't get tired or stubborn. Long conversations suffer from context degradation — early messages may be summarised or truncated, losing important details.
```

## Iteration Anti-Patterns

### The Politeness Trap

Being overly polite wastes tokens and can obscure feedback:

**Inefficient:**
> "Thank you so much for that attempt! It's really good, but I was wondering if maybe you could possibly consider changing the colour? Only if it's not too much trouble!"

**Efficient:**
> "Good structure. Change the button colour from blue to green (#16a34a)."

You can be direct without being rude. AI doesn't have feelings to hurt.

### The Kitchen Sink

Adding too much feedback at once:

**Overwhelming:**
> "Fix the colour, and also the spacing is wrong, and can you add a hover state, and the font should be different, and actually let's reconsider the whole layout..."

**Focused:**
> "Let's fix the colour first: change the button to green (#16a34a). We'll address other issues after."

Iterate on one thing at a time for complex changes.

### The Assumption Spiral

Assuming AI understood something it didn't, then building on that assumption:

**Turn 1:** "Add a user authentication system"
**Turn 2:** "Now add the admin panel" (assuming auth is correct)
**Turn 5:** "Why isn't the admin panel checking permissions?"

Verify each step before building on it.

## Knowing When You're Done

Iteration can become infinite if you don't have clear stopping criteria.

**You're done when:**
- Output meets your acceptance criteria (from Module 1)
- Further changes would be polish, not substance
- You'd accept this from a human colleague

**You're not done when:**
- "It's probably fine" (verify, don't assume)
- "I can fix it later" (unless fixing is genuinely trivial)
- "I'm tired of this" (take a break, don't lower standards)

## Practice Exercise

```
EXERCISE:
You asked AI to write a Python function that calculates compound interest. The first version:
- Uses the wrong formula (simple interest instead of compound)
- Has a good function signature and docstring
- Handles edge cases well

Plan your iteration:
1. What feedback would you give?
2. What would you keep vs. ask to change?
3. What would make you restart instead of refine?
4. How would you verify the fix?
```

## Key Takeaways

- Iteration is normal, not failure — most AI interactions require refinement
- Three responses: accept (good enough), refine (iterate), restart (fresh context)
- Good feedback is specific, shows the gap, and acknowledges what's working
- Use the "three strikes" heuristic: same feedback three times means restart
- Long conversations degrade — break complex tasks into sessions
- Be direct (not rude), focused (one thing at a time), and verify before building
- Know your stopping criteria before you start

---

Next: **Module 6: The Agentification Shockwave** →
