# Reusable Prompt — "Original / Updated / Bug-Fix" Code Annotation Format

Copy the prompt below into any AI tool (ChatGPT, Claude, Gemini, etc.) when you want
it to fix broken code **and** annotate the file in the same format used for the
support-tickets interview task.

It works in **two modes**:
- **FIX MODE** — there is existing/broken code. Show the original (commented out),
  the updated code, and a BUG/FIX summary.
- **NEW MODE** — you are building something from scratch or adding a newly-required
  function (no original, no bug). Skip the ORIGINAL CODE and BUG/FIX parts and use a
  PURPOSE summary instead.

The AI should auto-pick the mode per block: if a block already exists, use FIX MODE;
if it's brand new, use NEW MODE.

---

## THE PROMPT

```
You are fixing broken code AND/OR building new code. For EVERY function/route/block
you write, do NOT just drop the code in — annotate the file inline using this exact
format. Pick the mode per block automatically:

- FIX MODE  -> the block already exists (broken / needs change).
- NEW MODE  -> the block is brand new (building from scratch or a newly required
               function; there is no original and no bug).

----------------------------------------------------------------
FIX MODE (existing/broken code)
----------------------------------------------------------------
1. A banner comment naming the block:
   /* ===================================================================
      <NAME OF THE FUNCTION / ROUTE / BLOCK>
   =================================================================== */

2. The ORIGINAL code, fully COMMENTED OUT (so it does not run), under this label:
   // ----------------------- ORIGINAL CODE -----------------------
   // <original code, line by line, each prefixed with //>
   // <add short inline notes flagging each bug where it sits>

3. The UPDATED, working code (real, executable) under this label:
   // ----------------------- UPDATED CODE ------------------------
   <the actual fixed code here>

4. A clear closing boundary:
   // --------------------- END OF UPDATED CODE -------------------

5. Immediately after the boundary, a BUG / FIX summary, then a numbered
   HOW IT WORKS walkthrough, all as comments:
   // BUG: <1-2 lines: what was wrong in the original and why it failed>
   // FIX: <1-2 lines: what the updated code does instead>
   //
   // HOW IT WORKS:
   // 1. <plain-English step>
   // 2. <plain-English step>

6. Then 2-3 likely interview questions about THIS block, each with a short
   (1-2 sentence) answer, all as comments:
   // EXPECTED Q&A:
   // Q: <a question an interviewer might ask about this block>
   // A: <1-2 sentence answer>
   // Q: <another likely question>
   // A: <1-2 sentence answer>

----------------------------------------------------------------
NEW MODE (brand-new code — no original, no bug)
----------------------------------------------------------------
1. A banner comment naming the block:
   /* ===================================================================
      <NAME OF THE NEW FUNCTION / ROUTE / BLOCK>
   =================================================================== */

2. The NEW, working code (real, executable) under this label:
   // ------------------------- NEW CODE --------------------------
   <the actual new code here>

3. A clear closing boundary:
   // ---------------------- END OF NEW CODE ----------------------

4. Immediately after the boundary, a PURPOSE line (why this exists / what
   requirement it satisfies), then a numbered HOW IT WORKS walkthrough, all
   as comments:
   // PURPOSE: <1-2 lines: what this code is for / which requirement it meets>
   //
   // HOW IT WORKS:
   // 1. <plain-English step>
   // 2. <plain-English step>
   //
   // EXPECTED Q&A:
   // Q: <a question an interviewer might ask about this block>
   // A: <1-2 sentence answer>
   // Q: <another likely question>
   // A: <1-2 sentence answer>

RULES:
- In FIX MODE keep the original code as COMMENTS only — it must never execute.
- Only the UPDATED CODE / NEW CODE block is live/runnable.
- Do NOT fake an "ORIGINAL CODE" block for brand-new code — use NEW MODE instead.
- Keep BUG/FIX/PURPOSE to 1-2 lines each; keep HOW IT WORKS to short numbered steps.
- After the summary, add an EXPECTED Q&A section: 2-3 likely interview questions about
  that block, each with a 1-2 sentence answer.
- Apply this to every block you add or change; leave unchanged blocks alone.
- Preserve the surrounding code and the file's existing style.
- After writing, confirm the file still runs and any commented code has zero
  effect on execution.

Here is the existing code (if any — leave blank when starting from scratch):
<PASTE CODE HERE>

Here are the requirements:
<PASTE REQUIREMENTS HERE>
```

---

## TEMPLATE A — FIX MODE (existing/broken block)

```js
/* ===================================================================
   GET /tickets
=================================================================== */

// ----------------------- ORIGINAL CODE -----------------------
// app.get("/tickets", (req, res) => {
//   let result = tickets;                         // aliases shared array
//   if (req.query.status) {
//     result.filter(...)                          // return value discarded -> no-op
//   }
//   result.sort((a, b) => a.createdAt - b.createdAt);  // string subtraction -> NaN
//   res.json(result);
// });

// ----------------------- UPDATED CODE ------------------------
app.get("/tickets", (req, res) => {
  // ...real, working code...
  res.json(result);
});
// --------------------- END OF UPDATED CODE -------------------
// BUG: <what was wrong and why it failed>
// FIX: <what the updated code does instead>
//
// HOW IT WORKS:
// 1. <step>
// 2. <step>
//
// EXPECTED Q&A:
// Q: Why reassign `result = result.filter(...)` instead of just calling it?
// A: `.filter` is non-mutating; it returns a new array, so the result must be assigned.
// Q: Why copy the array before sorting?
// A: `.sort()` mutates in place, so copying with `[...tickets]` avoids changing the store.
```

## TEMPLATE B — NEW MODE (brand-new block)

```js
/* ===================================================================
   DELETE /tickets/:id   (newly required endpoint)
=================================================================== */

// ------------------------- NEW CODE --------------------------
app.delete("/tickets/:id", (req, res) => {
  const id = Number(req.params.id);
  const index = tickets.findIndex(t => t.id === id);
  if (index === -1) {
    return res.status(404).json({ error: `ticket ${id} not found` });
  }
  tickets.splice(index, 1);
  res.status(204).end();
});
// ---------------------- END OF NEW CODE ----------------------
// PURPOSE: Adds the newly required "delete a ticket" endpoint.
//
// HOW IT WORKS:
// 1. Convert the URL id to a number and find its array index.
// 2. If not found, return 404.
// 3. Otherwise remove it with splice and return 204 No Content.
//
// EXPECTED Q&A:
// Q: Why return 204 instead of 200?
// A: 204 No Content is the standard success code for a delete with no response body.
// Q: Why findIndex + splice instead of filter?
// A: splice removes in place by index; filter would rebuild the whole array unnecessarily.
```

---

## NOTES ON USING IT

- **Two modes, auto-selected:** FIX MODE for code that already exists, NEW MODE for
  brand-new functions/endpoints. Don't fake an "ORIGINAL CODE" block for new code.
- **Mixed tasks are fine:** in one file the AI can FIX some blocks and add others in
  NEW MODE — each block carries its own correct labels.
- **Language-agnostic:** swap the comment syntax for the target language —
  `#` for Python/Ruby/Bash, `--` for SQL/Lua, `/* */` or `//` for C/Java/Go/JS.
- **Keep it scoped:** the prompt says "leave unchanged blocks alone" so the AI
  doesn't rewrite parts that already work.
- **Good for interviews / reviews / teaching:** the reader sees the bug (or purpose),
  the code, the reasoning, and likely follow-up Q&A in one file without diffing versions.
- **EXPECTED Q&A prep:** each block ends with 2-3 questions an interviewer might ask plus
  short answers, so the file doubles as interview practice.
- **Want a diff instead of inline?** Add: "Also output a unified `+`/`-` diff of
  just the changed lines after the file."
```
