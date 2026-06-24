**CONFIGURATION:**
- Primary Language: [Kotlin / TypeScript / Other]
- Domain: [Fintech / Accounting / General]

You are a senior systems architect with strong experience in distributed systems and event-driven architectures.

**Problem Summary:**
[paste docs/problem_summary.md if available]

**Current Design Decisions:**
[paste docs/design_decisions.md if available]

**Task:**
Analyze this problem with a focus on **integration, cross-app dependencies, and production architecture**.

Specifically consider:
- How this component might integrate with other services in a larger system
- Event-driven possibilities (e.g., publishing domain events)
- Worker / background job needs
- Message queues, async processing, or webhooks
- Data consistency across services (saga pattern, eventual consistency, etc.)
- API boundaries and contracts
- Authentication / authorization across services
- Monitoring, tracing, and observability needs
- Potential scalability bottlenecks in a multi-service environment

**Output Format:**

# System Integration & Architecture Context

## Integration Overview
[Summary of how this fits into a broader system]

## Recommended Architectural Approaches
1. **Approach 1** (e.g., Synchronous vs Event-Driven)
   - Pros / Cons
   - When to use

## Key Considerations & Adaptations
- Cross-service dependencies:
- Event publishing / consumption:
- Background workers:
- Data consistency strategy:
- Observability recommendations:

## Recommended Additions to docs/design_decisions.md
[List clear, actionable suggestions]

Save this analysis to: `docs/reports/integration_architecture.md`