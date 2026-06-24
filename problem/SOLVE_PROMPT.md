# Reusable Prompt — Senior-Level Interview Problem Solving Guide

Copy the prompt below into any AI tool. For ANY coding interview problem, it forces a
clear pre-solution analysis FIRST (so the interviewer sees lead-engineer-level thinking)
and only THEN updates the code.

---

## THE PROMPT

```
You are helping me solve a coding interview problem at a LEAD ENGINEER level. Before
writing or updating ANY code, you MUST answer the four sections below, in order. Only
after that may you implement the solution.

STYLE (most important): Be CLEAR, CONCISE, SMART, and SHORT. Every line must earn its
place — no filler, no hedging, no restating the question. Senior signal = saying the
right thing in the fewest words. If a section can be one line, make it one line.

1. CLARIFYING QUESTIONS
   List the key questions I should ask the interviewer before coding (input size/range,
   edge cases, duplicates, sorted or not, empty input, return shape, time/space limits,
   in-place vs new, concurrency/IO if relevant). 3-6 sharp questions, no filler.

2. PROBLEM TYPE
   Name the pattern: sliding window, two pointers, dynamic programming, graph (BFS/DFS),
   greedy, binary search, hashing, heap/priority queue, backtracking, etc. State which
   and the ONE signal in the prompt that points to it.

3. SOLUTION IDEA (in a few simple words)
   Explain the core idea in 1-3 plain sentences — the insight, not the code.

4. OPTIMAL APPROACH
   Give the optimal approach with its time and space complexity (Big-O), and briefly
   why it's optimal (what the naive version costs and what this saves).

THEN (and only then): implement / update the code, following any code-formatting rules
I've given you. Keep the analysis tight and confident — this is to show proficiency, so
be precise, not verbose.

CHALLENGE SUMMARY FILE: Keep the overall write-up for the challenge in ONE unique file:
CHALLENGE_SOLUTION.md.
- RESET PERIOD = PER CHALLENGE, not per question. Within the SAME challenge, keep
  updating/appending this file as we solve each part/question. When a NEW challenge
  starts, WIPE it and start fresh.
- Finalize it once the challenge is fully solved. It should hold the complete answer
  for the current challenge: the 4-section analysis above, the solution/code summary,
  and the Q&A.

Here is the problem:
<PASTE PROBLEM HERE>

Here is the current code (if any):
<PASTE CODE HERE>
```

---

## TEMPLATE (what the answer should look like)

```md
### 1. Clarifying questions
- <question about input size / range>
- <question about edge cases / duplicates / empty>
- <question about expected output shape>
- <question about constraints (time/space, in-place)>

### 2. Problem type
<Pattern name> — signaled by "<the phrase in the prompt that gives it away>".

### 3. Solution idea
<1-3 plain sentences: the core insight.>

### 4. Optimal approach
<Approach in 2-4 sentences.> Time: O(...), Space: O(...). Optimal because the naive
way is O(...) and this avoids <the redundant work>.

--- then the code ---
```

---

## NOTES

- **Clear, concise, smart, short** — this is the #1 rule. One line per point when
  possible; cut every word that isn't load-bearing.
- **Analysis before code, always** — the four sections come first so the interviewer
  sees the thought process, not just a finished answer.
- **Tight, not verbose** — senior signal is precision: short questions, named pattern,
  one-line insight, Big-O with justification.
- **Name the signal** — saying *why* a problem is "sliding window" (e.g. "longest
  substring / subarray with a constraint") shows pattern recognition, not memorization.
- **Always include Big-O** — and contrast with the naive cost; that's the lead-engineer
  tell.
- **Then follow code rules** — after the analysis, apply the formatting prompt
  (ORIGINAL/UPDATED or NEW CODE + summary + EXPECTED Q&A).
- **Challenge write-up resets per challenge** — `CHALLENGE_SOLUTION.md` holds the whole
  challenge (analysis + code summary + Q&A), updated across its questions and wiped
  fresh when a new challenge begins. (Contrast: `INTERVIEW_ANSWERS.md` resets per
  question.)
```
