# SHARPEN — Single Decision

Phase 04 · verb: sharpen · artifact: single_decision · Prompt: `04_sharpen_single_decision.md`

See [HOW_TO_USE.md](../HOW_TO_USE.md). After choosing an approach, run COMMIT (`03_commit_solution_coverage.md`) before this prompt unless Coverage Map already exists.

---

You are a senior engineer collaborator.

**Current files for context:**
- docs/problem_summary.md
- docs/solution_options.md
- docs/design_decisions.md

**Decision Topic to Refine:** [e.g. "Core Architecture / Approach" or "Data Integrity & Validation Strategy"]

Analyze this topic thoroughly. Respect optimization priorities (`PRI-*`) from docs/problem_summary.md.
Cite requirement IDs (`FR-*`, `NFR-*`, `SC-*`) — do not restate full requirement prose.

Return the **complete updated version of the entire docs/design_decisions.md file** with this specific decision properly recorded.

---

**For Core Architecture / Approach:**

1. Return the complete **Approach Fit Analysis** table (update ratings if options changed).
2. Write a **Summary** citing `PRI-*` as tie-breaker.
3. If status is `Human Reviewed`, also update **Solution Overview** from that summary.
4. A decision is incomplete if any concern rated **Required** for the chosen approach lacks a matching row.

**For other major decisions** (Technology Choices, Security, etc.) when 2+ viable options exist:

Include a smaller inline fit sub-table (3–5 rows) under **Approach Fit Analysis** in the decision block.

---

**Recorded Decision format:**

### [Exact Decision Topic]

**Decision:** [Clear final choice]
**Addresses:** FR-1, NFR-2, …
**Aligned priorities:** PRI-1, …
**Resolves questions:** Q-2 (if applicable, else "—")
**Approach Fit Analysis:** [Link to main section, or inline sub-table]
**Rationale:** [Strong justification citing PRI-* and requirement IDs; must align with Fit Analysis]
**Alternatives Considered:** [2–3 options with brief pros/cons]
**Trade-offs:** [Honest assessment; flag any conflict with OOS-* or ASM-* explicitly]
**Status:** Human Reviewed

---

**After updating the decision:**

- Refresh the **Requirement Traceability Matrix** for every ID touched by this decision.
- Set matrix Status to `Partial` or `Addressed` as appropriate.

Only update this one decision (and linked sections: Fit Analysis, Solution Overview, Traceability Matrix as applicable). Keep all other recorded decisions exactly as they are unless matrix rows need updating.
