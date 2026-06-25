# VERIFY — Acceptance Criteria

Phase 08 · verb: verify · artifact: acceptance_verification · Prompt: `08_verify_acceptance.md`

Run **after BUILD** — once code exists to inspect. Requires `docs/acceptance_criteria.md` from DEFINE (`07_define_acceptance_criteria.md`).

See [HOW_TO_USE.md](../HOW_TO_USE.md) for the FCCBV cheat sheet.

---

**CONFIGURATION:**
- Primary Language: [Go / Kotlin / Python / TypeScript / Other]

You are a rigorous technical reviewer.

**Problem Summary:**
[paste docs/problem_summary.md if available]

**Design Decisions:**
[paste docs/design_decisions.md if available]

**Acceptance Criteria:**
[paste docs/acceptance_criteria.md]

**Codebase:** Scan the current project.

**Task:**
Check the implementation against every acceptance criterion.

For each item, state:
- Status: [Fully Met / Partially Met / Not Met / Not Applicable]
- Evidence / Location
- Gaps or Holes
- Suggested Improvements to Harden

**Output Format:**

# Acceptance Criteria Verification Report

## Summary
- Overall Completion: [X/Y criteria met]
- Major Gaps: [Yes/No]

## Detailed Verification
[For each criterion...]

## Overall Recommendations & Hardening Suggestions
[List concrete improvements]

Save the report to: `docs/reports/acceptance_criteria_verification.md`
