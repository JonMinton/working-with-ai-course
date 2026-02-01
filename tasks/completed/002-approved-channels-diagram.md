# Task: Approved Channels Diagram

## Type
diagram

## Assigned To
gemini

## Source
File: `tracks/enterprise/02-approved-channels.md`

ASCII source:
```
┌─────────────────────────────────────────────────────────────┐
│                     THE SAME MODEL...                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────────┐     ┌─────────────────────┐       │
│  │   APPROVED CHANNEL  │     │  UNAPPROVED CHANNEL │       │
│  │                     │     │                     │       │
│  │ • Enterprise        │     │ • Personal web      │       │
│  │   agreement         │     │   interface         │       │
│  │ • Data doesn't      │     │ • May train on      │       │
│  │   train model       │     │   your inputs       │       │
│  │ • Audit logging     │     │ • No audit          │       │
│  │ • SSO/identity      │     │ • Personal          │       │
│  │ • IT/compliance     │     │   account           │       │
│  │   approved          │     │ • Shadow IT         │       │
│  │                     │     │                     │       │
│  │ e.g., Copilot,      │     │ e.g., claude.ai     │       │
│  │ Azure OpenAI,       │     │ personal login,     │       │
│  │ enterprise API      │     │ ChatGPT free tier   │       │
│  └─────────────────────┘     └─────────────────────┘       │
│                                                             │
│          Same underlying model capability                   │
│          Completely different risk profile                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Request
Create a clean SVG diagram that:
1.  Represents the two types of channels (Approved vs. Unapproved) under a single model.
2.  Includes the list of attributes for each channel.
3.  Uses a modern, minimal style consistent with the previous diagram.
4.  Uses green/success for approved items and yellow/warning for unapproved items.

## Output
`assets/diagrams/approved-channels.svg`

## Constraints
- **Colours** (from course CSS):
  - Background: `#ffffff`
  - Box borders: `#e7e5e4`
  - Success: `#16a34a`
  - Warning: `#ca8a04`
