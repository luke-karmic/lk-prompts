# ANALYZE — Gap Analysis

Phase 06 · verb: analyze · artifact: gaps · Prompt: `06_analyze_gaps.md`

See [HOW_TO_USE.md](../HOW_TO_USE.md) for the full workflow guide.

---

You are a senior technical reviewer with strong experience in reliable systems and fintech.

**Full Context:**
- Problem Summary: docs/problem_summary.md
- Solution Options: docs/solution_options.md (if present)
- Design Decisions: docs/design_decisions.md

Perform a thorough gap analysis. Cross-reference:

- Every `FR-*` / `NFR-*` / `SC-*` still `Pending` or `Partial` in the Requirement Traceability Matrix
- Considerations Coverage rows from problem_summary with **Low** confidence or **No**
- Open `Q-*` items not yet resolved by a recorded decision
- Approach Fit Analysis — concerns rated Weak or Adequate for the chosen approach

Focus especially on:

- Data integrity and correctness
- Security & compliance considerations
- Error handling and observability
- Scalability and concurrency (if relevant)
- Auditability / traceability
- Any domain-specific risks (e.g., financial, accounting)
- Failure cases, missed unhappy paths

For each gap, cite the relevant requirement ID (`FR-*`, `NFR-*`) or consideration name.

Provide prioritized recommendations and suggest any additions or changes to docs/design_decisions.md.
Be pragmatic — focus on what actually matters for this problem.
