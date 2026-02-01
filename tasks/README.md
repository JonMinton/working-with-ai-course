# Multi-Model Task Handover

This folder manages tasks that are handed off between AI models (e.g., Claude → Gemini → Claude).

## Folder Structure

```
tasks/
├── pending/       # Tasks ready to be picked up
├── in-progress/   # Tasks currently being worked on
├── completed/     # Finished tasks (for reference)
└── README.md      # This file
```

## Task File Format

Each task is a markdown file named: `NNN-short-description.md`

```markdown
# Task: [Brief Title]

## Type
[diagram | review | visual-check | other]

## Assigned To
[claude | gemini | human | any]

## Source
[File path and line numbers, or description of source material]

## Request
[Clear description of what needs to be done]

## Output
[Expected output location, e.g., assets/diagrams/filename.svg]

## Constraints
- [Style requirements]
- [Technical constraints]
- [Quality criteria]

## Status
- [ ] Created
- [ ] In progress
- [ ] Completed
- [ ] Reviewed
- [ ] Integrated

## Notes
[Model/human writes notes here during and after work]
```

## Workflow

1. **Creating model** writes task file to `pending/`
2. **Assigned model** moves file to `in-progress/`, does the work
3. **Assigned model** updates status, moves to `completed/`
4. **Reviewing model** (or human) checks work, adds review notes
5. **Integrating model** incorporates result into main project

## Model Strengths (Guidance)

| Task Type | Recommended Model | Why |
|-----------|-------------------|-----|
| Diagram generation | Gemini | Strong visual understanding, can generate SVG |
| Visual review | Gemini | Can "see" rendered output |
| Complex refactoring | Claude | Long context, careful reasoning |
| Documentation | Claude | Writing quality |
| Quick code gen | GPT-4o / Gemini Flash | Speed |

## Colour Scheme Reference

From `index.html` CSS variables:
- Primary background: `#fafaf9`
- Secondary background: `#ffffff`
- Primary text: `#1c1917`
- Secondary text: `#57534e`
- Accent (links, buttons): `#2563eb`
- Success (completed): `#16a34a`
- Border: `#e7e5e4`
