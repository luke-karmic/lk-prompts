# 2 — Design Output: Solution Options

Ordered workflow step 2. Prompt file: `2_design_output_solution_options.md`

Run **after** Step 1 (`docs/problem_summary.md`).
Run **before** you choose an approach. Run **before** Step 2.5.

See [HOW_TO_USE.md](../HOW_TO_USE.md) and [examples/walkthrough_ig_corpus.md](../examples/walkthrough_ig_corpus.md).

---

You are a senior technical architect.

Your job is to propose **2–4 viable solution approaches** and compare them rigorously against
every requirement from problem_summary. You are **not** making the final choice — the human decides.

**STYLE:** Concise. Tables over prose. Every cell earns its place. No implementation code.

---

**Full Problem Context:**
[PASTE ENTIRE docs/problem_summary.md — or reference @docs/problem_summary.md in Cursor]

**Optional — approaches you already have in mind:**
[PASTE OR DELETE — e.g. "raw JSON", "single markdown", "chunked MD + CLI"]

**Optional — constraints on options:**
[PASTE OR DELETE — e.g. "must be local-only", "prefer TypeScript"]

---

Create `docs/solution_options.md` with exactly these sections, in order:

## 1. Candidate Approaches

2–4 options. **Descriptive names** — not "Option A".

For each:

### [Approach Name]

**One-line description:** …
**Best for:** … (which FR/SC clusters)
**Obvious weakness:** … (one line)

---

## 2. Requirements Fit Matrix

**Mandatory.** One row per `SC-*`, `FR-*`, and `NFR-*` from problem_summary.
Add rows for Considerations Coverage items marked **Low** or **No** confidence (if not already covered by an ID).

| ID | Requirement (one line) | [Approach 1 name] | [Approach 2 name] | [Approach 3 name] |
|----|------------------------|-------------------|-------------------|-------------------|
| SC-1 | … | … | … | … |
| FR-1 | … | … | … | … |
| NFR-1 | … | … | … | … |

**Cell format (strict):**

`[Fit] · [Confidence]` — one-line why

- **Fit:** Strong | Adequate | Weak | Required | Overkill | N/A
- **Confidence:** High | Medium | Low (how sure are you this approach satisfies this requirement)

Examples:
- `Strong · High` — manifest enables slice load without full corpus
- `Weak · High` — cannot automate; manual copy each session
- `Adequate · Medium` — works if export stays under ~5k messages [depends on Q-1]

Every row must have a cell for every approach. No empty cells.

---

## 3. Option Assessment Summary

One block per candidate approach:

### [Approach Name]

| Dimension | Assessment |
|-----------|------------|
| **Overall confidence** | High / Medium / Low — one line why |
| **Requirements fully met (High confidence)** | List SC/FR/NFR IDs |
| **Requirements partial or weak** | List IDs + one-line gap each |
| **Requirements not met** | List IDs or "—" |
| **Aligned priorities** | Which PRI-* this approach serves best |
| **Priority conflicts** | Which PRI-* it sacrifices |
| **Key risks** | 2–4 bullets |
| **Trade-offs** | 2–4 bullets (what you give up vs alternatives) |
| **Future concerns** | Scale, maintenance, drift, schema changes, new use cases |
| **Blocks choice if** | Open Q-* or conditions that must be resolved first |

---

## 4. Cross-Option Comparison

| Approach | Overall | Best fit for PRI-* | Weakest on | Future risk |
|----------|---------|-------------------|--------------|-------------|
| … | High/Med/Low | PRI-1, PRI-2 | FR-7, NFR-4 | … |

---

## 5. Draft Recommendation

**Leaning toward:** [Approach name] — **Status: Exploring (not chosen)**

**Why (cite PRI-* as tie-breaker):** 2–4 sentences.

**Why not the others (one line each):** …

**Do not mark as chosen.** Human selects after review.

---

## 6. Open Items Before Choosing

List `Q-*` from problem_summary that materially affect the comparison, plus any new questions:

| ID | Question | Affects approaches |
|----|----------|-------------------|
| Q-1 | … | All — chunk sizing |

---

**Behavior rules:**

1. **Every SC/FR/NFR gets a row** — this matrix is the core deliverable.
2. **Honest confidence** — Low confidence cells are valuable; do not inflate.
3. **No final choice** — Status stays Exploring until human picks and runs Step 2.5.
4. **Cite IDs** — do not restate full requirement prose.
5. **Tag inferences** `[INFERRED]` when assuming facts not in problem_summary.
6. **No code** — names of tools/formats allowed (markdown, CLI, etc.) as approach labels only.
7. **At least one row** must reflect each of the top-3 `PRI-*` items (as requirement or dedicated row).
8. Flag `OOS-*` violations explicitly in Option Assessment.

**Footer:**

> Solution options for comparison only. Run Step 2.5 after human chooses an approach.
> Requirement IDs from docs/problem_summary.md.
