# Task: Interactive Glossary

> **Outcome (June 2026):** Implemented. Definitions live in a central `glossary.json` (16 terms covering the core concepts listed below plus weights, system prompt, agent, sycophancy, jagged frontier, RAG, fine-tuning, temperature, and LLM). The app auto-links the **first occurrence** of each term per page to a hover/tap tooltip — no markup is required in the content, so authoring stays clean and the feature degrades gracefully to plain text without JavaScript. Matching skips code, links, and headings; tooltips are keyboard-accessible (focusable, `aria-describedby`, Escape to dismiss) and tap-to-toggle on touch. Verified in Chrome (light + dark, hover/tap/keyboard). See `applyGlossary()` in `index.html`.

## Type
feature

## Description
Add an interactive glossary that shows definitions when users hover over marked terms/phrases.

## Requirements
- Terms are marked in markdown (possibly with a custom syntax like `==term==` or `[term]{.glossary}`)
- On hover (or tap on mobile), a tooltip shows the definition
- Definitions stored in a central glossary file
- Non-intrusive — shouldn't distract from reading

## Technical Considerations
- Could use CSS-only tooltips for simplicity
- Or lightweight JS for better positioning
- Glossary could be a JSON file or markdown with structured format
- Need to decide on markup syntax that's author-friendly

## Example Terms to Include
- **Hallucination** — When AI generates plausible-sounding but false information
- **Context window** — The amount of text an AI can consider at once
- **Prompt** — The input/instructions given to an AI
- **MCP** — Model Context Protocol, a standard for connecting AI to external tools
- **Non-deterministic** — Producing different outputs from the same input
- **Few-shot** — Providing examples in a prompt to guide AI behaviour

## Priority
Medium — nice to have, not blocking

## Notes
- Should work without JavaScript (graceful degradation)
- Consider accessibility (screen readers, keyboard navigation)
- Mobile-friendly (tap instead of hover)
