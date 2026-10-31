# Engineering State: ai-engineer-journey

- Target Role: Production AI / Machine Learning Systems Engineer
- Timeline: 24 Weeks (6 Months) @ 10 hours/week
- Current Phase: Month 1 (Production Microservice Plumbing & Containerization)
- Current Sprint: Week 1, Day 1 (concept hours start Mon 2 Nov 2026)
- Sprint Target: FastAPI Async Plumbing, Pydantic V2 Schemas & SSE Streaming

## Schedule (dated)
Weekday concepts: Mon–Thu, 1 hr/day. Build sprint: Sat/Sun, 6 hrs. Week N starts on the Monday below.

| Week | Starts (Mon) | Sprint (Sat–Sun) | Phase |
| :--- | :--- | :--- | :--- |
| 01 | 2 Nov 2026 | 7–8 Nov | 1 |
| 02 | 9 Nov | 14–15 Nov | 1 |
| 03 | 16 Nov | 21–22 Nov | 1 |
| 04 | 23 Nov | 28–29 Nov | 1 — **Gate 1** |
| 05–08 | 30 Nov – 21 Dec | ends 26–27 Dec | 2 — **Gate 2** (end Wk 8) |
| 09–14 | 28 Dec – 1 Feb 2027 | ends 6–7 Feb | 3 — **Gate 3** (end Wk 14) |
| 15–20 | 8 Feb – 15 Mar | ends 20–21 Mar | 4 — **Gate 4** (end Wk 20) |
| 21–24 | 22 Mar – 12 Apr | ends 17–18 Apr | 5 — **Gate 5** (capstone) |

Slippage rule: add one buffer weekend per month if a sprint overruns; shift later dates, never cut a deliverable.
(Dates are nominal; recompute from the actual start if Week 1 slips.)

## Phase Gates
A phase is passed only when ALL its criteria hold: deliverable runs, `uv run pytest` is green, work is committed, and this file is updated.

- [ ] **Gate 1 (Wk 4)**: Async FastAPI service in Docker (non-root, JSON logs, `/healthz`) streams LLM tokens with retries/timeouts and returns strict-schema JSON with per-request cost. Stretch: small asyncpg/Postgres job-status table (covers SQL gap from overview).
- [ ] **Gate 2 (Wk 8)**: Metrics library (P@K, R@K, MRR, PSI) + 50-example golden eval + LLM judge; GitHub Actions fails the build when accuracy < 90%.
- [ ] **Gate 3 (Wk 14)**: Hybrid RAG API (pgvector HNSW + GIN FTS + RRF + cross-encoder rerank) returning cited answers; retrieval p95 target < 300ms; 100% of claims cite retrieved chunks.
- [ ] **Gate 4 (Wk 20)**: MCP server/client + cyclic agent with Postgres checkpoints and HITL resume; vLLM/Ollama benchmarked; routing + semantic cache cuts cost. Demo: self-healing text-to-SQL agent.
- [ ] **Gate 5 (Wk 24)**: Flagship repo with `docker compose up --build`, README with architecture, p50/p95, eval scores, Langfuse tracing, injection tests, Locust report.

## Completed Milestones
- [x] Initialized Git repository with `uv` package manager and lockfile
- [x] Configured 24-week curriculum and `ROADMAP.md`
- [x] Established project directory skeleton

## In-Flight Tasks (Week 1 Checklist)
- [ ] Implement strict Pydantic V2 models (`InferenceRequest`, `InferenceResponse`) with `extra='forbid'`
- [ ] Build non-blocking async POST endpoint gated with `asyncio.Semaphore(5)`
- [ ] Build an SSE `StreamingResponse` endpoint yielding token chunks
- [ ] Write automated `pytest` test suite verifying validation (422) and streaming response formats

## Architectural Decisions & Standards
- Tooling: Python 3.12, `uv`, FastAPI, Pydantic V2, Docker (multi-stage)
- Core Rule: Async I/O for all remote calls; zero synchronous blocking inside routes
- Testing: No untested endpoints; pytest with `httpx.AsyncClient` required

## Blockers / Notes
- None. Ready for Week 1 Day 1 concept ingestion.
- **Docker in Week 1**: `Dockerfile` and `docker-compose.yml` are placeholders that will remain empty until Week 2 (multi-stage build). In Week 1, run FastAPI directly via `uv run`.