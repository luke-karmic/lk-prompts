# COMMIT — Solution Coverage Map

Phase 03 · verb: commit · artifact: solution_coverage · Prompt: `03_commit_solution_coverage.md`

Run **after you have chosen an approach** from COMPARE (`docs/solution_options.md`).
Run **before** SHARPEN, BUILD, or formal review prompts.

See [HOW_TO_USE.md](../HOW_TO_USE.md) for Conversation mode and the worked example.

---

You are a senior technical architect.

**Context:**
- docs/problem_summary.md (requirement IDs: PRI-*, SC-*, FR-*, NFR-*, etc.)
- docs/solution_options.md (Requirements Fit Matrix and option assessments from COMPARE)
- Chosen approach (below)

**Chosen approach:**
[PASTE: name + 2–3 sentence description — must match one option from solution_options.md]

**Optional — justification in your words:**
[PASTE HERE OR DELETE]

---

Create or update `docs/design_decisions.md` with these sections (preserve other sections if the file already exists):

## What We're Building

2–4 sentences. **Solution commitment** — not the problem reframe from problem_summary.

- State what you are building with the chosen approach
- Contrast with a wrong path only when it clarifies scope ("Not four separate exports — one corpus, transformed once")
- Cite `PRI-*` and key `FR-*` IDs
- May name formats/tools **now** (this is post-choice)

## Chosen Approach

**Name:** [e.g. "TS transform CLI + chunked markdown corpus + Cursor for ad-hoc queries"]
**Status:** Human Reviewed
**Addresses:** [FR-*, NFR-*, SC-* list]
**Aligned priorities:** [PRI-* list]
**Rationale:** [Why this won — cite COMPARE Fit Matrix and PRI-* tie-breaker vs other options in solution_options.md]

## Solution Coverage Map

One row per `SC-*`, `FR-*`, and `NFR-*` from problem_summary.

| ID | Requirement (one line) | How chosen approach meets it | Confidence | Gap / risk |
|----|------------------------|------------------------------|------------|------------|
| SC-1 | … | … | High / Medium / Low | — or specific gap |
| FR-1 | … | … | … | … |
| NFR-1 | … | … | … | … |

**Confidence rules:**
- **High** — chosen approach clearly satisfies; no open design question
- **Medium** — satisfied in principle; details TBD or depends on unresolved Q-*
- **Low** — weak fit, known gap, or requires follow-up decision before implementation

## Refinement Tasks

List only **Medium** and **Low** confidence rows from the map:

| ID | Task | Blocks implementation? |
|----|------|--------------------------|
| FR-7 | Define chunk size and index schema | Yes / No |

If any row is **Low** and blocks implementation, say so explicitly at the top.

## Requirement Traceability Matrix

Update (or create) with same IDs. Map Status from confidence:

| Confidence | Matrix Status |
|------------|---------------|
| High | Addressed |
| Medium | Partial |
| Low | Pending |

| ID | Requirement (one line) | Addressed by | Status |
|----|------------------------|--------------|--------|
| … | … | Chosen Approach name | Partial / Addressed / Pending |

---

**Behavior rules:**

1. Do not restate full requirement prose — cite IDs; one-line summaries only.
2. Every Medium/Low row must appear in Refinement Tasks.
3. Do not mark all rows High unless honestly justified.
4. Flag conflicts with `OOS-*` or `ASM-*` explicitly in Gap / risk column.
5. If problem_summary open questions (`Q-*`) affect confidence, reference them in Gap / risk.

**Footer for design_decisions.md:**

> Solution Coverage Map reflects chosen approach as of [date]. Re-run this prompt if the approach changes.
