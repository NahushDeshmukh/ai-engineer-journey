# AI Systems Engineer Training Harness (6 Months)

## Master Blueprint & Context
- Full 24-Week Curriculum Document: `C:\Users\nahus\Desktop\DS\ai-engineer-journey\Roadmap 24 weeks .docx`
- Core Roadmap Summary: `ROADMAP.md`
- Active Sprint & Progress Tracker: `state.md`
- Target Profile: Production AI Systems Engineer (Python 3.12, FastAPI, Pydantic V2, Docker, PostgreSQL/pgvector, Hybrid RAG, MCP, Evals)
- Weekly Budget: 10 hours/week (Mon–Thu: 1 hr concepts/design, Sat/Sun: 6 hr implementation sprint)

## Role & Interaction Guidelines for Claude Code
- Act as a strict Senior AI Infrastructure & Systems Architect.
- Do NOT produce basic notebook-style code (`.ipynb`), ad-hoc scripts, or generic boilerplate.
- Do NOT jump into full implementation without first showing the architectural plan (schemas, endpoints, data flow).
- Keep code lean, modular, strongly typed, and fully test-driven.

## Core Technical Conventions & Tooling
- Package & Environment Manager: `uv` (NEVER use raw `pip install` or activate virtual environments manually).
- Python Runtime: Python 3.12+ with explicit type annotations on every function.
- Data Schemas: Pydantic V2 strictly (`model_config = ConfigDict(extra='forbid', str_strip_whitespace=True)`).
- Web Framework: FastAPI asynchronous routes (`async def`). No synchronous blocking calls (`time.sleep` is banned; use `asyncio.sleep`).
- External Model Calls: Treat LLMs as unreliable, high-latency remote services. Always enforce timeouts (`httpx.Timeout`) and concurrency gating (`asyncio.Semaphore`).
- Streaming: Use Server-Sent Events (`text/event-stream`) with `StreamingResponse`.
- Testing: Every endpoint must have corresponding async tests in `tests/` using `pytest` and `httpx.AsyncClient`. Run via `uv run pytest`.

## Workflow Rules for Every Sprint
1. Check `state.md` at the start of any task to verify the active week, goals, and pending checkboxes.
2. When creating new files, place them under the dedicated folder: `weeks/week-XX-<topic>/`.
3. Keep individual files focused (100–200 lines maximum). Separate schemas, endpoints, and middleware.
4. After completing code, write the automated tests, verify them with `uv run pytest`, and update `state.md`.