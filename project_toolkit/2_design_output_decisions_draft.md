# 2 — Design Output: Decisions Bootstrap (Formal Mode)

Ordered workflow step 2 — **formal mode only**. Prompt file: `2_design_output_decisions_draft.md`

**Default path:** use [`2_design_output_solution_options.md`](2_design_output_solution_options.md) instead.
That prompt writes `docs/solution_options.md` with the Requirements Fit Matrix and option assessments.

Use this file only when you want a **single bulk draft** of `docs/design_decisions.md` including
Recorded Decisions stubs — typically for interview formal mode.

See [HOW_TO_USE.md](../HOW_TO_USE.md).

---

You are a senior software architect.

**Full Problem Context:**
[PASTE ENTIRE docs/problem_summary.md CONTENT]

**Prefer the standard Step 2 flow:** Run `2_design_output_solution_options.md` first, then Step 2.5 after choosing.

If continuing with formal bootstrap, create `docs/design_decisions.md` with this structure:

---

# Design Decisions

**Requirement IDs referenced:** [list all FR-*, NFR-*, SC-*, PRI-* from problem_summary]

## Solution Overview

_[Placeholder — fill at Step 2.5 once approach is chosen]_

## Approach Fit Analysis — Core Architecture

Same structure as `docs/solution_options.md` §2 Requirements Fit Matrix.
Copy from solution_options.md if that step was run first.

| Concern | [Option A] | [Option B] | [Option C if any] |
|---------|------------|------------|-------------------|
| FR-1: … | Fit · Confidence — why | … | … |

**Summary:** Draft recommendation — **Status: Exploring**

## Requirement Traceability Matrix

Initialize all SC/FR/NFR as `Pending`.

## Decisions To Be Made

1. Core Architecture / Approach
2. Technology Choices
3. Data Models & Types
4. Data Integrity & Validation Strategy
5. Error Handling & Logging
6. AI/LLM Usage & Guardrails (if relevant)
7. Testing Strategy
8. Security & Compliance Considerations

## Recorded Decisions

Draft format only — all `Status: Draft`. See `3_design_refine_single_decision.md`.

---

**Rules:** Do not mark anything Human Reviewed. Cite requirement IDs. After human chooses, run Step 2.5.
