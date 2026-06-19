# Luke 2026 AI Engineering Toolkit

A human-led, AI-assisted workflow for technical interviews and production-grade problem solving. You stay in the driver's seat — AI accelerates framing, analysis, and implementation while you own every decision.

---

## What This Is

This repo contains structured prompts for:

- Problem framing and prioritization
- Iterative design decisions
- Architecture and gap analysis
- Implementation scaffolding
- Automated quality and security reviews

Every review prompt produces a prioritized, professional report and auto-saves to `docs/reports/`. The result is a clear audit trail: what you decided, why, and what the code looks like under scrutiny.

---

## Setup (Once Per Interview)

```bash
mkdir -p docs/reports
```

Open this repo (or copy the prompts into your interview project) alongside Cursor or your preferred AI tool with **project directory access**. Pin the prompts you use most — you'll reference them repeatedly across phases.

**Recommended layout in your working project:**

```
your-project/
├── docs/
│   ├── problem_summary.md      # Phase 1 — you write or expand with AI
│   ├── design_decisions.md     # Phases 1–2 — living decision log
│   └── reports/                # Phase 3+ — auto-saved review outputs
│       ├── security_2026_report.md
│       ├── code_quality_report.md
│       └── testability_report.md
└── src/                        # Phase 4 — implementation
```

---

## The 40-Minute Workflow

| Phase | Time | Focus |
|-------|------|-------|
| 0. Setup | — | Folder structure + AI tool ready |
| 1. Human Framing | 3–6 min | Problem summary + decisions to make |
| 2. Iterative Decisions | 5–10 min | One topic at a time, human-reviewed |
| 3. Architecture & Gap Analysis | 4–7 min | Diagram + security + other reviews |
| 4. Implementation | 10–15 min | Small chunks, manual review |
| 5. Final Quality & Closure | 5–8 min | Remaining reviews, tests, verbal summary |

---

### Phase 0: Setup

Create `docs/reports/` and ensure your AI tool can read and write the project directory. No code yet — just the workspace.

---

### Phase 1: Human Framing (3–6 min)

**Goal:** Establish context and priorities before any architecture or code.

1. Write `docs/problem_summary.md` yourself, or use the **Problem Statement Expander** prompt from [`toolkit/1_engineering_toolkit.md`](toolkit/1_engineering_toolkit.md).

   Include:
   - Problem summary (3–5 sentences)
   - **Optimization priorities** (ranked — this drives every later decision)
   - Functional and non-functional requirements
   - Assumptions, edge cases, out of scope

2. Run the **Design Decisions Bootstrap** prompt from [`toolkit/2_design_decisions_refinement.md`](toolkit/2_design_decisions_refinement.md) to generate `docs/design_decisions.md` with a **Decisions To Be Made** list.

   Do not finalize decisions yet. Review the AI's initial recommendations and mark anything you disagree with.

---

### Phase 2: Iterative Human Decisions (5–10 min)

**Goal:** Lock in decisions one topic at a time with explicit rationale.

Use the **Decision Refiner** prompt from [`toolkit/3_decision_refiner.md`](toolkit/3_decision_refiner.md) for each topic:

1. Set `Decision Topic to Refine` (e.g. "Data Integrity & Validation Strategy")
2. Review the AI's options and recommendation
3. **You** make the final call — edit if needed
4. Confirm `Status: Human Reviewed` before moving on

Repeat for each item in **Decisions To Be Made**. Typical topics:

- Core architecture / approach
- Technology choices
- Data models & types
- Data integrity & validation
- Error handling & logging
- AI/LLM usage & guardrails (if relevant)
- Testing strategy
- Security & compliance

**Rule:** Never batch-decide. One topic per prompt invocation keeps ownership clear and prevents AI from silently overriding your priorities.

---

### Phase 3: Architecture & Gap Analysis (4–7 min)

With finalized (or mostly finalized) decisions:

| Prompt | File | Output |
|--------|------|--------|
| Architecture & Diagram | [`toolkit/4_diagramming.md`](toolkit/4_diagramming.md) | Mermaid flowchart + approach evaluation |
| Gap Analysis | [`toolkit/5_gap_analysis.md`](toolkit/5_gap_analysis.md) | Prioritized gaps in design |
| 2026 Security Review | [`reports/security_main_considerations.md`](reports/security_main_considerations.md) | → `docs/reports/security_2026_report.md` |

Run additional reviews as time allows:

| Prompt | File | Output |
|--------|------|--------|
| Code Quality | [`reports/code_quality.md`](reports/code_quality.md) | → `docs/reports/code_quality_report.md` |
| Testability | [`reports/testability.md`](reports/testability.md) | → `docs/reports/testability_report.md` |
| Performance & Scalability | Available on request | → `docs/reports/` |
| Reliability & Data Integrity | Available on request | → `docs/reports/` |

**Before running review prompts:** Set the configuration block at the top of each prompt (language, project type, domain). Paste or reference `docs/problem_summary.md` and `docs/design_decisions.md` for context.

All review reports follow the same structure:

- Executive summary with overall risk/quality level
- Findings: **Critical → High → Medium → Low**
- Positive aspects
- Recommended updates to `design_decisions.md`
- Next steps

---

### Phase 4: Implementation (10–15 min)

**Goal:** Ship working code that reflects your decisions.

1. Generate code in **small chunks** (one module or feature at a time)
2. Reference `docs/design_decisions.md` in each implementation prompt
3. For TypeScript projects, optionally start with [`high_code_quality_ts_project_scaffold.md`](high_code_quality_ts_project_scaffold.md) for a strict, production-grade baseline
4. **Review manually** after each chunk — do not accept large diffs blindly

Prompt pattern:

```markdown
Implement [specific module] according to docs/design_decisions.md.
Respect optimization priorities in docs/problem_summary.md.
Do not introduce patterns we explicitly rejected in design decisions.
```

---

### Phase 5: Final Quality & Closure (5–8 min)

1. Run any review prompts not yet executed (they auto-save to `docs/reports/`)
2. Generate tests aligned with your recorded testing strategy
3. Fix Critical and High findings if time permits
4. Prepare a verbal summary:
   - Problem and priorities
   - Key architectural decisions and trade-offs
   - What you'd do with more time
   - Point reviewers to `docs/reports/` for the full audit trail

---

## Prompt Reference

| Purpose | Location |
|---------|----------|
| Problem statement expander | [`toolkit/1_engineering_toolkit.md`](toolkit/1_engineering_toolkit.md) |
| Design decisions bootstrap | [`toolkit/2_design_decisions_refinement.md`](toolkit/2_design_decisions_refinement.md) |
| Iterative decision refiner | [`toolkit/3_decision_refiner.md`](toolkit/3_decision_refiner.md) |
| Architecture & Mermaid diagram | [`toolkit/4_diagramming.md`](toolkit/4_diagramming.md) |
| Gap analysis | [`toolkit/5_gap_analysis.md`](toolkit/5_gap_analysis.md) |
| 2026 security review (auto-save) | [`reports/security_main_considerations.md`](reports/security_main_considerations.md) |
| Code quality review (auto-save) | [`reports/code_quality.md`](reports/code_quality.md) |
| Testability review (auto-save) | [`reports/testability.md`](reports/testability.md) |
| Full codebase security audit | [`security/top_flaws_project_check_report.md`](security/top_flaws_project_check_report.md) |
| TypeScript project scaffold | [`high_code_quality_ts_project_scaffold.md`](high_code_quality_ts_project_scaffold.md) |

---

## How to Use Effectively

### Stay human-led

AI proposes; you dispose. The workflow breaks down when you skip Phase 2 or accept batched decisions. Every recorded decision should have your explicit `Status: Human Reviewed`.

### Priorities are the anchor

Optimization priorities in `problem_summary.md` resolve ambiguity. When the AI recommends something that conflicts with your priorities, override it and note why in the rationale.

### One thing at a time

- One decision topic per Decision Refiner invocation
- One module per implementation prompt
- One review prompt at a time (each produces a full report)

### Configure before reviewing

Review prompts have a configuration block at the top. Set language, project type, and domain **before** running — findings and recommendations depend on it.

### Treat reports as artifacts, not homework

`docs/reports/` is what you show interviewers or reviewers. Skim Critical/High, mention one positive aspect, and reference specific findings in conversation. You don't need to fix everything in 40 minutes.

### Re-run reviews after significant changes

If implementation diverges from design decisions, re-run the relevant review prompt. Reports are cheap to regenerate; stale findings are not.

---

## Quick Checklist

```
[ ] mkdir -p docs/reports
[ ] docs/problem_summary.md — priorities ranked
[ ] docs/design_decisions.md — Decisions To Be Made listed
[ ] Each decision: Human Reviewed with rationale
[ ] Mermaid architecture diagram generated
[ ] Security review → docs/reports/security_2026_report.md
[ ] Code quality + testability reviews (if time)
[ ] Implementation in small chunks, manually reviewed
[ ] Tests generated per testing strategy
[ ] Verbal summary ready; docs/reports/ referenced
```

---

## Philosophy

This workflow is mature by design:

- **Human-led** — you frame the problem and own every decision
- **Well-documented** — decisions, rationale, and review artifacts persist
- **AI-leveraged** — AI handles expansion, analysis, and boilerplate at speed
- **Review-ready** — prioritized reports give interviewers a clear signal of engineering judgment

The AI is a senior collaborator, not an autopilot. Strong ownership plus structured artifacts is the differentiator.
