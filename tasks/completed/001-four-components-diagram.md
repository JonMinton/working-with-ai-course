# Task: Four Components Diagram

## Type
diagram

## Assigned To
gemini

## Source
File: `core/03-understanding-ai.md` (lines 7-28)

ASCII source:
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

## Request
Create a clean SVG diagram that:
1. Represents the same four components (Prompt, Agent, Tools, Persistence/Memory)
2. Shows the flow: Prompt → Agent → Tools, with Agent also connecting down to Persistence
3. Includes the brief descriptions from each box
4. Uses a modern, minimal style

## Output
`assets/diagrams/four-components.svg`

## Constraints
- **Colours** (from course CSS):
  - Background: `#ffffff`
  - Box borders: `#e7e5e4`
  - Primary text: `#1c1917`
  - Secondary text (descriptions): `#57534e`
  - Accent (arrows, highlights): `#2563eb`
- **Typography:** Sans-serif, clean and readable
- **Size:** ~600px wide, scalable
- **Accessibility:** Text should be actual text (not paths) for screen readers
- **Style:** Flat design, subtle shadows or none, rounded corners on boxes

## Status
- [x] Created
- [ ] In progress
- [ ] Completed
- [ ] Reviewed
- [ ] Integrated

## Notes
This is the key conceptual diagram for Module 3. It should be immediately clear at a glance.

Created by Claude. Ready for Gemini to pick up.
