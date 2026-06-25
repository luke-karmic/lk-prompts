# Luke 2026 AI Engineering Toolkit

A human-led, AI-assisted workflow for technical interviews and production-grade problem solving. You stay in the driver's seat — AI accelerates framing, analysis, and implementation while you own every decision.

**New here?** Read [HOW_TO_USE.md](HOW_TO_USE.md) for the step-by-step workflow. **Example walkthrough:** [examples/walkthrough_ig_corpus.md](examples/walkthrough_ig_corpus.md)

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
├── .cursor/
│   └── rules/
│       └── lk-engineering.mdc  # from ide/fintech_project_cursor_rules.md (via scaffold)
├── docs/
│   ├── problem_summary.md      # Step 1 — WHAT & WHY (stable IDs)
│   ├── solution_options.md     # Step 2 — OPTIONS (fit matrix, risks)
│   ├── design_decisions.md     # COMMIT — CHOSEN (coverage map)
│   ├── acceptance_criteria.md  # DEFINE — AC-* traces to FR-*/NFR-*
│   └── reports/                # Phase 3+ — auto-saved review outputs
│       ├── security_2026_report.md
│       ├── code_quality_report.md
│       ├── testability_report.md
│       └── integration_architecture.md
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

**Goal:** Establish WHAT & WHY before any architecture or code.

1. Write `docs/problem_summary.md` yourself, or use the **Problem Statement Expander** from [`project_toolkit/01_frame_problem_summary.md`](project_toolkit/01_frame_problem_summary.md).

   Output includes stable IDs (`PRI-*`, `SC-*`, `FR-*`, `NFR-*`, `CON-*`, `OOS-*`, `ASM-*`, `Q-*`):
   - Problem statement + success criteria
   - **Optimization priorities** (ranked — drives every later trade-off)
   - Functional, non-functional, constraints, out of scope, assumptions
   - Open questions + considerations coverage table

   Answer any **Questions for Human** before proceeding. No solution content in this file.

2. Run **Solution Options** from [`project_toolkit/02_compare_solution_options.md`](project_toolkit/02_compare_solution_options.md).

   Generates `docs/solution_options.md`: Requirements Fit Matrix (every SC/FR/NFR × each approach), risks, trade-offs, future concerns. **Status: Exploring** — you choose.

3. Run **Solution Coverage Map** from [`project_toolkit/03_commit_solution_coverage.md`](project_toolkit/03_commit_solution_coverage.md) after choosing.

   Generates `docs/design_decisions.md`: What We're Building + Coverage Map + Refinement Tasks.

   **Formal mode (optional):** [`02b_formal_decisions_bootstrap.md`](project_toolkit/02b_formal_decisions_bootstrap.md) for bulk interview draft.

---

### Phase 2: Iterative Human Decisions (5–10 min)

**Goal:** Lock in HOW with explicit rationale and requirement traceability.

Use **Decision Refiner** from [`project_toolkit/04_sharpen_single_decision.md`](project_toolkit/04_sharpen_single_decision.md). **Start with Core Architecture / Approach.**

1. Review the **Approach Fit Analysis** table — each concern rated Strong/Weak/Required/etc. per option
2. Confirm the summary cites `PRI-*` as tie-breaker
3. Set `Decision Topic to Refine` (e.g. "Core Architecture / Approach")
4. **You** make the final call — edit if needed
5. Confirm `Status: Human Reviewed` → updates Solution Overview + Traceability Matrix

Each recorded decision cites `Addresses: FR-*`, `Aligned priorities: PRI-*`, and links to Fit Analysis.

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
| Architecture & Diagram | [`project_toolkit/05_diagram_architecture.md`](project_toolkit/05_diagram_architecture.md) | Mermaid flowchart + approach evaluation |
| Gap Analysis | [`project_toolkit/06_analyze_gaps.md`](project_toolkit/06_analyze_gaps.md) | Prioritized gaps in design |
| 2026 Security Review | [`reports/project_output_security_audit.md`](reports/project_output_security_audit.md) | → `docs/reports/security_2026_report.md` |

Run additional reviews as time allows:

| Prompt | File | Output |
|--------|------|--------|
| Code Quality | [`reports/project_output_code_quality.md`](reports/project_output_code_quality.md) | → `docs/reports/code_quality_report.md` |
| Testability | [`reports/project_output_testability.md`](reports/project_output_testability.md) | → `docs/reports/testability_report.md` |
| Performance & Optimal Metrics | [`reports/project_output_optimal_metrics.md`](reports/project_output_optimal_metrics.md) | → `docs/reports/performance_metrics_report.md` |
| Observability Metrics | [`reports/project_output_observability_metrics.md`](reports/project_output_observability_metrics.md) | → `docs/reports/metrics_recommendations.md` |
| Testing Pyramid | [`reports/project_output_testing_pyramid.md`](reports/project_output_testing_pyramid.md) | → `docs/reports/testing_pyramid_analysis.md` |

**Before running review prompts:** Set the configuration block at the top of each prompt (language, project type, domain). Paste or reference `docs/problem_summary.md` and `docs/design_decisions.md` for context.

All review reports follow the same structure:

- Executive summary with overall risk/quality level
- Findings: **Critical → High → Medium → Low**
- Positive aspects
- Recommended updates to `docs/design_decisions.md`
- Next steps

---

### Phase 4: Implementation (10–15 min)

**Goal:** Ship working code that reflects your decisions.

1. Generate code in **small chunks** (one module or feature at a time)
2. Reference `docs/design_decisions.md` in each implementation prompt
3. For TypeScript projects, optionally start with [`scaffolding/project_generate_typescript_scaffold.md`](scaffolding/project_generate_typescript_scaffold.md) for a strict, production-grade baseline (includes `docs/` layout and `.cursor/rules/lk-engineering.mdc` from [`ide/fintech_project_cursor_rules.md`](ide/fintech_project_cursor_rules.md))
4. **Review manually** after each chunk — do not accept large diffs blindly

Prompt pattern:

```markdown
Implement [specific module] according to docs/design_decisions.md.
Every change must trace to FR-* / NFR-* cited in the relevant decision.
Respect PRI-* ordering from docs/problem_summary.md.
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

Prompt files follow `{phase}_{verb}_{artifact}.md` (e.g. `01_frame_problem_summary.md`). Formal bootstrap uses `02b_` prefix.

### Workflow (ordered)

| Phase | Purpose | File | Output |
|------|---------|------|--------|
| FRAME | Problem statement expander | [`project_toolkit/01_frame_problem_summary.md`](project_toolkit/01_frame_problem_summary.md) | `docs/problem_summary.md` |
| COMPARE | **Solution options** | [`project_toolkit/02_compare_solution_options.md`](project_toolkit/02_compare_solution_options.md) | `docs/solution_options.md` |
| COMMIT | Solution coverage map | [`project_toolkit/03_commit_solution_coverage.md`](project_toolkit/03_commit_solution_coverage.md) | `docs/design_decisions.md` |
| Formal bootstrap | Decisions bootstrap (formal only) | [`project_toolkit/02b_formal_decisions_bootstrap.md`](project_toolkit/02b_formal_decisions_bootstrap.md) | bulk `design_decisions.md` draft |
| SHARPEN | Iterative decision refiner (formal) | [`project_toolkit/04_sharpen_single_decision.md`](project_toolkit/04_sharpen_single_decision.md) | updates `docs/design_decisions.md` |
| DIAGRAM | Architecture & Mermaid diagram | [`project_toolkit/05_diagram_architecture.md`](project_toolkit/05_diagram_architecture.md) | Mermaid + evaluation |
| ANALYZE | Gap analysis | [`project_toolkit/06_analyze_gaps.md`](project_toolkit/06_analyze_gaps.md) | prioritized design gaps |
| DEFINE | Acceptance criteria | [`project_toolkit/07_define_acceptance_criteria.md`](project_toolkit/07_define_acceptance_criteria.md) | `docs/acceptance_criteria.md` |
| VERIFY | Acceptance verification | [`project_toolkit/08_verify_acceptance.md`](project_toolkit/08_verify_acceptance.md) | `docs/reports/acceptance_criteria_verification.md` |

### Traceability

Requirement IDs live in `docs/problem_summary.md`. The **Requirement Traceability Matrix** and **Approach Fit Analysis** live only in `docs/design_decisions.md`.

| ID prefix | Document | Purpose |
|-----------|----------|---------|
| `PRI-*`, `FR-*`, `NFR-*`, `SC-*`, … | problem_summary | WHAT — frozen after Step 1 |
| Fit + Confidence per option | **solution_options** | COMPARE — before choosing |
| Coverage Map | design_decisions | COMMIT — confidence after COMMIT |
| `AC-*` | acceptance_criteria | Verification → `FR-*` / `NFR-*` |

See [HOW_TO_USE.md](HOW_TO_USE.md) and [examples/walkthrough_ig_corpus.md](examples/walkthrough_ig_corpus.md).

### Project output (reviews → `docs/reports/`)

| Purpose | File | Output |
|---------|------|--------|
| Security audit (2026) | [`reports/project_output_security_audit.md`](reports/project_output_security_audit.md) | `docs/reports/security_2026_report.md` |
| Security findings (codebase) | [`reports/project_output_security_findings.md`](reports/project_output_security_findings.md) | inline report |
| Code quality | [`reports/project_output_code_quality.md`](reports/project_output_code_quality.md) | `docs/reports/code_quality_report.md` |
| Testability | [`reports/project_output_testability.md`](reports/project_output_testability.md) | `docs/reports/testability_report.md` |
| Testing pyramid | [`reports/project_output_testing_pyramid.md`](reports/project_output_testing_pyramid.md) | `docs/reports/testing_pyramid_analysis.md` |
| Performance & optimal metrics | [`reports/project_output_optimal_metrics.md`](reports/project_output_optimal_metrics.md) | `docs/reports/performance_metrics_report.md` |
| Observability metrics | [`reports/project_output_observability_metrics.md`](reports/project_output_observability_metrics.md) | `docs/reports/metrics_recommendations.md` |
| Acceptance verification | [`project_toolkit/08_verify_acceptance.md`](project_toolkit/08_verify_acceptance.md) | `docs/reports/acceptance_criteria_verification.md` |
| Integration architecture | [`reports/project_output_integration_architecture.md`](reports/project_output_integration_architecture.md) | `docs/reports/integration_architecture.md` |
| PR description | [`reports/project_output_pr_notes.md`](reports/project_output_pr_notes.md) | `docs/pr_notes.md` |

### Design output / refine

| Purpose | File | Output |
|---------|------|--------|
| Data structures (interactive) | [`architecture/design_output_data_structures.md`](architecture/design_output_data_structures.md) | `docs/reports/data_structures.md` |
| Project architecture (interactive) | [`architecture/design_refine_project_architecture.md`](architecture/design_refine_project_architecture.md) | ADR → `docs/design_decisions.md` |
| ADR from decision | [`architecture/design_output_adr.md`](architecture/design_output_adr.md) | ADR document |

### Project generate (code / config)

| Purpose | File | Output |
|---------|------|--------|
| TypeScript project scaffold | [`scaffolding/project_generate_typescript_scaffold.md`](scaffolding/project_generate_typescript_scaffold.md) | full TS project + cursor rules |
| Scaffold from docs | [`scaffolding/project_generate_scaffold_from_docs.md`](scaffolding/project_generate_scaffold_from_docs.md) | project files + README |
| Docker database setup | [`project_toolkit/project_generate_docker_database.md`](project_toolkit/project_generate_docker_database.md) | `docker-compose.yml`, scripts |
| TypeScript domain types | [`project_toolkit/project_generate_typescript_types.md`](project_toolkit/project_generate_typescript_types.md) | `src/types.ts` |

### IDE rules & practice

| Purpose | File | Notes |
|---------|------|-------|
| Cursor / AI behavior rules | [`ide/fintech_project_cursor_rules.md`](ide/fintech_project_cursor_rules.md) | → `.cursor/rules/lk-engineering.mdc` |
| Table summary style rule | [`ide/table_summary_concise_rule.md`](ide/table_summary_concise_rule.md) | optional cursor rule |
| Requirement elicitation sim | [`client_related/interview_simulate_requirement_elicitation.md`](client_related/interview_simulate_requirement_elicitation.md) | 5-min interview practice |

---

## How to Use Effectively

### Stay human-led

AI proposes; you dispose. The workflow breaks down when you skip Phase 2 or accept batched decisions. Every recorded decision should have your explicit `Status: Human Reviewed`.

### Priorities are the anchor

Optimization priorities in `docs/problem_summary.md` resolve ambiguity. When the AI recommends something that conflicts with your priorities, override it and note why in the rationale.

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
[ ] docs/problem_summary.md — IDs assigned, open questions answered
[ ] docs/solution_options.md — Fit Matrix, Status still Exploring until you choose
[ ] docs/design_decisions.md — Coverage Map after COMMIT
[ ] Core Architecture: Human Reviewed + Solution Overview written
[ ] Each decision: cites FR-*/PRI-*, Status Human Reviewed
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
