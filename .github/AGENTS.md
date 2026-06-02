# AGENTS.md — Mergington High School API

> **Single authoritative reference for all agents working in this repository.**
> Read this file fully before starting any task.

---

## Project Overview

**Mergington High School API** — a FastAPI application that lets students view and sign up for extracurricular activities. In-memory data store (no database).

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Language | Python 3.11+ |
| API framework | FastAPI |
| Server | Uvicorn |
| Testing | Pytest |
| Frontend | Vanilla JS + HTML (served as static files) |

---

## Repository Layout

```
src/
  app.py               # FastAPI app — all routes and in-memory data
  static/
    index.html         # Single-page frontend
    app.js             # Fetch-based frontend logic
    styles.css
tests/
  test_app.py          # All pytest tests (use TestClient from fastapi.testclient)
requirements.txt
pytest.ini
```

---

## Build & Test Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Run tests
pytest

# Run dev server
uvicorn src.app:app --reload
```

---

## Code Conventions

- All routes in `src/app.py` — do not create additional modules unless the issue explicitly requires it
- Raise `HTTPException` for all error responses; never return raw dicts for errors
- HTTP status codes: `404` for not found, `400` for bad input/business rule violations, `200` for success
- Tests use `fastapi.testclient.TestClient`; import the `app` object from `src.app`
- Test naming: `test_<function>_<condition>_<expected_outcome>` (e.g. `test_signup_when_full_returns_400`)
- No new libraries without explicit approval in the issue
- Write issues in business language first, then add a short technical context block with the exact file and function name.
- For BA-style issues, describe the user outcome, who is affected, and the rule that is being broken before naming any code.
- Keep technical context minimal but explicit so the agent can jump straight to the right function without guessing.

---

## Hard Stops

These are non-negotiable. Stop immediately and report to a human if any of these apply.

1. **Do not add a real database or file persistence** — the store is intentionally in-memory.
2. **Do not add authentication or session management** — out of scope for this project.
3. **Do not modify `requirements.txt` to add libraries** unless the issue explicitly lists the library name.
4. **Do not change the static file serving setup** (`/static` mount) unless the issue explicitly requires it.
5. **Do not commit secrets, tokens, or credentials** under any circumstances.
