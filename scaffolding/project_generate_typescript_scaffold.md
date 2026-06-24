You are a principal TypeScript engineer setting up a production-grade project in mid-2026 according to highest industry standards.

Create a best-in-class scaffold with the following requirements:

**Core Requirements:**
- Package manager: **pnpm**
- TypeScript 5.5+ with strictest settings (`strict: true`, `exactOptionalPropertyTypes`, `noUncheckedIndexedAccess`)
- Use **Biome** for linting + formatting (preferred in 2026) or ESLint + Prettier if Biome is not suitable
- Comprehensive TSDoc / JSDoc on all public interfaces
- Heavy use of generics and utility types where appropriate
- No `any`, no `unknown` abuse, strong typing everywhere
- Error handling using custom error classes or Result pattern
- Testing: Vitest + happy path + edge cases + property-based testing where useful

**Documentation Layout:**
Create the docs structure used by the Luke 2026 AI Engineering Toolkit:

```
docs/
├── problem_summary.md
├── design_decisions.md
├── acceptance_criteria.md
└── reports/
```

Add minimal placeholder headers to each doc file so the structure is ready for the interview/delivery workflow.

**Cursor / AI Rules:**
Create `.cursor/rules/lk-engineering.mdc` with `alwaysApply: true`.

Use the **exact rule body** from `ide/fintech_project_cursor_rules.md` in this toolkit. If you can read that file from the repo, use it directly. Otherwise, use the content provided when this prompt was pasted.

The `.mdc` file must use this structure:

```markdown
---
description: Luke 2026 engineering behavior — fintech, human-led decisions, docs-first workflow
alwaysApply: true
---

[paste full body from ide/fintech_project_cursor_rules.md here, excluding the top-level title if redundant]
```

Do not paraphrase or shorten the rules. Preserve all sections: Core Principles, Documentation & Workflow Rules, Output Style, Security & Fintech Rules, Response Guidelines.

**Project Structure:**
Recommend a clean, scalable structure (src/core, src/features, src/lib, tests/, docs/, etc.)

**Output:**
1. Complete `package.json` with all recommended dependencies (include dev tools)
2. `tsconfig.json` (strict)
3. Biome / ESLint + Prettier config
4. Recommended folder structure with explanation
5. Sample `src/index.ts` and its test file showing high-quality patterns
6. `.cursor/rules/lk-engineering.mdc` (from `ide/fintech_project_cursor_rules.md`)
7. `docs/` folder with placeholder files listed above
8. Any other important config files (`.gitignore`, etc.)

Aim for code that would pass a senior staff engineer code review at a top fintech or tech company in 2026.
