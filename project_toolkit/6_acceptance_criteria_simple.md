# 6 — Design Output: Acceptance Criteria

Ordered workflow step 6 (post-solution shape). Prompt file: `6_acceptance_criteria_simple.md`

See [HOW_TO_USE.md](../HOW_TO_USE.md) for the full workflow guide.

Run this **after** Core Architecture and key design decisions are Human Reviewed — once you
know enough about the solution to write testable criteria.

---

You are a senior technical architect.

**Full Context:**
- Problem Summary: docs/problem_summary.md
- Design Decisions: docs/design_decisions.md

Create `docs/acceptance_criteria.md` with testable criteria derived from the requirements
and recorded decisions. Do not invent new scope — trace every criterion back to problem_summary.

**Format for each criterion:**

### AC-1: [Short title]

**Given** [precondition]
**When** [action or event]
**Then** [expected outcome]

**Traces to:** FR-1, NFR-2
**Verified by:** [unit test / integration test / manual check]

---

**Rules:**

1. Assign stable IDs: `AC-1`, `AC-2`, …
2. Every AC must include **Traces to:** with at least one `FR-*` or `NFR-*` ID.
3. Cover all `SC-*` success criteria from problem_summary.
4. Prioritize criteria for requirements still `Pending` or `Partial` in the Traceability Matrix.
5. Keep criteria testable — avoid vague language ("should be fast" → cite NFR with measurable threshold if defined).
6. Mark `[DEFERRED]` criteria for out-of-phase scope with reference to `OOS-*` if applicable.

**Output:** Create or update `docs/acceptance_criteria.md`.
