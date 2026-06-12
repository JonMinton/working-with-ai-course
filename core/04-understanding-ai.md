# Module 4: Understanding AI Systems

## The Four Components

To work effectively with AI, you need a mental model of what you're working with. Every AI system you use — a chat window, a coding assistant, a research tool — is built from four distinct components that are often conflated:

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │   CONTEXT   │───▶│    MODEL    │───▶│   TOOLS     │     │
│  │             │    │             │    │             │     │
│  │ Everything  │    │ Interprets, │    │ What it can │     │
│  │ the model   │    │ reasons,    │    │ do in the   │     │
│  │ sees now    │    │ decides     │    │ world       │     │
│  └─────────────┘    └──────┬──────┘    └─────────────┘     │
│                            │                               │
│                            ▼                               │
│                    ┌─────────────┐                         │
│                    │   MEMORY    │                         │
│                    │             │                         │
│                    │ What carries│                         │
│                    │ across      │                         │
│                    │ interactions│                         │
│                    └─────────────┘                         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

Understanding these separately helps you:
- Diagnose problems correctly
- Set appropriate expectations
- Design better workflows
- Communicate clearly about AI capabilities

(And when these four run in a loop towards a goal, you get an **agent** — we'll define that properly below.)

## Component 1: The Model

**What it is:** The underlying AI model — its capabilities, training, reasoning patterns. This is the next-token predictor from Module 1.

**Key properties:**
- Different models have different capabilities (Claude, GPT, Gemini, Llama, etc.)
- Models have training cutoffs — they don't "know" events after a certain date
- Models have characteristic strengths and weaknesses
- The model itself is **stateless** — it doesn't remember between calls

**Common misconceptions:**

| Misconception | Reality |
|---------------|---------|
| "The AI learned from our conversation" | Models don't learn from individual conversations |
| "This AI is smarter than that one" | Different models have different trade-offs, not linear ranking |
| "The AI knows about X" | It only knows what was in training data before cutoff |
| "The AI is being stubborn" | It's following patterns in its training; there's no intent |

**What varies by model:**
- Reasoning capability (including whether it can "think" at length before answering)
- Context window size
- Speed / latency
- Cost
- Training data recency
- Specific domain knowledge
- Safety behaviours

Most providers now offer a fast/cheap tier and a slow/capable tier. Matching the model to the task — quick drafts on the cheap tier, high-stakes reasoning on the capable one — is a small decision that compounds.

```
QUIZ:
You had a great conversation with an AI yesterday where you explained your project in detail. Today you start a new conversation. What does the AI know about your project?

* Everything from yesterday
* A summary of yesterday
*! Nothing — unless you tell it again or there's explicit memory/persistence
* It depends on the model
FEEDBACK:By default, each conversation starts fresh. The model itself doesn't retain information. Any "memory" requires explicit persistence systems.
```

## Component 2: The Context

**What it is:** Everything the model receives as input — your message, system prompts, conversation history, any retrieved documents. (Module 1 called this the "sharp" knowledge source — the one you control.)

**Key properties:**
- There's a maximum size (the context window) — now typically hundreds of thousands of tokens, around a million on some models (roughly a long novel's worth)
- Everything the model "knows" for this interaction is in the context
- Big windows don't make curation pointless: material competes for attention, and relevant-but-buried details get missed
- System prompts set behaviour; user prompts are your requests

**The context includes (typically):**
1. System prompt (often hidden) — instructions for how to behave
2. Conversation history — previous turns in this conversation
3. Retrieved context — documents, search results, file contents
4. Your current message

**What the model does NOT have access to:**
- Your files (unless explicitly provided)
- Your screen (unless there's a screenshot tool)
- Your other conversations
- Information not in the current context

```
EXERCISE:
You're working with an AI on a codebase. You've been discussing the authentication module for an hour. Now you ask: "What about the payment module?"

List what the AI knows and doesn't know about the payment module at this point.
```

**Context window management:**
- Long conversations eventually exceed the window
- Older messages may be truncated or summarised
- You can't assume the AI "remembers" early conversation details
- This is why re-stating context helps

## Component 3: Tools (Capabilities)

**What it is:** Actions the agent can take beyond generating text — code execution, web search, file operations, API calls.

**Key properties:**
- Base models only generate text — tools extend capabilities
- Tool availability varies by platform and configuration
- You (or your organisation) decide what tools to provide
- Tools have their own failure modes (network errors, permissions, etc.)

**Common tool categories:**

| Category | Examples | What It Enables |
|----------|----------|-----------------|
| **Information** | Web search, file reading | Access to external knowledge |
| **Execution** | Code interpreter, shell | Running code, computations |
| **Creation** | File writing, image generation | Producing artifacts |
| **Integration** | APIs, MCP servers | Connecting to other systems |

**The tool boundary is a trust boundary:**
- Tools are how AI affects the real world
- More tools = more capability = more risk
- Enterprise deployments often restrict tools

## Tool Risk and Permissions Model

Treat tool access like **permissions**, not features. The goal is to reduce blast radius.

**Principles:**
- **Least privilege:** only the tools and scopes needed for the task
- **Approval gates:** high‑impact actions require explicit human approval
- **Separation of duties:** different tool sets for draft vs. execution
- **Auditability:** log who requested what, when, and why

**Practical examples:**
- A drafting assistant can read documents but cannot send emails
- A data analyst can query a database but cannot modify records
- A deployment assistant can propose changes but cannot apply them

```
QUIZ:
An AI assistant doesn't have web search enabled. You ask it about a news event from last week. What happens?

* It searches the web anyway
* It tells you it can't access the web and explains its knowledge cutoff
*! It might answer based on training data (possibly outdated) or acknowledge uncertainty
* It refuses to answer
FEEDBACK:Without tools, the AI can only use its training data. It might answer (if the event is in training data) or acknowledge it doesn't know. Good AI systems are transparent about this.
```

## Component 4: Memory / Persistence

**What it is:** What carries across interactions — conversation history, stored preferences, external databases, files.

**Key properties:**
- Default: nothing persists (stateless)
- Conversation history is one form of persistence (but limited by context window)
- Some systems have explicit "memory" features
- External storage (files, databases) can provide persistence

**Types of persistence:**

| Type | Scope | Mechanism |
|------|-------|-----------|
| **None** | Single response | Stateless API call |
| **Conversation** | Single session | History in context |
| **Session memory** | Explicit save/recall | Platform feature |
| **External storage** | Permanent | Files, databases |
| **Project context** | Shared | Documentation, codebase |

**Design questions for persistence:**
- What should the AI "remember" about me/my project?
- How much context window space does this consume?
- Who controls what's stored? (Privacy implications)
- What happens when I want it to "forget"?

```
EXERCISE:
You're designing an AI assistant for a legal firm. Consider:

1. What should persist across sessions? (Client matters, preferences, etc.)
2. What should NOT persist? (Privileged information, speculation, etc.)
3. How would you implement these boundaries?
```

## So Where's the "Agent"?

You'll hear "agent" constantly. Here is the clean definition:

> An **agent** is a model running in a loop with tools, working towards a goal: it acts, observes the result, and decides what to do next — repeating until the goal is met or it needs your input.

A chat assistant answers and stops. An agent might read your files, run code, notice the tests fail, fix the code, re-run the tests, and *then* report back. Same model — the difference is the loop and the tools.

This matters because autonomy changes the stakes. With a chat answer, mistakes cost you only the time to notice them. With an agent, mistakes can be *acted on* — files changed, emails sent, records updated — before you've seen anything. That's why the rest of this module treats tool access as a permissions question, and why Module 5's verification habits apply with extra force to agents.

## Why Keeping These Separate Matters

When AI does something unexpected, diagnose by component:

| Symptom | Possible Cause | Component |
|---------|---------------|-----------|
| "It doesn't know about X" | Not in training data | Model |
| "It doesn't know about X" | Not in current context | Context |
| "It can't do X" | Tool not available | Tools |
| "It forgot X" | Not persisted | Memory |
| "It's worse than yesterday" | Different model or version | Model |
| "It's ignoring my instructions" | Truncated or buried in context | Context |

**Debugging framework:**
1. Is this a **model** limitation? (Capability, training cutoff)
2. Is this a **context** issue? (Missing information, poor structure, buried instructions)
3. Is this a **tool** issue? (Unavailable, failed, wrong permissions)
4. Is this a **memory** issue? (Context lost, not retrieved)

## The "Capable Temp" Mental Model

A helpful metaphor for AI agents:

> **"A very capable temp who arrives each morning with no memory of yesterday, works only from the briefing you give them, and walks out at the end of the day with nothing carried over."**

This captures:
- Capability (not just a tool — can reason and adapt)
- No memory between sessions (each conversation starts independently)
- Scoped access (only what you provide in the briefing)
- No carryover (the working relationship resets each time)

The key nuance: any files, documents, or outputs the temp *produces during the day* are yours — they're saved in your project, your repository, your file system. What doesn't persist is the temp's own *working memory* — their understanding of context, preferences, and prior conversations. The work product stays; the relationship resets.

What it doesn't capture:
- The temp has no judgment about sensitive situations
- The temp follows instructions literally
- The temp can't "notice" context you didn't provide

## Shaping AI Behaviour: Instruction Files

Most AI coding assistants allow you to provide **project-level context** through instruction files. These are markdown files in your project that the AI reads automatically, giving it context about:

- What your project does
- Coding conventions and preferences
- Important architecture decisions
- Common pitfalls to avoid

This is how you avoid re-explaining your project in every conversation.

**The concept is universal, but the implementation varies:**

| Tool | Instruction File Location |
|------|--------------------------|
| Claude Code | `CLAUDE.md` in project root |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Cursor | `.cursorrules` or `.cursor/rules/*.mdc` |
| Cross-tool convention | `AGENTS.md` in project root |

The content is similar across tools — you're telling the AI what it needs to know about your project. `AGENTS.md` has emerged as a vendor-neutral convention that many tools read; some teams maintain a single source file and copy/symlink it to the tool-specific locations.

**What to include:**
- Brief project description and purpose
- Key technologies and frameworks
- Coding style preferences
- Important file locations
- Things the AI should avoid doing

**What NOT to include:**
- Secrets or credentials
- Information that changes frequently
- Lengthy documentation (link to it instead)

> **Developer Track:** Module D1 covers instruction file design in detail, including cross-tool strategies and advanced patterns like file-type-specific rules.

```
EXERCISE:
Think about a project you work on regularly.

1. What would you want an AI to know before helping you with it?
2. What mistakes would you want to prevent?
3. Write 5-10 bullet points that would go in an instruction file.
```

## Key Takeaways

- Model, context, tools, and memory are **distinct components** — and an agent is those four running in a loop towards a goal
- The model itself is stateless — memory requires additional systems
- The context window is the model's entire world for that interaction
- Tools are how AI affects the real world — and a trust boundary; agents raise the stakes because they act before you've checked
- When things go wrong, diagnose by component
- "The AI should know..." is usually a context or memory issue
- **Instruction files** let you provide persistent project context across sessions

---

Next: **Module 5: Verification & Quality** →
