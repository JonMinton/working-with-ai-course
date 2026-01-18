# Review Notes (Additive Phase Handover)

## Snapshot of what’s covered so far

### Welcome
- Positions the course as collaboration skills for the agentic AI era.
- Sets three audiences (enterprise, developer, academic) and the shared core.
- Emphasises the "10% that matters": specification, verification, and architectural judgement.

### Core modules
1. **Structured Thinking for AI Collaboration**
   - The specification gap and why it exists.
   - Five components of clear specification: linearisation, context externalisation, abstraction level, acceptance criteria, scope boundaries.
   - Exercises and quizzes to practise translating intent into actionable prompts.

2. **Precision Without Formalism**
   - Why formal notation exists and how it can obscure clarity.
   - Multiple notations for the same precision: prose, pseudocode, tests, examples.
   - Precision levels matched to stakes.
   - Explicit definitions and structured writing for unambiguous requirements.
   - Added distinction between **text vs. binary** files as a core collaboration constraint.

3. **Understanding AI Systems**
   - Four components model: prompt, agent, tools, persistence.
   - Capabilities and limits by component; practical diagnostic framework.
   - Context window management and the "amnesiac temp" mental model.
   - Instruction files as a way to provide project-level context.

4. **Verification & Quality**
   - Verification mindset and error modes.
   - Verification strategies by output type: code, facts, structured data, prose.
   - Visual reasoning gap and the need for human visual checks.
   - Test‑driven specification and cross‑model review.
   - Checklists for code and content verification.

### Specialised tracks
- **Enterprise**
  - Trust architecture, approved channels, and governance patterns framed as organisational controls.
- **Developer**
  - Affordances and interface design, architectural reasoning, and MCP tool design.
- **Academic**
  - Literature workflows, modular academic writing, and AI peer review.

## One–two important potential gaps to address later

1. **Evaluation and monitoring as a lifecycle discipline**
   - There is strong guidance on *verification* at the point of output, but less on longer‑term evaluation (regression testing, benchmarking prompts, drift detection, and ongoing monitoring for tool‑using agents). A short section on *evaluation as a routine* could bridge the gap between one‑off verification and sustained reliability.

2. **Data handling and privacy risk models beyond the basics**
   - The enterprise content discusses trust and channels, but a dedicated, practical guide to *data classification* and *risk tiers* (what can go into prompts, what must stay out, redaction patterns, audit logging expectations) would help operationalise governance. This could be a short checklist or decision tree rather than a full policy.

## Suggested usage
- Treat this file as a review handover for the later edit phase.
- As new content is appended, update the “Snapshot” section with concise bullet points to keep the global picture clear.
