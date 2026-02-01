# Module 3: Understanding AI Systems

## The Four Components

To work effectively with AI, you need a mental model of what you're working with. Every AI system has four distinct components that are often conflated:

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │   PROMPT    │───▶│    AGENT    │───▶│   TOOLS     │     │
│  │             │    │   (model)   │    │             │     │
│  │ Your input  │    │ Interprets, │    │ What agent  │     │
│  │ + system    │    │ reasons,    │    │ can do in   │     │
│  │ context     │    │ decides     │    │ the world   │     │
│  └─────────────┘    └──────┬──────┘    └─────────────┘     │
│                            │                               │
│                            ▼                               │
│                    ┌─────────────┐                         │
│                    │ PERSISTENCE │                         │
│                    │  / MEMORY   │                         │
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

## Component 1: The Agent (Model)

**What it is:** The underlying AI model — its capabilities, training, reasoning patterns.

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
- Reasoning capability
- Context window size
- Speed / latency
- Cost
- Training data recency
- Specific domain knowledge
- Safety behaviours

```
QUIZ:
You had a great conversation with an AI yesterday where you explained your project in detail. Today you start a new conversation. What does the AI know about your project?

* Everything from yesterday
* A summary of yesterday
*! Nothing — unless you tell it again or there's explicit memory/persistence
* It depends on the model

FEEDBACK: By default, each conversation starts fresh. The model itself doesn't retain information. Any "memory" requires explicit persistence systems.
```

## Component 2: The Prompt (Input Context)

**What it is:** Everything the model receives as input — your message, system prompts, conversation history, any retrieved documents.

**Key properties:**
- There's a maximum size (context window) — typically 8K to 200K tokens
- Everything the model "knows" for this interaction is in the prompt
- Order and structure of the prompt affects output
- System prompts set behaviour; user prompts are your requests

**The prompt includes (typically):**
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

FEEDBACK: Without tools, the AI can only use its training data. It might answer (if the event is in training data) or acknowledge it doesn't know. Good AI systems are transparent about this.
```

## Component 4: Persistence / Memory

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

## Why Keeping These Separate Matters

When AI does something unexpected, diagnose by component:

| Symptom | Possible Cause | Component |
|---------|---------------|-----------|
| "It doesn't know about X" | Not in training data | Agent |
| "It doesn't know about X" | Not in current context | Prompt |
| "It can't do X" | Tool not available | Tools |
| "It forgot X" | Not persisted | Memory |
| "It's worse than yesterday" | Different model version | Agent |
| "It's ignoring my instructions" | Truncated from context | Prompt |

**Debugging framework:**
1. Is this an **agent** limitation? (Model capability, training)
2. Is this a **prompt** issue? (Missing context, poor structure)
3. Is this a **tool** issue? (Unavailable, failed, wrong permissions)
4. Is this a **persistence** issue? (Context lost, not retrieved)

## The "Amnesiac Temp" Mental Model

A helpful metaphor for AI agents:

> **"A very capable temp who starts fresh every day, works only with what you hand them, and shreds everything when they leave."**

This captures:
- Capability (not just a tool — can reason and adapt)
- Lack of persistence (fresh every day)
- Scoped access (only what you provide)
- No retention (shreds when done)

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

The content is similar across tools — you're telling the AI what it needs to know about your project. Some teams maintain a single source file and copy/symlink it to multiple locations for cross-tool compatibility.

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

- Agent, prompt, tools, and memory are **distinct components**
- The model itself is stateless — memory requires additional systems
- The context window is the model's entire world for that interaction
- Tools are how AI affects the real world — and a trust boundary
- When things go wrong, diagnose by component
- "The AI should know..." is usually a prompt or persistence issue
- **Instruction files** let you provide persistent project context across sessions

---

Next: **Module 4: Verification & Quality** →
