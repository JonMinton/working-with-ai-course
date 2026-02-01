# Working With AI: A Practical Course

A self-contained learning platform for AI collaboration skills. Static HTML/JS frontend with markdown content.

## Tech Stack
- Single-page app: `index.html` (vanilla JS, no build step)
- Content: Markdown files rendered client-side via marked.js
- Styling: CSS custom properties, no framework
- Progress tracking: localStorage (currently client-only)

## File Structure
- `/index.html` — Main app, all JS/CSS inline
- `/welcome.md` — Landing page content
- `/core/` — Core modules (01-04), required for all learners
- `/tracks/` — Specialised tracks (enterprise, developer, academic, creative, operations)
- `/assets/` — Images and media (currently empty)

## Content Conventions
- British English spelling (behaviour, organisation, colour)
- Markdown files use ATX headings (`#`, `##`, etc.)
- Interactive elements use special code block syntax:
  - `QUIZ:` blocks for multiple choice
  - `EXERCISE:` blocks for practical activities
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

## Content Expansion Protocol

**Goal:** Add new material without deleting or rewriting existing content. Editing and consolidation happen later in a dedicated review phase.

**Additive phase (models only):**
- Only append to existing `.md` files (no deletions or rewrites)
- Use ATX headings and British English spelling
- Add new content under clear subheadings (e.g., `## Additional examples`, `## Common pitfalls`)
- Prefer scannable formats (short paragraphs, bullets, tables)
- Keep examples concrete and actionable
- Keep cross-references relative and accurate

**Edit/peer review phase (human + models):**
- Consolidate overlaps and remove duplication
- Tighten structure, tone, and terminology
- Verify claims and accuracy
- Ensure accessibility for non-technical readers

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
