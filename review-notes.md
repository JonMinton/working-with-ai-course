# Review Notes (Editorial Rewrite Handover — June 2026)

This file records the state of the course after the major editorial revision on branch `claude/editorial-rewrite`. Treat it as the handover for the next editing phase.

## What changed in this revision

### New core Module 1: How AI Actually Works
The biggest content gap was that the course taught *working with* AI without ever explaining *what an LLM is*. The new `core/01-how-ai-works.md` covers: next-token prediction, weights vs. context (the load-bearing distinction), hallucination as structural, tokenisation failures, probabilistic output, sycophancy, confabulated self-explanations, and the jagged frontier. All other core modules were renumbered (old 1–6 → new 2–7) and now cross-reference Module 1.

### Core module fixes
- **Module 4 (was 3):** fixed the agent/model conflation — components are now Model / Context / Tools / Memory, with a new section defining an *agent* as model + tools + loop. Context window claims updated; `AGENTS.md` convention added.
- **Module 5 (was 4):** un-spliced the factual-content/data-handling checklists (a botched earlier merge); modernised the visual reasoning gap (agentic tools can now screenshot their own output; final judgment stays human).
- **Module 7 (was 6):** rebuilt the garbled five-rings ASCII diagram; replaced hard year-ranges with ordering language and an honest note about forecast shelf-life; removed invented per-ring population counts; replaced a fabricated Hinton quote with an accurate paraphrase; fixed the track list (it described tracks that don't exist).

### Factual integrity pass (all tracks + case studies)
- Removed the unverifiable "Harvard APEX+" case study everywhere.
- Softened unverifiable precision (adoption percentages, cost figures, dated roadmaps) to "publicly reported" or illustrative framing across E4, L4, O4, C4, Ed4, and case-studies.md.
- `case-studies.md` rewritten with a verification-minded preamble; it now models the course's own standards.
- C4 legal landscape rewritten evergreen (no case names, no year-stamped section titles).

### App (`index.html`) rewrite
Collapsible nav, per-track "my plan" progress, dark mode, lazy full-text search, robust quiz parser (feedback lives in JS — quotes and multi-line feedback are now safe), reading time, mobile drawer. localStorage key `wwai-completed` kept compatible with the old app.

## Known gaps / next-phase candidates
- `resources.md` links were left as-is; a link-checking pass (do they still resolve in 2026?) would be worthwhile.
- SVG diagrams: `four-components.svg` is stale (shows old PROMPT/AGENT labels) and is no longer swapped in; either regenerate to match Model/Context/Tools/Memory or delete. The Mermaid idea in CLAUDE.md remains open.
- Tracks were *fixed*, not rewritten — a deeper editorial pass per track (especially redundancy between E2/E4 and E3/L3) is the next level of polish.
- Supabase backend (auth, feedback) still planned, not started.
- The `tasks/pending/` folder still holds proposals (interactive glossary, additional tracks) untouched by this revision.

## Verification protocol used (worth repeating)
1. Three parallel review agents (one per track cluster) reporting factual/format/quality issues with line numbers.
2. Targeted fixes by parallel edit agents under a "never invent facts; soften instead" rule.
3. Automated QUIZ/EXERCISE format validation across all md files.
4. Rendered-site checks in Chrome: nav, quiz interaction (right and wrong paths), search, dark mode, plan toggles, mark-complete flow, diagram alignment.
