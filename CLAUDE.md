# Working With AI: A Practical Course

A self-contained learning platform for AI collaboration skills. Static HTML/JS frontend with markdown content.

## Tech Stack
- Single-page app: `index.html` (vanilla JS, no build step)
- Content: Markdown files rendered client-side via marked.js
- Styling: CSS custom properties, no framework; light/dark themes via `[data-theme]`
- Progress tracking: localStorage (keys: `wwai-completed`, `wwai-mytracks`, `wwai-open`, `wwai-theme`)
- App features: collapsible nav sections, per-track "my plan" progress, client-side full-text search (lazy-indexed), reading-time estimates, mobile drawer
- Test locally with `python3 -m http.server` (fetch() needs http, not file://)

## Core Module Structure (June 2026 revision)
Seven core modules in `/core/`:
1. `01-how-ai-works.md` — LLM mechanics for general audiences (weights vs context, hallucination, sycophancy, jagged frontier). Other modules cross-reference it.
2. `02-structured-thinking.md` 3. `03-precision.md` 4. `04-understanding-ai.md` (model/context/tools/memory; agent = model+tools+loop) 5. `05-verification.md` 6. `06-iteration.md` 7. `07-agentification.md`
When editing, keep cross-module references consistent with this numbering.

## File Structure
- `/index.html` — Main app, all JS/CSS inline
- `/welcome.md` — Landing page content
- `/core/` — Core modules (01-06), required for all learners
- `/tracks/` — Specialised tracks (enterprise, developer, academic, creative, operations, education, leadership)
- `/assets/` — Images and media (SVG diagrams and visual assets)

## Content Conventions
- British English spelling (behaviour, organisation, colour)
- Markdown files use ATX headings (`#`, `##`, etc.)
- Interactive elements use special code block syntax:
  - `QUIZ:` blocks for multiple choice — first line(s) after `QUIZ:` are the question, options start `* ` (wrong) or `*! ` (exactly one, correct), then `FEEDBACK:` which may span multiple lines to the end of the block. Inline markdown is allowed in questions/options.
  - `EXERCISE:` blocks for practical activities (body rendered as markdown)
- Factual integrity: never add statistics, case studies, or quotes that can't be traced to public reporting; frame company figures as "reported". Prefer evergreen phrasing over dates that will go stale.
- Tables for comparisons; keep them scannable
- Cross-references between modules use relative paths

**Nested code fences:** When an EXERCISE or QUIZ block needs to contain code examples, use tildes (`~~~`) for the outer block to avoid parsing conflicts:
~~~
~~~
EXERCISE:
Here is some code:

```python
def example():
    pass
```
~~~
~~~

## Planned Development
- Backend: Supabase (auth, progress tracking, feedback)
- User feedback: per-page ratings and comments
- Target audience: non-technical users (no GitHub account required)

## Multi-Model Workflow

This project uses multiple AI models. See `tasks/README.md` for the handover protocol.

**Task folders:**
- `/tasks/pending/` — Tasks ready to be picked up
- `/tasks/in-progress/` — Tasks being worked on
- `/tasks/completed/` — Finished tasks

**Model assignments:**
- Diagram generation → Gemini (visual strength)
- Visual review/verification → Gemini
- Complex refactoring, documentation → Claude
- Quick code generation → GPT-4o or Gemini Flash

**Diagrams:** ASCII diagrams in markdown are the source of truth. SVG versions in `/assets/diagrams/` are for progressive enhancement in the web view.

**Future consideration: Mermaid diagrams**
The peer-review-cycle SVG was reverted to ASCII because the SVG didn't accurately capture the paper-centric flow of the original. Mermaid could be a better approach for diagrams:
- Text-based, version-controllable, diffable
- Any model can edit (no visual generation needed)
- Add mermaid.js to index.html for client-side rendering
- Would replace both ASCII source and separate SVG files
Evaluate when ready for editorial phase in Claude Code.

## Git Workflow

**Repository:** `github.com/JonMinton/working-with-ai-course`

### Phase 1: Content Creation (single branch)
During active content creation, all models work on `main`:
- Commit with model identifier prefix: `[claude]`, `[gemini]`, `[gpt-4o]`
- Example: `[claude] Add instruction files section to Core Module 3`
- Pull latest before starting work
- Commit frequently to avoid conflicts

### Phase 2: Editorial Review (PR workflow)
When content needs review before merging:
- Create feature branch: `content/module-name` or `fix/description`
- Open PR to `main`
- Designated reviewer model comments on the PR
- Human makes final merge decision

### Commit Message Format
```
[model] Brief description of change

Optional longer explanation if needed.

Co-Authored-By: Claude <noreply@anthropic.com>
```

Replace `Claude` with `Gemini` or `GPT-4o` as appropriate.

## Important Notes
- This is educational content — accuracy and clarity matter
- Keep examples concrete and actionable
- Core modules should be accessible to all audiences
- Developer track can assume technical background
- Don't add features beyond what's explicitly requested
