# Module 2: Structured Thinking

Module 1 explained what an LLM is: a system that generates plausible continuations of whatever you give it. The practical consequence is that *what you give it* is nearly everything. This module is about the skill of expressing what you want — clearly enough that a system with no access to your head can act on it.

## The Specification Gap

Every interaction with AI involves a gap:

```
What you want (in your head)
        ↓
    [THE GAP]
        ↓
What you expressed (prompt/instruction)
        ↓
What AI interpreted
        ↓
What AI produced
```

Your job is to **minimise the specification gap** — the distance between your intent and your expression of it.

This is a new skill. It didn't exist before because:
- **Programming** required precision, but the compiler enforced it
- **Writing** was for human readers who could infer and ask questions
- **Management** relied on humans to interpret documents and use judgment

AI accepts natural language (so you *can* be vague) but executes autonomously (so vagueness causes real problems). And as Module 1 showed, when you leave gaps, the AI doesn't stop to ask what you meant — it fills them with the most *plausible* interpretation, which may not be yours.

## The Five Components of Clear Specification

### 1. Linearisation

Human thought is associative, parallel, recursive. AI works best with linear dependency chains.

**Before (human thinking):**
> "I need a website for my bakery — oh it should have nice photos — and online ordering — but maybe just a contact form first — actually the menu is most important"

**After (linearised for AI):**
> 1. Create a single-page website with these sections in order:
>    - Header with bakery name and logo placeholder
>    - Menu section displaying items with prices
>    - Contact form (name, email, message)
>    - Footer with address and hours
> 2. Use a warm colour palette (cream, brown, soft orange)
> 3. Make it mobile-responsive
> 4. [Future phase: online ordering]

The skill is **serialising** the non-linear mental model into ordered steps with clear dependencies.

```
EXERCISE:
Take this messy request and linearise it:

"Can you help with my presentation? It's for the board meeting next week about the Q3 results. I need charts but also some narrative. Oh and there was that customer complaint we resolved — that's a good story. The CFO wants to see the numbers compared to forecast. Make it look professional but not boring."

Write out a structured, linearised specification that an AI could act on.
```

### 2. Context Externalisation

Humans carry implicit context. AI only knows what's in the prompt.

**Human assumption:** "You know what I mean by 'the project'"

**Reality:** The AI has no idea which project, what state it's in, or what you've discussed before (unless it's in the current context).

**Before:**
> "Now make it work for the other case too"

**After:**
> "The function currently handles single items. Modify it to also accept an array of items and process each one, returning an array of results. Keep the single-item behaviour as the default."

The skill is **externalising what you're holding in your head**.

```
QUIZ:
Which of these prompts has the best context externalisation?

* "Fix the bug we discussed"
* "The login function returns null when the user doesn't exist. Instead, it should throw a UserNotFoundError with the attempted username."
*! "In src/auth/login.ts, the login() function on line 45 returns null when User.find() returns undefined. Change it to throw a UserNotFoundError with message 'User not found: {username}'."
* "Make the auth work properly"

FEEDBACK: The third option provides file location, current behaviour, desired behaviour, and specific details — everything needed to act without guessing.
```

### 3. Appropriate Abstraction Level

Too high-level: "Make it better" — AI can't act meaningfully
Too low-level: "Change line 47 to use forEach" — you're doing the thinking

The right level: You specify **what** without specifying **how**.

| Too Vague | Right Level | Too Specific |
|-----------|-------------|--------------|
| "Improve performance" | "The current implementation loads all 10,000 records before filtering. Refactor to filter at the database query level." | "Add a WHERE clause to line 23 of query.sql" |
| "Make it secure" | "Add input validation to prevent SQL injection in the search function" | "Use parameterised queries with $1 placeholders" |
| "Better error handling" | "When the API returns a 4xx error, show the user a message instead of crashing" | "Wrap line 56 in try-catch" |

```
EXERCISE:
For each of these, write a specification at the "right level":

1. Too vague: "Make the dashboard faster"
2. Too specific: "Add `useMemo` to the `calculateTotals` function on line 89"
3. Too vague: "The tests are flaky"
```

### 4. Verifiable Acceptance Criteria

Humans often know success when they see it. AI needs checkable conditions.

**Before:**
> "Make the form validation better"

**After:**
> Add validation to the contact form:
> - Email field: reject if not matching standard email format, show "Please enter a valid email"
> - Message field: require minimum 10 characters, show character count
> - Submit button: disable until all validations pass
> - On successful submission: show green confirmation banner for 3 seconds

The skill is **converting intuitive quality judgments into testable specifications**.

This connects directly to Test-Driven Development — if you can write the test first, you have a verifiable specification.

### 5. Scope Boundaries

Humans have implicit scope. AI will do exactly what it's told, or interpret ambiguously.

**Before:**
> "Clean up the codebase"

**After:**
> Refactor the `/src/utils` folder:
> - Remove functions not imported anywhere
> - Consolidate duplicate helper functions
> - Add JSDoc comments to exported functions
>
> **Boundaries:**
> - Do NOT modify files outside `/src/utils`
> - Do NOT change function signatures used elsewhere
> - Do NOT delete test files

The skill is **defining what's in and out of scope explicitly**.

```
QUIZ:
What's wrong with this specification?

"Update the user profile page to show the user's recent activity. Make it look nice and match the rest of the site."

* It's too long
*! It lacks scope boundaries — "match the rest of the site" could mean changing other pages
* It's too technical
* Nothing is wrong with it

FEEDBACK: Without explicit boundaries, AI might modify other pages to "match" or interpret "recent activity" in unexpected ways (last hour? last year? all activity types?).
```

## Putting It Together

A well-structured specification includes:

1. **Context:** What exists now, what state things are in
2. **Goal:** What you want to achieve (linearised if complex)
3. **Constraints:** What to avoid, what's out of scope
4. **Acceptance criteria:** How you'll know it's done
5. **Abstraction level:** Enough detail to act, not so much you're writing the solution

## Prompt Hygiene and Reusable Playbooks

Once you find a prompt pattern that works, **treat it as a reusable asset**.

Good prompt hygiene means:
- **Versioning** your prompts (date or revision tag)
- **Naming** prompts by purpose (“spec-to-test”, “risk-review”, “edge-cases”)
- **Keeping known‑good examples** alongside the prompt
- **Logging outcomes** (what worked, what failed, and why)

This turns prompt writing from improvisation into **repeatable practice**.

**Example playbook snippet:**

1. *Context summary* (current state + constraints)
2. *Explicit goal* (what should change)
3. *Acceptance criteria* (tests or checks)
4. *Scope boundaries* (what must not change)
5. *Edge cases* (inputs that must be handled)

Over time, teams build a library of prompts that reduce variance and speed up collaboration.

## Practice Exercise

```
EXERCISE:
You want to add a dark mode toggle to a web application. Write a complete specification using all five components.

Include:
- Current context (what exists)
- Linearised steps
- Explicit constraints
- Verifiable acceptance criteria
- Clear scope boundaries

Compare your specification to one generated by AI — where did you need to be more explicit?
```

## Key Takeaways

- The specification gap is the distance between intent and expression
- Linearisation converts parallel thinking into sequential steps
- Context externalisation makes implicit assumptions explicit
- Abstraction calibration finds the right level of detail
- Acceptance criteria convert "I'll know it when I see it" into testable conditions
- Scope boundaries prevent unexpected side effects

---

Next: **Module 3: Precision Without Formalism** →
