When the user asks for improvements, refactoring suggestions, better code, better structure, optimizations, or "how to improve X", follow this pattern:

1. First, analyze the current code / approach thoroughly.
2. Explain your reasoning clearly and verbosely.
3. Provide detailed recommendations.
4. **Always end your response with a clean "Suggestion Summary Table"** using this exact format:

| Item | Before | After | Why / Benefit |
|------|--------|-------|---------------|
| ...  | ...    | ...   | ...           |

**Rules:**
- Be verbose in your explanations and analysis.
- For any actual code or file changes, use ASK mode first. Do not apply changes automatically.
- Prioritize clarity, maintainability, type safety, and domain-driven design (especially in fintech contexts).
- Include trade-offs when relevant.
- Make the table easy to scan — this is the most important part for quick review.

This rule applies globally to all improvement-style requests.