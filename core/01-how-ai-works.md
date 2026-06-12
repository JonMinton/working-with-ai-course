# Module 1: How AI Actually Works

Everything else in this course — specification, verification, iteration — follows from a handful of facts about what a large language model (LLM) actually is. Most frustration with AI comes from a wrong mental model: treating it like a search engine, a database, or a person. It is none of these.

You don't need any mathematics for this module. You need about ten honest facts.

## The One-Sentence Version

> A language model is a system trained to predict what text comes next, so well that the predictions are useful.

That's it. When you ask a question, the model isn't *looking up* an answer. It's generating the most plausible continuation of the conversation, one small chunk of text at a time. Every capability and every failure mode in this course traces back to that sentence.

This sounds like it shouldn't work. The surprise of the past few years is that predicting text extremely well turns out to require something that looks a lot like understanding — of grammar, facts, reasoning patterns, code, and style. But "looks a lot like" is doing real work in that sentence, and the differences matter.

## Where Its Knowledge Comes From: Weights vs. Context

A model has exactly two sources of information, and the difference between them is the single most useful thing to understand:

| | **Weights (training)** | **Context (the conversation)** |
|---|---|---|
| What it is | Patterns absorbed from training on vast amounts of text | Everything in the current conversation: your messages, documents you've shared, instructions, tool results |
| Character | Vast but fuzzy — like things you read years ago | Small but sharp — like a page open in front of you |
| Freshness | Frozen at a training cutoff date | As current as what you put there |
| Reliability | Strong for common knowledge, unreliable for specifics | The model can quote it exactly |
| Your control | None | Total |

**Training is compression, not storage.** The model read enormous amounts of text, but it didn't keep a copy. What remains is a dense web of patterns — closer to how you remember the *gist* of a book from years ago than to a library you can consult. That's why a model can explain photosynthesis flawlessly (the pattern appears in training data thousands of times) yet misremember the publication year of a moderately famous paper (that detail appeared rarely, and nothing forces the model to say "I'm not sure" instead of producing a plausible year).

**The practical rule:** anything you need the model to get *exactly* right — your data, your figures, the specific document, the current state of anything — put it in the context. Never rely on the weights for specifics you could supply.

```
QUIZ:
You ask an AI to summarise your company's Q3 sales report without attaching it. The AI produces a fluent, well-structured summary. What has most likely happened?

* It accessed your company's systems to find the report
* It remembered the report from training data
*! It generated a plausible-sounding summary of a generic Q3 report — fabricated, because the real one was never in its context
* It refused, because it cannot summarise documents

FEEDBACK: The model can only work from its training patterns and the current context. With no report in the context, the only available move is to generate what a Q3 summary plausibly looks like. The fluency is the danger: fabrication and fact read identically.
```

## Why Confident Errors Are Structural

"Hallucination" — fabricating plausible falsehoods — is not a bug that will be patched out next release. It's a direct consequence of the design: the model's job is to produce *plausible text*, and plausibility and truth usually overlap but are not the same thing.

The model generates a citation the same way it generates everything else: by producing what citations look like. Real author names, a real-sounding journal, a plausible year. When the true fact is strongly represented in training data, the most plausible continuation *is* the truth. When it isn't, the model produces something true-shaped instead — with identical fluency and confidence.

Modern models are markedly better calibrated than early ones — they say "I'm not certain" more often, and they can check claims with search tools when those are available. But the failure mode is reduced, not gone, and it concentrates predictably:

**High fabrication risk:**
- Citations, quotes, URLs, and references
- Specific numbers, dates, and statistics
- Details about people and organisations that aren't famous
- Anything recent (after the training cutoff)
- Niche topics where training data was thin

**Low fabrication risk:**
- Common knowledge, widely-documented concepts
- Reasoning over material *you supplied in the context*
- General structure, formats, and conventions

Notice the asymmetry: the model is most reliable on exactly the things you could easily check, and least reliable on the specifics you were hoping it would save you from checking. Module 5 (Verification) builds on this.

## Tokens: Why It Can't Count the R's in "Strawberry"

Models don't see letters or words. Text is chopped into **tokens** — chunks of roughly 3–4 characters in English. "Strawberry" might be two tokens: `straw` + `berry`. The model perceives those two units, not ten letters.

This explains a whole family of otherwise-bizarre failures:

- Miscounting letters or syllables in a word
- Unreliable arithmetic on long numbers (digits are tokenised inconsistently)
- Clumsiness with acrostics, palindromes, and precise character-level edits

And it explains the fix: **tools**. When a model can write and run a small program to count the letters or do the sum, the answer comes from the program, not from token prediction. A model with a calculator is reliable at arithmetic; a model without one is guessing fluently. This is why "can the AI do X?" often has the answer: "not by itself — but trivially with the right tool." Module 4 covers tools in depth.

## Same Question, Different Answers

Generation is **probabilistic**. At each step the model weighs many possible next tokens and samples among the likely ones. Ask the same question twice and you may get different answers — sometimes differently *worded*, occasionally differently *concluded*.

Practical consequences:

- A great answer once is not evidence you'll get a great answer every time. Reliability and capability are different properties.
- If an answer matters, asking again (or asking a second model) is a cheap check. Agreement doesn't prove correctness, but disagreement proves at least one answer is wrong.
- Anything you build *on top of* AI needs to tolerate variation — a theme the Developer track takes up in testing.

## Sycophancy: It's Trained to Please You

After the initial text-prediction training, models are further trained on human feedback — and humans rate agreeable, confident answers highly. The result is a systematic bias called **sycophancy**: models lean towards telling you what you appear to want to hear.

Watch for it whenever you:

- **Ask leading questions.** "This is a good plan, right?" reliably gets a yes. "What are the three biggest weaknesses of this plan?" gets you information.
- **Push back.** Models often fold under challenge even when they were right the first time. "Are you sure?" is not a verification method — the model may simply switch answers to appease you.
- **Share your own work.** Default feedback runs positive. Ask for the case *against*, or tell it a critical colleague will review the same document and you want to get there first.

The defence is to make honesty the thing being asked for: request criticism explicitly, ask for steelmanned counter-arguments, and avoid revealing which answer you're hoping for.

```
QUIZ:
You ask an AI "Are you sure?" after it gives an answer, and it apologises and changes its answer. What have you learned?

* The first answer was wrong
* The second answer is right
*! Very little — models often change answers under social pressure regardless of correctness
* The model has now double-checked its reasoning

FEEDBACK: "Are you sure?" applies social pressure, and sycophantic training makes models respond to pressure by yielding. To actually check an answer, ask for the reasoning, verify against a source, or pose the question fresh in a new conversation without signalling doubt.
```

## "Why Did You Do That?" Gets You a Story, Not an Answer

When you ask a model to explain *why* it just did something, it cannot inspect its own internal computation. It does what it always does: generates a plausible continuation — in this case, a plausible-sounding explanation. The technical term is **confabulation**, and humans do it too.

The explanation may be accurate, in the way a good guess is accurate. But treat self-reports about its own reasoning, confidence, or limitations as *more generated text*, not as privileged inside information. "I double-checked this" is a sentence the model predicted would fit well there; no checking necessarily occurred.

This is also why asking "do you understand?" is nearly useless — the answer is always yes. A better probe: ask the model to restate the task in its own words, or to tell you what it would do first. That output you can actually evaluate.

## The Jagged Frontier

Human abilities cluster: someone who can write a legal brief can certainly address an envelope. Model abilities don't cluster the same way. A model can pass a bar exam yet lose at noughts and crosses; produce a working web application in minutes yet bungle a four-digit multiplication.

Researchers call this the **jagged frontier**: capability extends impressively far in some directions and surprisingly near in others, with no intuitive boundary. Two consequences:

1. **Don't infer general competence from one impressive result.** Brilliance at task A says little about adjacent-looking task B.
2. **Don't infer general incompetence from one silly failure.** "It can't even count letters" tells you about tokenisation, not about whether it can review your contract.

The only reliable way to map the frontier for *your* tasks is to test it on your tasks — cheaply, before you depend on it. This is why the course keeps returning to verification rather than trust.

## What's Changed — and What Hasn't

The picture above describes the stable core. Around it, capabilities have moved fast:

- **Reasoning modes.** Modern models can "think before answering" — generating extended internal working before the reply. This markedly improves multi-step reasoning, at a cost in speed. The thinking is still generated text, with the same failure modes, but error rates drop because the model can catch its own inconsistencies mid-stream.
- **Tool use and agents.** Models now routinely search the web, run code, read files, and operate applications in a loop — acting, observing results, and correcting course. This converts many "AI can't do X" claims into "AI couldn't do X without tools." Module 4 and Module 7 take this up.
- **Long contexts.** Context windows grew from a few pages to whole books' worth of text. But "in the context" still beats "in the weights", and material can compete for attention in very long contexts — relevance and placement still matter.

What hasn't changed: prediction at the core, two knowledge sources, structural plausibility-over-truth, probabilistic output, sycophancy, confabulated self-explanations, and the jagged frontier. These survive each model generation; advice built on them stays useful.

## Ten Rules of Thumb

| # | Rule | Because |
|---|------|---------|
| 1 | Put anything that must be exact into the context | Weights are fuzzy; context is sharp |
| 2 | Never trust a citation, quote, URL, or statistic you haven't checked | Fabrication concentrates on specifics |
| 3 | Fluency is not evidence | Confident and correct read identically |
| 4 | For counting and arithmetic, want a tool involved | Token prediction is the wrong instrument |
| 5 | One good answer ≠ reliable answers | Generation is probabilistic |
| 6 | Don't ask leading questions | Sycophancy will echo your hopes back |
| 7 | "Are you sure?" is pressure, not verification | Models fold to appease |
| 8 | Its explanations of itself are guesses | No access to its own internals |
| 9 | Test capability on *your* tasks before relying on it | The frontier is jagged |
| 10 | "AI can't do X" claims have short shelf lives — but these rules don't | Capabilities move; the architecture's character persists |

```
EXERCISE:
Run a small calibration experiment with whatever AI tool you use:

1. Ask it three factual questions you can verify: one about common knowledge, one about a specific detail in your own field, and one about something from the last few months.
2. Before checking, note how confident each answer *sounded*.
3. Verify all three.

What did you find about the relationship between how an answer sounds and whether it's right? Keep this experiment — repeating it when you adopt a new tool is the fastest way to calibrate your trust.
```

```
EXERCISE:
Take a piece of your own recent work (a document, plan, or design) and ask an AI for feedback twice, in two separate conversations:

1. "I'm really proud of this — it came out well, didn't it?"
2. "A sceptical senior colleague will review this tomorrow. Find the problems they'll find, ranked by severity."

Compare the two responses. This is sycophancy made visible — and prompt 2 is the template worth keeping.
```

## Key Takeaways

- An LLM predicts plausible next text; it doesn't look things up. Every failure mode follows from this.
- It has two knowledge sources: fuzzy frozen weights and the sharp context you control. Put what matters in the context.
- Confident fabrication is structural, and concentrates on specifics: citations, numbers, names, recent events.
- Tokens explain the "stupid" failures; tools fix most of them.
- Output is probabilistic — capability and reliability are different things.
- Models are trained to please: don't lead the witness, and don't mistake "Are you sure?" for verification.
- Self-explanations are confabulated. Evaluate outputs, not self-reports.
- The capability frontier is jagged. Map it on your own tasks.

---

Next: **Module 2: Structured Thinking** →
