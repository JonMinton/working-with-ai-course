# C3. Visual Collaboration

## The Description-to-Visual Gap

You have an image in your mind. You describe it in words. AI generates something... different.

This gap is fundamental to visual collaboration:

```
┌─────────────────────────────────────────────────────────────┐
│              THE VISUAL TRANSLATION PROBLEM                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Your mental      Your verbal       AI's              AI's │
│     image    →    description   →  interpretation  →  output│
│                                                             │
│     [rich]         [limited]        [different]      [fixed]│
│                                                             │
│   Each step loses or distorts information                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

Every word you choose constrains and guides — but also potentially misleads.

## Types of Visual AI

Different tools, different capabilities:

| Type | Examples | Strengths | Limitations |
|------|----------|-----------|-------------|
| **Image generation** | DALL-E, Midjourney, Stable Diffusion | Creates from description | Unpredictable details, hands, text |
| **Image editing** | Photoshop AI, DALL-E edit | Modifies existing images | Needs clear region/intent |
| **Code generation** | Claude, GPT for CSS/SVG | Precise control via code | You must render and verify |
| **Design assistance** | Figma AI, Canva AI | Context-aware suggestions | Limited to tool's framework |

This module focuses on principles that apply across tools.

## Describing Visual Intent

### Be Specific About What Matters

Vague: "A nice logo"

Specific: "A wordmark logo for a law firm. Modern, minimal. Sans-serif typography. Dark blue (#1e3a5f) on white. No icons or symbols — just the firm name 'Morrison & Associates' with considered kerning."

**The rule:** If it matters, say it. If you don't say it, AI will decide.

### Use Reference Language

Borrow vocabulary from design:

| Instead of... | Try... |
|--------------|--------|
| "Make it look good" | "Increase white space, align elements to grid" |
| "More modern" | "Flat design, sans-serif, minimal ornamentation" |
| "Warmer feeling" | "Shift palette toward amber/ochre, add organic shapes" |
| "More professional" | "Increase contrast, reduce decoration, tighten alignment" |

You don't need to be a designer — but specific language gets specific results.

### Specify Composition

For complex images, describe spatial relationships:

> "A workspace scene. In the foreground, a laptop slightly left of center. Behind it, a coffee cup on the right. Background: blurred bookshelf. Lighting from top-left, creating soft shadows. Aspect ratio 16:9, suitable for a blog header."

Elements to consider:
- Foreground / midground / background
- Left / center / right positioning
- Scale relationships
- Lighting direction
- Aspect ratio and intended use

```
EXERCISE:
You want an illustration for a blog post about "work-life balance."

Write two prompts:
1. A vague prompt (how most people would describe it)
2. A specific prompt with composition, style, and colour guidance

Compare what you'd expect to get from each.
```

## The Iteration Loop for Visual Work

Visual iteration follows a specific pattern:

### Step 1: Generate Initial Options

Ask for multiple variations:

> "Generate 4 different approaches to this concept. Vary the style and composition."

Don't commit to one direction too early.

### Step 2: Identify What Works

For each output, note:
- What works (keep this)
- What doesn't (change this)
- What's missing (add this)

Be specific: "The colour palette works, but the figure's pose feels static."

### Step 3: Refine with Precision

Don't just say "make it better." Target specific elements:

> "Keep the overall composition and colour palette. Change: make the figure more dynamic (leaning forward), increase contrast between foreground and background, sharpen the edges of the main subject."

### Step 4: Know When to Pivot

If refinement isn't converging, start fresh with a new approach rather than endlessly tweaking.

## Working with AI-Generated Code (CSS, SVG)

When AI generates visual code (CSS, HTML, SVG), you have more control but a different workflow:

```
┌─────────────────────────────────────────────────────────────┐
│                CODE-BASED VISUAL WORKFLOW                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Describe intent → AI generates code → You render it       │
│         ↓                                     ↓             │
│   AI cannot see      ←     You describe     ←  You see      │
│   the rendered result      what's wrong        the result   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Critical insight:** AI cannot see what the code produces. You must be the visual verifier.

### Describing Code-Based Visual Problems

When something looks wrong, describe it precisely:

**Unhelpful:** "The layout is broken"

**Helpful:** "The sidebar is overlapping the main content by about 50 pixels on screens narrower than 1024px. The sidebar should collapse to a hamburger menu below 768px."

**Unhelpful:** "The colours are off"

**Helpful:** "The button background (#3b82f6) doesn't have enough contrast against the dark header (#1f2937). The button text is unreadable. Either lighten the button to #60a5fa or move it outside the header."

### Providing Visual Context

When AI can't see, give it data:

> "Current state: The card has 20px padding, 8px border-radius, a 1px #e5e7eb border, and a subtle box-shadow. The problem: it feels too heavy. Make it lighter and more airy while keeping it visually distinct from the background."

Numbers, colours, and measurements give AI something to work with.

```
QUIZ:
AI generated CSS for a hero section. The text is hard to read against the background image. What's the most effective feedback?

* "Make the text more readable"
* "Fix the contrast issue"
*! "Add a semi-transparent dark overlay (rgba(0,0,0,0.5)) behind the text, or add a text-shadow to the heading"
* "Change the background image"

FEEDBACK: Specific technical solutions are more actionable than describing the problem. You're the one who can see the issue — propose a fix.
```

## Style References and Mood Boards

### Using Existing Work as Reference

When words aren't enough, reference existing work:

> "Style similar to the illustrations on Notion's homepage — flat, minimal, geometric shapes, limited colour palette with one accent colour, subtle textures."

**Ethical note:** Reference style for inspiration, not replication. "In the style of [famous artist]" can raise copyright and ethical concerns.

### Building a Mood Board

For complex projects, compile visual references:

- Colour palettes you like
- Typography examples
- Composition approaches
- Texture and pattern samples

Share these with AI (if it can accept images) or describe their key characteristics.

## Common Visual AI Pitfalls

### The "Make It Pop" Problem

Vague feedback leads to unpredictable changes:

| Vague | What You Might Get |
|-------|-------------------|
| "Make it pop" | Higher saturation, more contrast, random changes |
| "More dynamic" | Arbitrary motion blur, skewed elements |
| "Cleaner" | Could mean minimal, could mean aligned, could mean simpler |

Always translate vague instincts into specific requests.

### The Iteration Drift Problem

Each change can introduce new problems:

> Turn 1: Fix the spacing → Turn 2: Now the alignment is off → Turn 3: Alignment fixed but colours changed → Turn 4: Colours fixed but spacing is back...

**Solution:** Be explicit about what to preserve:

> "Fix the alignment issue. Keep everything else exactly as is — colours, spacing, typography, all unchanged."

### The Detail Obsession Problem

Spending hours perfecting details that don't matter:

**Ask yourself:**
- Will anyone notice this in context?
- Does this affect the core message?
- What's the opportunity cost of this iteration?

## When to Abandon AI

AI visual generation isn't always the answer:

**Consider alternatives when:**
- You need pixel-perfect precision
- Brand guidelines are strict
- The output must exactly match a reference
- You've iterated many times without satisfaction
- The work will be scrutinised closely

Sometimes Figma, Photoshop, or a professional designer is the right choice.

```
EXERCISE:
You need a simple icon for "settings" (gear icon) in a specific style: 24x24px, 2px stroke, rounded corners, single colour (#6b7280).

1. Try to get AI to generate SVG code for this
2. Note how many iterations it takes
3. Consider: Would drawing it manually have been faster?
```

## Key Takeaways

- The description-to-visual gap is fundamental — every word choice constrains and guides
- Be specific about what matters; use design vocabulary
- Specify composition: foreground/background, positioning, lighting, aspect ratio
- For code-based visuals, you must verify — AI cannot see rendered output
- Give AI numbers, colours, measurements when describing problems
- Use style references and mood boards for complex projects
- Avoid vague feedback ("make it pop") — translate to specific requests
- Know when to abandon AI and use other tools

---

Next: **C4. Attribution & Originality** →
