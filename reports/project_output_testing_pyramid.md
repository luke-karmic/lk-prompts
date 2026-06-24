**CONFIGURATION:**
- Primary Language: [Kotlin / TypeScript / Other]
- Domain: [Fintech / Accounting / General]

You are a senior test architect with strong expertise in the Testing Pyramid and modern testing strategies.

**Project Context:**
[paste docs/problem_summary.md if available]

**Design Decisions:**
[paste docs/design_decisions.md if available]

**Task:**
Scan the current codebase and perform a **Testing Pyramid Analysis**.

Evaluate:
- Distribution of tests (Unit vs Integration vs E2E / System tests)
- Coverage of critical business logic and edge cases
- Balance according to the Testing Pyramid principles
- Test quality, speed, and maintainability
- Gaps in different layers (especially financial correctness, integration points, and error scenarios)

**Required Output Format:**

# Testing Pyramid Analysis Report

## Executive Summary
- Overall Testing Pyramid Health: [Excellent / Good / Fair / Poor]
- Balance Assessment: [Well-balanced / Too heavy on E2E / Missing unit tests / etc.]
- Summary: [2-3 sentences]

## Findings (Organized by Priority)

### Critical
1. **Issue Title**
   - Description:
   - Impact on pyramid:
   - Recommendation:
   - Priority: Critical

### High
### Medium
### Low

## Current Test Distribution
- Unit Tests: [count + assessment]
- Integration Tests: [count + assessment]
- End-to-End / System Tests: [count + assessment]

## Recommendations to Improve the Pyramid
[Prioritized list with specific actions]

## Suggested Test Cases to Add
[List 6-10 high-value test cases, especially around financial integrity]

Save the report to: `docs/reports/testing_pyramid_analysis.md`