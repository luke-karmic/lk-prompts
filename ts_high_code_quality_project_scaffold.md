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

**Project Structure:**
Recommend a clean, scalable structure (src/core, src/features, src/lib, tests/, docs/, etc.)

Output:
1. Complete `package.json` with all recommended dependencies (include dev tools)
2. `tsconfig.json` (strict)
3. Biome / ESLint + Prettier config
4. Recommended folder structure with explanation
5. Sample `src/index.ts` and its test file showing high-quality patterns
6. Any other important config files (`.gitignore`, etc.)

Aim for code that would pass a senior staff engineer code review at a top fintech or tech company in 2026.