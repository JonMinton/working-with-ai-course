# Task: Peer Review Cycle Diagram

## Type
diagram

## Assigned To
gemini

## Source
File: `tracks/academic/03-peer-review.md`

ASCII source:
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  ┌─────────────────┐             ┌─────────────────┐       │
│  │   AI Reviewer   │◀──┐       ┌──▶│ Human Reviewer  │       │
│  │(Claude, Gemini) │   │       │   │(You)            │       │
│  └─────────────────┘   │       │   └─────────────────┘       │
│                        │       │                             │
│                        │ Paper │                             │
│                        │       │                             │
│  ┌─────────────────┐   │       │   ┌─────────────────┐       │
│  │  AI Adversary   │───┘       └───│   AI Assistant  │       │
│  │(Finds flaws)    │               │(Helps you fix)  │       │
│  └─────────────────┘               └─────────────────┘       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Request
Create a clean SVG diagram that:
1.  Represents the four roles in the peer review cycle.
2.  Shows the cyclical flow of the paper between the roles.
3.  Includes the brief descriptions for each role.
4.  Uses a modern, minimal style consistent with previous diagrams.

## Output
`assets/diagrams/peer-review-cycle.svg`

## Constraints
- **Colours** (from course CSS):
  - Background: `#ffffff`
  - Box borders: `#e7e5e4`
  - Text: `#1c1917`, `#57534e`
