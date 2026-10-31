# Engineering State: ai-engineer-journey

- Target Role: Production AI / Machine Learning Systems Engineer
- Timeline: 24 Weeks (6 Months) @ 10 hours/week
- Current Phase: Month 1 (Production Microservice Plumbing & Containerization)
- Current Sprint: Week 1, Day 1
- Sprint Target: FastAPI Async Plumbing, Pydantic V2 Schemas & SSE Streaming

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