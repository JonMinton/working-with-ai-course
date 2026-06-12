# Module 3: Precision Without Formalism

## The Purpose of Formalism

Formalism exists to make **unambiguous statements**. Algebra, logic notation, type signatures — these are all attempts to express ideas without room for misinterpretation.

But there's a failure mode: **notation fetishism** — when the notation itself becomes the subject of study rather than the clarity it was meant to serve.

Consider this formal statement:

> Let Σ be a finite alphabet, and let Σ* denote the Kleene closure of Σ. A language L is regular if and only if there exists a deterministic finite automaton M = (Q, Σ, δ, q₀, F) such that L = L(M).

This is precise. It's also opaque to most practitioners — including, often, the practitioner writing the prompt. If you can't tell whether the formal statement says what you mean, the precision is doing nothing for you.

The same idea, expressed differently:

> A pattern is "regular" if you can match it by reading left-to-right, keeping track of only a fixed number of possible states, without needing to backtrack or remember arbitrary amounts of what you've seen.

This is equally precise for practical purposes and vastly more actionable.

## Multiple Notations for the Same Precision

The same unambiguous statement can often be expressed in:

| Notation | Best For | Example |
|----------|----------|---------|
| **Algebra/Symbols** | Compact, provable | `∀x ∈ Users: x.age ≥ 18` |
| **Pseudocode** | Implementable | `for each user: assert user.age >= 18` |
| **Structured Prose** | Readable | "Every user must be at least 18 years old" |
| **Examples** | Intuitive | "Valid: age=25. Invalid: age=16" |
| **Tests** | Verifiable | `expect(validateAge(16)).toBe(false)` |

The skill is **thinking precisely**, then choosing the notation appropriate to context.

For AI collaboration specifically:
- Modern models handle formal notation competently — but *you* still have to verify the output, and you can only verify what you can read
- Pseudocode works well (close to implementation, readable by you)
- Structured prose with clear definitions works excellently
- Examples are powerful (concrete beats abstract, and mismatches are easy to spot)

```
QUIZ:
Which notation would work best for specifying a sorting requirement to an AI?

* ∀i ∈ [0, n-2]: a[i] ≤ a[i+1]
*! "Sort the array in ascending order, so each element is less than or equal to the next"
* "Make it sorted"
* for(i=0;i<n-1;i++){assert(a[i]<=a[i+1])}
FEEDBACK:The prose version is unambiguous, and both you and the AI can read it without translation. The mathematical notation is equally precise but harder for most people to verify. The code is precise but overly specific about implementation.
```

## Precision in Different Domains

### Describing Data Structures

**Overly formal:**
> A binary tree T is a tuple (V, E, r) where V is a set of vertices, E ⊆ V × V is a set of directed edges, r ∈ V is the root, and ∀v ∈ V: |{(u,v) ∈ E}| ≤ 1 ∧ |{(v,w) ∈ E}| ≤ 2

**Precise but accessible:**
> A binary tree where:
> - Each node has at most 2 children (left and right)
> - Each node except the root has exactly 1 parent
> - There's a single root node with no parent
> - Example: A root with value 5, left child 3, right child 7

### Describing Behaviour

**Overly formal:**
> The function f: String × Int → Option[String] is defined such that f(s, n) = Some(s.substring(0, min(n, s.length))) if s ≠ null, None otherwise.

**Precise but accessible:**
> A function that takes a string and a number, and returns:
> - The first N characters of the string (or the whole string if shorter)
> - Nothing (null/None) if the input string is null
>
> Examples:
> - ("hello", 3) → "hel"
> - ("hi", 10) → "hi"
> - (null, 5) → None

### Describing Constraints

**Overly formal:**
> ∀t ∈ Transactions: t.amount > 0 ∧ t.amount ≤ account(t.from).balance ∧ t.from ≠ t.to

**Precise but accessible:**
> Transaction rules:
> - Amount must be positive
> - Amount cannot exceed sender's balance
> - Sender and recipient must be different accounts

## The Hierarchy of Precision

Not all statements need the same precision level:

```
High stakes / Core logic → Maximum precision
    "A user is considered 'active' if they've logged in within the last 30 days
     AND have completed at least one transaction"

Medium stakes / General behaviour → Clear but flexible
    "The dashboard should load quickly and show relevant information first"

Low stakes / Aesthetic → Directional
    "Use a clean, professional look"
```

Match precision to stakes. Over-specifying low-stakes decisions wastes effort and constrains unnecessarily.

```
EXERCISE:
Categorise these requirements by precision level needed, then write an appropriately precise specification for each:

1. How user passwords should be validated
2. What colour the submit button should be
3. When a background job should retry after failure
4. How the landing page should "feel"
```

## Definitions as Precision Tools

One of the most powerful precision techniques: **define your terms explicitly**.

**Ambiguous:**
> "Show recent orders"

**Precise (via definition):**
> Show recent orders.
>
> **Definition:** "Recent" means placed within the last 7 days.
> **Definition:** "Order" includes completed purchases only, not abandoned carts.

This pattern — statement plus definitions — gives you prose readability with formal precision.

## Precision Through Structure

Structure itself creates precision. Compare:

**Unstructured:**
> The user should be able to search for products by name or category, and results should show the product image, name, price, and rating, sorted by relevance by default but with options to sort by price or rating, and there should be filters for category, price range, and minimum rating.

**Structured:**
> **Search Functionality**
>
> *Inputs:*
> - Query: matches product name OR category
>
> *Result Display (per item):*
> - Product image
> - Name
> - Price
> - Rating
>
> *Sorting:*
> - Default: relevance
> - Options: price (asc/desc), rating (desc)
>
> *Filters:*
> - Category (multi-select)
> - Price range (min-max)
> - Minimum rating (1-5 stars)

Same information. The structured version is unambiguous about what's a filter vs. a sort, what's optional vs. required.

## When AI Misunderstands: Precision Diagnosis

When AI produces something wrong, ask: **was this a precision failure?**

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| AI did something unexpected | Scope boundaries unclear | Add explicit "do NOT" constraints |
| AI made wrong assumptions | Context not externalised | State current situation explicitly |
| AI over-interpreted | Abstraction level too high | Add concrete examples or constraints |
| AI under-interpreted | Abstraction level too low | Back off, state goal not method |
| AI got details wrong | Definitions ambiguous | Define key terms explicitly |

```
EXERCISE:
You asked AI: "Add pagination to the user list"

AI added pagination but:
- Used page numbers instead of your preferred "Load More" pattern
- Set page size to 10 when you wanted 25
- Added pagination to the admin user list too, not just the public one

Write a revised specification that would prevent all three issues.
```

## A Useful Distinction: What Does the AI Actually Receive?

A practical precision habit: know what form your material reaches the model in. Models work on text (and, increasingly, images); everything else has to be converted first.

| Type | Examples | What happens when you share it |
| :--- | :--- | :--- |
| **Plain text** | `.txt`, `.md`, `.csv`, `.html`, `.py` | The model reads the characters directly — nothing is lost |
| **Binary documents** | `.pdf`, `.docx`, `.xlsx` | A tool extracts text (and sometimes layout) first. Extraction can silently drop tables, footnotes, formulas, or scanned pages |
| **Images** | `.png`, `.jpg`, screenshots | Modern models can view images directly, but fine detail (small text, dense charts) may be misread |
| **Audio/video, archives** | `.mp3`, `.mp4`, `.zip` | Need transcription or unpacking by a tool before any content reaches the model |

Most chat tools now handle these conversions automatically, which makes it easy to forget they're happening. The failure mode has shifted accordingly: it's less "the AI can't open my PDF" and more "the AI read a *lossy extraction* of my PDF and neither of us noticed what was missing." If an answer depends on a table, a figure, or precise formatting, check that the AI actually received it — ask it to quote the relevant passage back. When something seems off, the question to ask is: *what did the model actually receive?*

## Key Takeaways

- Formalism serves precision; notation is just a vehicle
- The same precise idea can be expressed in multiple notations
- Choose notation based on context (AI collaboration favours prose and examples)
- Match precision level to stakes
- Explicit definitions transform ambiguous prose into precise specification
- Structure creates precision even in natural language
- When AI misunderstands, diagnose whether it's a precision failure

---

Next: **Module 4: Understanding AI Systems** →
