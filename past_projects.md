# Engineering Project Stories

---

# Reya DEX – Real-time Frontend & WebSocket Optimization

**Category:** Frontend Performance & Real-time Systems

## Situation

During my consulting role at Karmic working on Reya DEX (~$10bn daily trading volume), the frontend experienced severe performance degradation under market volatility. Trade executions took 5–10+ seconds due to combined frontend and backend issues, resulting in poor UX.

Additional problems included:

* High CPU usage
* Memory leaks
* Unreliable WebSocket connections causing stale or inconsistent data
* Incorrect calculation formulas in certain scenarios
* Frequent data misalignment during releases because business logic existed in multiple frontend and backend code paths

## Task

Dramatically improve real-time performance, reliability, consistency, and user experience while supporting extreme trading volumes.

## Actions

* Revamped the WebSocket layer across frontend and backend with robust reconnection logic, exponential backoff, and efficient message handling.
* Worked closely with the quant team to consolidate all trading formulas into a shared package used by both frontend and backend.
* Implemented aggressive throttling and debouncing to reduce unnecessary React re-renders.
* Applied heavy memoization using `React.memo`, `useMemo`, and `useCallback`.
* Introduced React Query for caching and synchronization while eliminating expensive HTTP polling.
* Performed extensive profiling using Chrome DevTools and React Profiler.
* Removed thread-blocking operations from critical rendering paths.
* Collaborated on backend optimizations including removing unnecessary smart contract simulations, reducing execution latency by approximately one second.

## Results

* Trade execution became near real-time.
* Stable and reliable WebSocket communication.
* Significant CPU and memory improvements.
* Eliminated memory leaks.
* Fully consistent trading calculations.
* Dramatically improved user experience during periods of market volatility.

## Nuances

This required balancing data freshness against rendering performance while supporting highly volatile market conditions across desktop and mobile clients. The project demonstrates deep frontend performance optimization combined with backend collaboration.

---

# Bitvavo – Kafka Microservices for Real-time Event Processing

**Category:** Event-Driven Architecture & Distributed Systems

## Situation

As Technical Lead for Growth at Bitvavo, the Growth domain processed millions of real-time events across more than 150 crypto assets using a fragile AWS Lambda architecture.

Key challenges included:

* Sliding price windows
* Volatility calculations
* Watchlist matching
* Large-scale notification delivery
* Reliability during periods of extreme market volatility

## Task

Design four specialized Kafka microservices capable of processing millions of events with:

* Exactly-once processing
* 100% delivery guarantees
* No duplicate notifications
* Approximately five-second end-to-end latency
* Automatic failover

## Actions

* Built four Node.js (NestJS) microservices:

  * Real-time Pricing Sliding Window
  * Volatility Calculation Service
  * Watchlist Matching Service
  * CRM Notification Delivery Service
* Implemented Kafka transactional processing with idempotency keys and dead-letter queues.
* Introduced KEDA autoscaling based on Kafka backpressure.
* Performed large-scale load testing using K9.
* Added full observability with ELK, Prometheus, and Sentry.
* Coordinated architecture and delivery across four engineering teams.

## Results

* Successfully processed millions of events daily.
* Delivered five million notifications with 100% delivery.
* Generated seven-figure annual revenue through engagement campaigns.
* Improved scalability, reliability, and operational visibility.

## Nuances

The project required careful handling of Kafka partition rebalancing, exactly-once semantics, throughput trade-offs, and consistency across distributed services.

---

# AI RAG System for Law Firm

**Category:** AI Engineering & LLM Integration

## Situation

A law firm spent hours manually reviewing large collections of legal documents including contracts, PDFs, transcripts, and case files.

## Task

Build a production-ready AI system capable of understanding legal documents, generating questionnaires, extracting conclusions, and significantly reducing review time.

## Actions

* Built a Python LangChain Retrieval-Augmented Generation (RAG) pipeline.
* Used Pinecone as the vector database.
* Designed a multi-agent architecture using LangGraph.
* Implemented hierarchical indexing and context compression.
* Optimized token usage and retrieval quality.
* Added LangSmith tracing and evaluations.
* Integrated OCR for scanned documents.
* Automated workflows using n8n.
* Built a React frontend for lawyer interaction.

## Results

* Reduced case review from hours to minutes.
* Estimated 60–80% reduction in manual review effort.
* Improved consistency across legal analysis.
* Generated actionable summaries and questionnaires automatically.

## Nuances

Special attention was given to hallucination mitigation, document grounding, legal privacy requirements, and secure handling of sensitive client information.

---

# Bitvavo – Growth Domain Migration (AWS Lambda → Kubernetes)

**Category:** System Migration & Technical Leadership

## Situation

The Growth domain at Bitvavo—including referrals, campaigns, and notifications—was built entirely on AWS Lambda, creating operational challenges around orchestration, debugging, observability, and scalability.

## Task

Lead the migration of the entire Growth platform to Kubernetes over two quarters while continuing to deliver business features.

## Actions

* Planned the migration using the Strangler Fig pattern.
* Built and deployed more than seven Node.js/TypeScript microservices.
* Introduced Kubernetes with OPA authorization.
* Migrated event processing to Kafka.
* Added Prometheus, Grafana, ELK, and Sentry.
* Led engineering growth from zero to thirteen team members.

## Results

* Completed migration with no major production incidents.
* Enabled high-revenue notification systems.
* Improved deployment velocity.
* Increased scalability, maintainability, and reliability.

## Nuances

The migration required running hybrid infrastructure during transition while maintaining zero downtime and uninterrupted feature delivery.

---

# AI Conversational Trading Assistant for Crypto Exchange

**Category:** AI Engineering, RAG & LLM Integration

## Situation

A cryptocurrency exchange wanted to validate an AI-powered assistant that could improve onboarding, reduce support workload, and increase trading engagement without introducing unnecessary security or regulatory risk.

Rather than building a fully autonomous trading agent, the MVP focused on conversational capabilities backed by live exchange data and trusted documentation.

## Task

Design and build a conversational AI assistant capable of:

* Answering market questions
* Explaining trading concepts
* Summarizing user portfolios
* Handling support requests
* Guiding users through trades

The solution needed to be secure, production-ready, and easily expandable.

## Actions

* Designed a Python LangChain architecture using Retrieval-Augmented Generation (RAG).
* Integrated exchange APIs for:

  * Live market prices
  * Portfolio balances
  * Open positions
  * Trading history
  * Market statistics
* Implemented intent classification to route requests to:

  * Market data
  * Portfolio
  * Support
  * Educational content
  * Trading workflows
* Indexed documentation, FAQs, educational material, and compliance policies in a vector database (Pinecone or FAISS).
* Combined structured API responses with retrieved documentation before passing context to the LLM.
* Designed guided trading flows requiring explicit confirmation before order submission.
* Added conversation memory, watchlists, user preferences, and price alerts.
* Implemented LangSmith tracing, prompt evaluation, and observability.
* Added AI guardrails, audit logging, financial disclaimers, and hallucination mitigation.

## Results

* Delivered an AI assistant capable of:

  * Real-time market insights
  * Portfolio summaries
  * Automated customer support
  * Educational explanations
  * Guided trade execution
* Created a scalable foundation for future AI-powered features.
* Reduced implementation risk by limiting the MVP to read-only capabilities while validating customer demand.

## Nuances

The architecture deliberately separated deterministic API data from semantic retrieval.

* Real-time prices and portfolio information always came directly from exchange APIs.
* Documentation and knowledge retrieval were handled through the RAG pipeline.
* The LLM acted as an orchestrator rather than the source of truth.
* Trade execution required explicit user confirmation.
* Security, compliance, observability, and hallucination prevention were built into the architecture from day one.
