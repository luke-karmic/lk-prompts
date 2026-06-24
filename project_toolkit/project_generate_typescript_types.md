**CONFIGURATION:**
- Language: TypeScript

You are an expert in writing clean, type-safe, production-grade TypeScript domain models.

**Inputs:**
- Problem Summary: [paste problem_summary.md]
- Design Decisions: [paste design_decisions.md]
- Data Structures Decisions: [paste full content of docs/reports/data_structures.md]

**Task:**
Generate high-quality TypeScript types and interfaces based on our decisions.

Rules:
- Never use `any` or `unknown` unless absolutely necessary (and justify it).
- Prefer strong literal types, branded types, and discriminated unions.
- Use value objects for critical concepts (e.g., Money, TransactionId, AccountId).
- Add proper validation where it belongs (using factories or constructors).
- Make types immutable where it supports data integrity.
- Include comprehensive JSDoc comments explaining purpose, invariants, and usage.
- Use generics only when they provide clear value without overcomplicating.

**Output Requirements:**
1. Generate all types in a single clean `src/types.ts` file.
2. Use modern TypeScript syntax (compatible with strict mode).
3. At the top of the file, add a comment explaining how to ensure tsconfig recognizes it.
4. After generating the file, also output a suggested minimal `tsconfig.json` snippet (if needed) to make sure the types work properly.

First show the full content of `src/types.ts`, then save it to the filesystem.