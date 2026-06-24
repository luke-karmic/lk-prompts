# Walkthrough Example — IG Chat Export → LLM Corpus

End-to-end **Steps 0–3** for the IG export problem.

| Step | Prompt | Output file |
|------|--------|-------------|
| 1 | [`1_design_output_problem_summary.md`](../project_toolkit/1_design_output_problem_summary.md) | `docs/problem_summary.md` |
| 2 | [`2_design_output_solution_options.md`](../project_toolkit/2_design_output_solution_options.md) | `docs/solution_options.md` |
| 2.5 | [`2.5_design_output_solution_coverage.md`](../project_toolkit/2.5_design_output_solution_coverage.md) | `docs/design_decisions.md` |
| 3 | Chat refine | updates `design_decisions.md` |

---

## Step 0 — Setup

```bash
mkdir -p docs/reports
```

Pin prompts 1, 2, and 2.5.

---

## Step 1 — Problem Framing

**Paste into Step 1 prompt:**

```text
Here is an IG export of the chat. It will be used for LLMs for learning about my
psychology, past mistakes, learnings, JP to EN dynamics, but also used in my JP
translation project for generating sentences as a source. This JSON is the current
format. It should be made as easy as possible for an LLM to use for these purposes.

Consider memory/token usage, ease of understanding, indexing.
```

**Output:** `docs/problem_summary.md` — see Step 1 section in prior version for full FR/SC/PRI list. Answer Q-2 (your messages only for sentence gen) and Q-3 (chunked + index) before Step 2.

---

## Step 2 — Solution Options

**Run Step 2 prompt** with `@docs/problem_summary.md`.

**Output:** `docs/solution_options.md` (abbreviated)

### 1. Candidate Approaches

**Raw JSON + system prompt** — Pass export inline each session; no transform.  
**Best for:** nothing at scale. **Obvious weakness:** token cost, no indexing.

**Single large markdown** — One-time manual or script conversion to one `.md` file.  
**Best for:** small exports. **Obvious weakness:** doesn't scale; weak FR-7.

**Chunked markdown + CLI transform** — pnpm CLI: JSON → `corpus/chunks/` + `manifest.json`.  
**Best for:** PRI-1, PRI-2, FR-6, FR-7. **Obvious weakness:** upfront schema design.

**LLM-assisted transform** — Model summarizes/tags during conversion.  
**Best for:** FR-3, FR-4 tagging. **Obvious weakness:** NFR-3, NFR-1 drift.

### 2. Requirements Fit Matrix

| ID | Requirement (one line) | Raw JSON + prompt | Single markdown | Chunked MD + CLI | LLM transform |
|----|------------------------|-------------------|-----------------|------------------|---------------|
| SC-1 | One corpus, four uses | Weak · Low — re-upload per use | Adequate · Med — one file, manual slices | Strong · High — manifest purpose tags | Adequate · Med — tags may drift |
| SC-2 | Fewer tokens than raw | Weak · High — full dump | Weak · High — whole file | Strong · High — one chunk | Adequate · Med — summary loss |
| SC-3 | Locatable without full load | Weak · High — no index | Adequate · Med — headings only | Strong · High — manifest | Adequate · Med — semantic search TBD |
| SC-4 | JP sentences without psych noise | Weak · High — all mixed | Adequate · Med — manual section | Strong · High — jp-sentences slice | Adequate · Med — filter quality varies |
| FR-1 | Ingest IG JSON | Required · High — native | Adequate · Med — needs converter | Required · High — CLI import | Required · High — needs pipeline |
| FR-2 | LLM-optimized output | Weak · Med — raw nested JSON | Strong · Med — markdown | Strong · High — chunk + frontmatter | Strong · Med — prose summaries |
| FR-3 | Psychology retrieval | Adequate · Low — if fits context | Adequate · Med | Strong · Med — purpose chunks | Strong · Med — auto tags unverified |
| FR-6 | JP sentence source | Weak · High — noisy | Adequate · Med | Strong · High — filtered slice | Adequate · Med |
| FR-7 | Indexing/navigation | Weak · High | Adequate · Med | Strong · Med — schema TBD (Q-3) | Adequate · Low — embedding scope |
| NFR-1 | Token efficiency | Weak · High | Weak · High | Strong · High | Adequate · Med |
| NFR-3 | Repeatable transform | N/A · High | Weak · Med — manual | Strong · High — deterministic | Weak · High — model drift |
| NFR-4 | Sensitive content | Adequate · Med — paste to cloud | Adequate · Med | Strong · High — local corpus | Weak · Med — sends to model |

### 3. Option Assessment Summary (excerpt)

**Chunked markdown + CLI transform**

| Dimension | Assessment |
|-----------|------------|
| **Overall confidence** | **High** — best balance on PRI-1, PRI-2, NFR-3 |
| **Fully met (High)** | SC-1, SC-2, SC-4, FR-1, FR-6, NFR-1, NFR-3 |
| **Partial or weak** | FR-7 · Med — manifest TBD; FR-3 · Med — tagging heuristics |
| **Priority conflicts** | Sacrifices PRI-4 if over-compressed — mitigate with lossless source archive |
| **Key risks** | Manifest schema wrong → rework; chunk size wrong → token or context issues |
| **Trade-offs** | Upfront CLI work vs long-term chat simplicity; no LLM magic on transform |
| **Future concerns** | Export grows 10x; new IG schema; fifth use case needs manifest extension |
| **Blocks choice if** | Q-1 volume unknown — affects chunk strategy |

### 4. Cross-Option Comparison

| Approach | Overall | Best for PRI-* | Weakest on | Future risk |
|----------|---------|----------------|------------|-------------|
| Raw JSON + prompt | Low | — | All SC/NFR-1 | Unusable as corpus grows |
| Single markdown | Low | PRI-3 | FR-7, NFR-1 | File size ceiling |
| **Chunked MD + CLI** | **High** | PRI-1, PRI-2 | FR-7 until schema | Schema migration |
| LLM transform | Medium | PRI-3 (readability) | NFR-3, NFR-4 | Drift, cost, privacy |

### 5. Draft Recommendation

**Leaning toward:** Chunked markdown + CLI transform — **Status: Exploring (not chosen)**

**Why:** Strong · High on more SC/FR/NFR rows than alternatives; aligns with PRI-1 and PRI-2. LLM transform fails NFR-3; raw JSON fails SC-2.

### 6. Open Items Before Choosing

| ID | Question | Affects |
|----|----------|---------|
| Q-1 | Export size? | Chunk size for all approaches |

**You choose:** Chunked markdown + CLI. Cursor for ad-hoc `@corpus/` queries only.

---

## Step 2.5 — Solution Coverage Map

**Run Step 2.5** with chosen approach (matches Step 2 option name).

**Output:** `docs/design_decisions.md` — What We're Building, Coverage Map, Refinement Tasks (FR-7 manifest schema blocks implementation).

*(Same as prior walkthrough Step 2.5 section.)*

---

## Step 3 — Refine

Refine FR-7 manifest schema → FR-7, SC-3 confidence → High.

---

## Flow

```
problem_summary.md  →  solution_options.md  →  [choose]  →  design_decisions.md  →  refine
     WHAT                  OPTIONS                         CHOSEN
```

## Cheat sheet

| Step | Prompt | You provide |
|------|--------|-------------|
| 1 | `1_...` | Raw unstructured problem |
| 2 | `2_...` | `@problem_summary.md` |
| — | — | Review matrix; pick approach |
| 2.5 | `2.5_...` | Chosen approach name from Step 2 |
| 3 | Chat | Refine Medium/Low from Coverage Map |
