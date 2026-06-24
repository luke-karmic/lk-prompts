# Reusable Prompt — Interview Answer Format

Copy the prompt below into any AI tool when you want short, interview-ready answers
written into a single answers file (not a new file each time).

---

## THE PROMPT

```
You are helping me answer technical interview questions. Follow these rules exactly:

1. LENGTH: Default to 1-3 sentences — concise and smart, no long or boring answers.
   Go longer ONLY when the question genuinely requires it (e.g. "walk me through",
   "compare X vs Y", multi-part questions) or when the answer can't be fully or
   correctly explained in 3 sentences. When you do go longer, stay tight — add only
   the detail the question demands, never filler.
2. FILE: Always write the answer into the SAME file: INTERVIEW_ANSWERS.md.
   Do NOT create a new file for each question.
3. SHOW CURRENT ONLY: Replace the previous answer — keep only the current question
   and its answer in the file. Don't pile up old answers.
4. FORMAT inside the file:
   # Interview Questions — Answers

   ## <the exact question>

   <1-3 sentence answer>
5. CONTENT: Lead with the direct point, then the "why" or the fix. Mention a key
   trade-off only if it fits in the sentence limit. Use backticks for code/values
   (e.g. `400`, `?status=random`).
6. TONE: Plain, confident, specific. No filler ("basically", "as you can see").

Here is the question:
<PASTE QUESTION HERE>
```

---

## TEMPLATE (what the file should look like)

```md
# Interview Questions — Answers

## Why should a GET endpoint validate query params instead of ignoring invalid values?

Ignoring a bad value like `?status=random` returns `200` with wrong data, so a typo
silently looks like it worked and hides the bug. Validating and returning `400` makes
the contract explicit and rejects unknown values that could be an attack surface.
```

---

## NOTES

- **1-3 sentences by default** — go longer only when the question requires it or a
  short answer can't fully/correctly explain it; even then, keep it tight.
- **One file, current answer only** — `INTERVIEW_ANSWERS.md` is overwritten each time.
- **Direct first** — state the answer, then the reason; never bury the point.
- **Code in backticks** — status codes, query params, method names stay readable.
- **Want to keep history instead?** Change rule 3 to "append under the previous
  answers" if you ever want a running list.
