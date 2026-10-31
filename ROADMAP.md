# 24-Week Production AI Systems Engineering Curriculum

## High-Level Timeline
- Weeks 01–04: Production Python, Microservice Plumbing & Containerization
- Weeks 05–08: Applied Statistics, Evaluation Harnesses (Evals) & Data Drift
- Weeks 09–14: High-Throughput Ingestion, Vector Databases & Hybrid RAG (RRF)
- Weeks 15–20: Agentic State Machines, Model Context Protocol (MCP) & Local Inference
- Weeks 21–24: System Hardening, Benchmarking & Production Capstone

## Sprint Tracking Matrix

| Week | Focus Area | Primary Deliverable |
| :--- | :--- | :--- |
| **01** | Async Python & FastAPI | Typed async endpoint with Pydantic validation & SSE streaming |
| **02** | Docker & Observability | Hardened multi-stage container emitting structured JSON logs |
| **03** | Upstream SDK Integration | Non-blocking LLM proxy with automated retries and timeouts |
| **04** | Constrained Decoding | Strict JSON schema extraction with cost and token accounting. Stretch (~2h): asyncpg + Postgres job-status table |
| **05** | Applied Statistics | Standalone metrics library (Precision@K, Recall@K, MRR, PSI) |
| **06** | Golden Evals & Datasets | 50-example benchmark test harness with deterministic assertions |
| **07** | Model-as-a-Judge | Automated LLM evaluation rubric measuring factual grounding |
| **08** | CI/CD Evaluation Gates | GitHub Actions workflow blocking builds on accuracy regressions |
| **09** | Document Ingestion | Structural Markdown chunking pipeline preserving rich metadata |
| **10** | PostgreSQL `pgvector` | HNSW-indexed vector store running cosine similarity queries |
| **11** | Lexical Search (BM25) | GIN-indexed PostgreSQL full-text search with ranking functions |
| **12** | Hybrid Search & RRF | Unified SQL query merging vector and text search via RRF |
| **13** | Re-Ranking Pipelines | Two-stage retrieval system with cross-encoder candidate re-scoring |
| **14** | Grounded RAG & Citations | End-to-end RAG service with strict source-grounded citations; retrieval p95 < 300ms |
| **15** | Function Calling Loops | Sandboxed tool-execution loop with model self-healing |
| **16** | Model Context Protocol | Standardized MCP client-server architecture over STDIO/SSE; read-only text-to-SQL tools (schema inspector, SQL executor) |
| **17** | Agent State Machines | Cyclic graph agent with dynamic routing and state persistence |
| **18** | Human-in-the-Loop | Stateful agent pause/resume flow with PostgreSQL checkpoints |
| **19** | Local Model Serving | Self-hosted vLLM/Ollama engine benchmarked under load |
| **20** | Routing & Semantic Cache | Tiered query gateway with vector-based semantic response caching; Gate 4 demo: self-healing text-to-SQL MCP agent |
| **21** | Distributed Telemetry | End-to-end Langfuse tracing tracking spans, latencies, and costs |
| **22** | AI Application Security | Pre-flight injection guardrails and hardened read-only tool roles |
| **23** | Concurrency Load Testing | Locust test suite validating connection pools and concurrency |
| **24** | Capstone Hardening | Production-grade repository with one-command Docker launch |

## Decisions & Targets
- **SQL stretch task (Week 04):** the curriculum has no SQL week before Week 10, so add a small asyncpg + Postgres job-status table (practise window functions, CTEs, indexes). Optional, ~2 hours.
- **Retrieval latency target (Weeks 12–14):** p95 < 300ms for hybrid RRF retrieval plus re-rank. Benchmark it at Week 12, re-check at Weeks 13 and 14.
- **MCP text-to-SQL demo (Weeks 15–20):** natural language to validated read-only SQL via the MCP server (Week 16), wrapped in the self-healing tool loop (Week 15) and the state-machine agent with Postgres checkpoints (Weeks 17–18). Demonstrated at Gate 4 (Week 20); candidate capstone flagship alongside the Hybrid RAG engine.
- **Phase gates and dated schedule:** see `state.md`.
