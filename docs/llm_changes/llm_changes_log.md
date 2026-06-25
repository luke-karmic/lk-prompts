## [2026-06-25] - FCCBV Prompt Renaming

**Summary:** Renamed project_toolkit workflow prompts to `{phase}_{verb}_{artifact}.md` and added FCCBV cheat sheet to HOW_TO_USE.

**Files Changed:**
- `project_toolkit/01_frame_problem_summary.md` (was `1_design_output_*`)
- `project_toolkit/02_compare_solution_options.md`
- `project_toolkit/02b_formal_decisions_bootstrap.md`
- `project_toolkit/03_commit_solution_coverage.md`
- `project_toolkit/04_sharpen_single_decision.md`
- `project_toolkit/05_diagram_architecture.md`
- `project_toolkit/06_analyze_gaps.md`
- `project_toolkit/07_define_acceptance_criteria.md`
- `project_toolkit/08_verify_acceptance.md` (new)
- `HOW_TO_USE.md`
- `README.md`
- `examples/walkthrough_ig_corpus.md`

**Key Changes:**
- Phase names: FRAME, COMPARE, COMMIT, SHARPEN, BUILD, DEFINE, VERIFY
- Printable cheat sheet and Go/coding-task shortcut in HOW_TO_USE
- VERIFY prompt moved into project_toolkit as `08_verify_acceptance.md`

**Reasoning:**
- Old step numbers (1, 2, 2.5, 3) were hard to memorize; verb-based phases match the user's choose-then-verify workflow.
