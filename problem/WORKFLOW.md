# Master Workflow — Interview Challenge Lifecycle

This is the top-level rule that ties the three prompt files together. Follow this
order for every interview challenge. Each step names which prompt file's rules apply.

Prompt files used:
- `SOLVE_PROMPT.md`      — pre-solution analysis (clarify → type → idea → optimal)
- `FORMATTING_PROMPT.md` — code annotation format (ORIGINAL/UPDATED or NEW + summary + Q&A)
- `ANSWER_PROMPT.md`     — short interview answers (per-question)

Output files:
- the code file(s)        — REAL runnable file(s) (`server.js`, `main.py`, etc.);
                            this is where the actual code lives and runs
- `CHALLENGE_SOLUTION.md` — overall write-up (analysis + short code summary + Q&A);
                            NO actual code; resets PER CHALLENGE
- `INTERVIEW_ANSWERS.md`  — single current answer; resets PER QUESTION

---

## THE LIFECYCLE

### Step 1 — Challenge given → ANALYZE (use SOLVE_PROMPT.md)
User provides the overall challenge. Produce the 4-section analysis:
clarifying questions, problem type, solution idea, optimal approach.
Be clear, concise, smart, short. Write this into `CHALLENGE_SOLUTION.md`.
DO NOT write code yet.

### Step 2 — Interviewer clarifies → BUILD/UPDATE CODE (use FORMATTING_PROMPT.md)
User relays the interviewer's answers to the clarifying questions from Step 1.
With those answers, fully build or update the code in its REAL, RUNNABLE FILE
(`server.js`, `main.py`, etc. — a real file to build and run, like this project),
following FORMATTING_PROMPT (ORIGINAL/UPDATED for existing code, NEW CODE for new;
each block gets BUG/FIX or PURPOSE + HOW IT WORKS + EXPECTED Q&A).
In `CHALLENGE_SOLUTION.md` record only a SHORT summary/reference (what changed and
why, the filename) — NEVER paste the actual code there.

### Step 3 — Submit → ANSWER FOLLOW-UPS (use ANSWER_PROMPT.md)
User submits, interviewer asks follow-up questions. For EACH question, write the
answer to BOTH files:
- `INTERVIEW_ANSWERS.md` — current answer ONLY (reset/overwrite each question).
- `CHALLENGE_SOLUTION.md` — APPEND the full Q&A to a running "Q&A" section.
  NEVER reset/overwrite this mid-challenge; it accumulates every question + answer
  so the full record can be saved. It is only wiped at Step 4 (passed).
Answer under ANSWER_PROMPT rules: 1-3 sentences (longer only if required).

### Step 4 — Passed → RESET + CLEAN CODE
When the user says the challenge is "passed" / "over" / "next" (or similar):
1. ERASE both `CHALLENGE_SOLUTION.md` and `INTERVIEW_ANSWERS.md`.
2. CLEAN THE CODE FILE(S): strip ALL annotations — remove the ORIGINAL CODE blocks,
   the banner/boundary comments, the BUG/FIX (or PURPOSE) summaries, and the
   EXPECTED Q&A. Leave ONLY the clean, final working code.
   (Those annotations exist only WHILE the task is in progress; once passed, the
   codebase keeps just the updated code.)
Ready for a new challenge → go back to Step 1.

### Step 4b — Not satisfied / new situation → LOOP BACK TO CODE
If the interviewer is NOT satisfied or introduces new situations/requirements,
DO NOT reset. Loop back to Step 2 (the build/update-code step) using
FORMATTING_PROMPT rules, then continue to Step 3 again.

---

## QUICK MAP

| Trigger | Step | Prompt | Files touched |
|---|---|---|---|
| Challenge given | 1 Analyze | SOLVE_PROMPT | CHALLENGE_SOLUTION.md |
| Interviewer clarifies | 2 Build/Update code | FORMATTING_PROMPT | code, CHALLENGE_SOLUTION.md |
| Interviewer asks questions | 3 Answer | ANSWER_PROMPT | INTERVIEW_ANSWERS.md (overwrite), CHALLENGE_SOLUTION.md (append Q&A) |
| "passed" / "next" / "over" | 4 Reset + Clean code | — | erase both output files; strip code annotations |
| Not satisfied / new situation | 4b Loop | FORMATTING_PROMPT | back to Step 2 |

---

## RULES

- **Order matters:** never skip ahead to code before Step 1's analysis, and never
  write code in Step 1.
- **Reset periods differ:** `INTERVIEW_ANSWERS.md` resets per question (Step 3);
  `CHALLENGE_SOLUTION.md` resets per challenge (Step 4 only).
- **Full Q&A is recorded:** every follow-up answer goes to BOTH files — overwritten in
  `INTERVIEW_ANSWERS.md`, but APPENDED (never reset) into the running Q&A section of
  `CHALLENGE_SOLUTION.md` so the complete history survives until the challenge passes.
- **Annotations are in-progress only:** ORIGINAL CODE, BUG/FIX summaries, and EXPECTED
  Q&A live in the code file ONLY during the task. On "passed", strip them so the
  codebase keeps just the clean updated code.
- **Only "passed"/"next"/"over" triggers a reset.** Dissatisfaction or new
  requirements never reset — they loop to Step 2.
- **Code lives in its real file:** the actual code always goes in the runnable file
  (`server.js`, `main.py`, ...) to build and run — NEVER pasted into
  `CHALLENGE_SOLUTION.md`, which only references it with a short summary.
- **Keep it tight everywhere:** clear, concise, smart, short — the senior signal.
