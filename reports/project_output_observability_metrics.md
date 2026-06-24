**CONFIGURATION:**
- Primary Language: [Kotlin / TypeScript / Other]
- Metrics Technology Preference: [Prometheus / OpenTelemetry / Custom / None]

You are a senior observability engineer.

**Problem Summary:**
[paste docs/problem_summary.md]

**Design Decisions:**
[paste docs/design_decisions.md]

**Task:**
Analyze the current project and generate a prioritized metrics report based on the business logic.

Focus on:
- Key business metrics (financial transactions, reconciliation, errors, latency, etc.)
- Operational metrics (CPU, memory, request rates, queue depths)
- Error rates and success rates
- Business-specific KPIs

**Output Format:**

# Metrics Recommendations Report

## Executive Summary
[Overall observability posture and recommendations]

## Prioritized Metrics (Ranked by Importance)

### Critical / High Priority
1. **Metric Name** (e.g., `transactions_processed_total`)
   - Type: Counter / Gauge / Histogram
   - Description:
   - Why important:
   - How to use / Alert on:
   - Watch-outs / Pitfalls:

### Medium Priority
...

### Low Priority
...

## Implementation Recommendations
- Recommended technology: [Prometheus + Grafana, OpenTelemetry, etc.]
- Instrumentation approach:
- Key labels / dimensions to add:

Save this report to: `docs/reports/metrics_recommendations.md`