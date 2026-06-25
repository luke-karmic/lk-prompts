# DIAGRAM — Architecture

Phase 05 · verb: diagram · artifact: architecture · Prompt: `05_diagram_architecture.md`

See [HOW_TO_USE.md](../HOW_TO_USE.md) for the full workflow guide.

---

You are an expert software architect.

**Current Context:**
- Problem Summary: docs/problem_summary.md
- Design Decisions: docs/design_decisions.md (including Approach Fit Analysis and Solution Overview)

Generate the following:

1. A clear Mermaid flowchart describing the core business logic and flow.
   - Annotate key nodes with relevant requirement IDs where helpful (e.g. `FR-3`, `NFR-2`).
   - Reflect the chosen approach from the Approach Fit Analysis — do not introduce alternatives that were rejected.

2. A brief evaluation of the recorded solution approach, citing `PRI-*` from problem_summary
   and confirming alignment with the Approach Fit Analysis summary in design_decisions.

3. Any useful suggestions or refinements for docs/design_decisions.md
   (clearly mark them as "LLM Suggestion - Pending Review").

Focus on clarity and practicality. Do not generate implementation code yet.
