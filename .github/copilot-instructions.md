# GitHub Copilot — Repository Instructions

> Read [AGENTS.md](AGENTS.md) before starting any task. It contains project description, tech stack, build/test commands, code conventions, and Hard Stops. Hard Stops are non-negotiable.

## Standards

| Standard | Applies To |
|----------|-----------|
| FastAPI route conventions | All new/modified endpoints in `src/app.py` |
| HTTPException error handling | All error responses |
| Pytest + TestClient | All automated tests in `tests/test_app.py` |
| Vanilla JS fetch pattern | All frontend changes in `src/static/app.js` |

## Core Principles

- **Correctness over brevity.** Never sacrifice correct error handling for shorter code.
- **Consistency.** Follow patterns already in `src/app.py` — do not introduce new patterns without justification.
- **No silent failures.** All error paths must raise `HTTPException` with an appropriate status code and detail message.
- **Minimal scope.** Only change what the issue requires. Do not refactor unrelated code.

## How to Apply

1. Read `AGENTS.md` first — every time, without exception.
2. For new routes: follow the existing route signature pattern in `src/app.py`.
3. For tests: use `TestClient`, match the naming convention, and mock nothing — the in-memory store is the test environment.
4. For frontend changes: follow the existing `fetch()` pattern in `src/static/app.js`.
5. After any change: run `pytest` — all tests must pass before declaring complete.
