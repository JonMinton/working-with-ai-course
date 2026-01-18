# D1. Affordances & Interfaces

## The Affordance Concept

An **affordance** is what an interface makes easy, hard, or impossible.

The same underlying capability can have radically different usability depending on how it's presented:

| Interface | Affordance |
|-----------|-----------|
| CLI with flags | Power users, scriptable, steep learning curve |
| REST API | Programmable, stateless, requires code |
| Chat interface | Conversational, flexible, harder to automate |
| GUI with buttons | Discoverable, constrained, less flexible |

Understanding affordances helps you:
- Design better interfaces for humans
- Design better interfaces for AI
- Recognise when the interface is the problem

## Same Capability, Different Interfaces

Consider a database search function:

**As CLI:**
```bash
search --query "term" --limit 10 --sort relevance
```

**As REST API:**
```
GET /search?q=term&limit=10&sort=relevance
```

**As chat:**
> "Find me the 10 most relevant items matching 'term'"

**As GUI:**
> [Search box] [Dropdown: Sort by] [Slider: Results]

Each affords different things:
- CLI: precise, scriptable, requires knowledge of flags
- API: programmable, stateless, requires code to use
- Chat: natural, flexible, harder to constrain
- GUI: discoverable, guided, limited by design

```
QUIZ:
You need to expose a data export function. Users will run it monthly with the same parameters. Which interface affords this best?

* Chat interface — users can just ask for what they want
* GUI with a "Run Export" button
*! CLI or API — can be scripted and scheduled
* Email-based — users email a request
FEEDBACK:Repeated, predictable tasks are best served by scriptable interfaces (CLI/API) that can be automated.
```

## Human-Centred Affordances

When designing for humans, consider:

### Discoverability
Can users find features? GUIs afford discoverability (menus, buttons). CLIs hide features behind documentation.

### Error Prevention
Does the interface prevent mistakes? Dropdowns afford constrained choices. Free text affords flexibility but also errors.

### Efficiency
For repeated tasks, what's fastest? Keyboard shortcuts afford speed for experts. Wizards afford guidance for novices.

### Feedback
Does the user know what happened? Progress bars afford patience. Silent completion affords anxiety.

## AI-Centred Affordances

When AI is the "user" of an interface (MCP tools, function calling), different affordances matter:

| Design Choice | Human Preference | AI Preference |
|---------------|-----------------|---------------|
| **Parameter naming** | Short, memorable (`-n`) | Descriptive, unambiguous (`max_results`) |
| **Defaults** | Sensible for common case | Explicit "no default" may be clearer |
| **Error messages** | Friendly, suggestive | Structured, parseable, actionable |
| **Input format** | Flexible, forgiving | Strict, predictable schema |
| **Documentation** | Narrative, examples | Structured descriptions, type signatures |
| **Granularity** | Coarse (fewer clicks) | Fine (composable primitives) |

### AI Needs Explicit Schemas

Humans can infer from examples. AI works better with explicit schemas:

**Human-friendly documentation:**
> "Pass the user's name and optionally their age"

**AI-friendly schema:**
```json
{
  "name": { "type": "string", "required": true, "description": "User's full name" },
  "age": { "type": "integer", "required": false, "description": "User's age in years" }
}
```

### AI Benefits from Constrained Outputs

When AI calls a tool, structured responses are easier to process:

**Hard for AI to parse:**
> "Found 3 results: The first one is about cats, the second about dogs..."

**Easy for AI to parse:**
```json
{
  "count": 3,
  "results": [
    {"id": 1, "topic": "cats"},
    {"id": 2, "topic": "dogs"},
    {"id": 3, "topic": "birds"}
  ]
}
```

```
EXERCISE:
Design a tool for AI to use that searches a knowledge base.

1. What parameters does it need?
2. What should the response format be?
3. How should errors be communicated?
4. What would make this tool easy for AI to use correctly?
```

## The Visual Reasoning Gap

AI has specific limitations with visual content:

**AI struggles with:**
- Spatial relationships ("Is A above or below B?")
- Visual debugging ("Why does this CSS render wrong?")
- Proportions and aesthetics ("Does this look balanced?")
- Complex visualisations (dense charts, overlapping elements)
- Physical/spatial metaphors

**Implications for interface design:**

When humans verify AI visual output:
- AI generates code (CSS, SVG, etc.)
- Code renders to visual output
- Human must verify (AI cannot do this step)
- Human provides textual feedback for iteration

When AI processes visual input:
- Screenshots help but aren't perfectly understood
- Textual descriptions of visual state are clearer
- Explicit coordinates/dimensions are clearest

## Translating Visual Intent to Text

A key skill: describing visual goals precisely enough for AI to implement.

**Vague:**
> "Make it look nice"

**Better:**
> "Align the form fields vertically, add 16px spacing between them, and use a subtle gray border"

**Best:**
> "Form layout:
> - All labels left-aligned, fields stretch to container width
> - 16px vertical gap between field groups
> - 1px solid #e0e0e0 border around the form
> - 24px padding inside the border
> - Submit button right-aligned at bottom"

The more explicit your visual specification, the better AI can implement it.

```
EXERCISE:
You want a dashboard with:
- A header with the app name
- Three metric cards in a row
- A chart below taking full width
- A footer

Write a specification detailed enough for AI to implement without visual ambiguity.
```

## Designing Hybrid Interfaces

Many systems need to serve both humans AND AI:

### Pattern: API + GUI

- API for AI/automation
- GUI for human exploration
- Shared underlying capability

### Pattern: Structured + Natural Language

- Accept both formal queries and natural language
- Parse natural language into structured form
- Return structured data with natural language summary

### Pattern: AI-Assisted GUI

- GUI for human interaction
- AI helps fill forms, suggest options
- Human retains control of final actions

## Configuring AI Assistants: Instruction Files

One of the most important affordances you can provide to AI coding assistants is **project context**. This is done through instruction files — markdown documents that the AI reads automatically when working in your project.

### Why This Matters

Without instruction files, every conversation starts from zero. The AI doesn't know:
- What your project does
- Your coding conventions
- Your tech stack preferences
- What mistakes to avoid

With instruction files, the AI has this context immediately. This is a form of **persistence** (see Core Module 3) that you control.

### Cross-Tool Comparison

Different AI tools use different file locations and formats:

| Tool | Primary Location | Additional Options | Format |
|------|-----------------|-------------------|--------|
| **Claude Code** | `CLAUDE.md` (root) | `CLAUDE.md` in subdirectories | Markdown |
| **GitHub Copilot** | `.github/copilot-instructions.md` | `.github/instructions/*.instructions.md` | Markdown |
| **Cursor** | `.cursorrules` (legacy) | `.cursor/rules/*.mdc` | Markdown/MDC |

**Key differences:**

- **Claude Code** supports nested files — a `CLAUDE.md` in a subdirectory adds context for that part of the codebase
- **GitHub Copilot** supports `applyTo` frontmatter for file-type targeting (e.g., `applyTo: **/*.py`)
- **Cursor** is transitioning from `.cursorrules` to `.mdc` files with metadata

### Writing Effective Instruction Files

**Structure for maximum clarity:**

```markdown
# Project Name

Brief description (1-2 sentences).

## Tech Stack
- Framework: Next.js 14
- Language: TypeScript (strict mode)
- Database: PostgreSQL via Prisma

## Conventions
- Use functional components, not classes
- Prefer named exports over default exports
- Error handling: use Result types, not exceptions

## File Structure
- `/src/components/` — React components
- `/src/lib/` — Shared utilities
- `/src/app/` — Next.js app router pages

## Important Notes
- Never modify files in `/src/generated/` — these are auto-generated
- All API routes require authentication middleware
- Use the `logger` utility, not console.log
```

**Principles:**

| Principle | Why It Matters |
|-----------|---------------|
| **Be specific** | "Use camelCase" is actionable; "write clean code" is not |
| **Be concise** | AI context windows are limited; don't waste tokens |
| **Prioritise** | Put the most important things first |
| **Update regularly** | Stale instructions cause confusion |
| **Version control** | Instruction files should be in git |

### Cross-Tool Compatibility Strategy

If you use multiple AI tools, you have several options:

**Option 1: Single source, multiple copies**
```
project/
├── AI_CONTEXT.md              # Source of truth
├── CLAUDE.md                  # Copy or symlink
├── .github/
│   └── copilot-instructions.md  # Copy or symlink
└── .cursorrules               # Copy or symlink
```

**Option 2: Build script**
```bash
# copy-ai-context.sh
cp AI_CONTEXT.md CLAUDE.md
cp AI_CONTEXT.md .github/copilot-instructions.md
cp AI_CONTEXT.md .cursorrules
```

**Option 3: Symlinks** (Unix/Mac)
```bash
ln -s AI_CONTEXT.md CLAUDE.md
ln -s AI_CONTEXT.md .cursorrules
mkdir -p .github && ln -s ../AI_CONTEXT.md .github/copilot-instructions.md
```

### Advanced Patterns

**File-type specific rules (GitHub Copilot):**

Create `.github/instructions/python.instructions.md`:
```markdown
---
applyTo: "**/*.py"
---
- Use type hints for all function parameters and returns
- Prefer pathlib over os.path
- Use pytest for testing
```

**Context-aware rules (Cursor .mdc):**

Create `.cursor/rules/api-routes.mdc`:
```markdown
---
description: "Rules for API route handlers"
---
- All routes must validate input with zod schemas
- Return consistent error format: { error: string, code: number }
- Log all requests with request ID
```

**Nested context (Claude Code):**

```
project/
├── CLAUDE.md                 # Project-wide context
├── frontend/
│   └── CLAUDE.md             # Frontend-specific additions
└── backend/
    └── CLAUDE.md             # Backend-specific additions
```

### What NOT to Put in Instruction Files

| Don't Include | Why |
|--------------|-----|
| Secrets/credentials | Security risk — these files are version-controlled |
| Frequently changing info | Creates maintenance burden, causes confusion |
| Entire documentation | Link to it instead; don't bloat the context |
| Obvious things | "Write working code" wastes tokens |
| Tool-specific syntax | Keep content portable across tools |

```
EXERCISE:
Create an instruction file strategy for a project with:
- A Python backend (FastAPI)
- A TypeScript frontend (React)
- Shared API types
- Multiple developers using different AI tools (Claude, Copilot, Cursor)

1. What goes in the root instruction file?
2. What goes in subdirectory-specific files?
3. How do you keep them in sync across tools?
4. What file-type-specific rules would help?
```

### The Instruction File as Affordance

Notice that instruction files are themselves an affordance:

- They make it **easy** for AI to understand your project
- They make it **hard** for AI to violate your conventions (if well-written)
- They make it **possible** to have persistent project context without re-explaining

This is exactly what affordances do — shape what's easy, hard, and possible.

## Key Takeaways

- Affordances determine what interfaces make easy/hard/impossible
- Same capability can have radically different interfaces
- Human-centred affordances: discoverability, error prevention, feedback
- AI-centred affordances: explicit schemas, structured responses, clear errors
- AI cannot reliably verify visual output — humans must check
- Translating visual intent to text is a key skill
- Hybrid interfaces serve both humans and AI
- **Instruction files are an affordance** — they shape AI behaviour by providing context
- Different AI tools use different file locations, but the content is portable
- Keep instruction files concise, specific, and version-controlled

---

Next: **D2. Architecture Patterns** →
