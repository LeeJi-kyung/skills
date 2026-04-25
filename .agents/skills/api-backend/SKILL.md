---
name: api-backend
description: Use for FastAPI routes, Pydantic schemas, Supabase access, CORS, health checks, and backend error envelopes.
---

# API Backend

## Defaults
- FastAPI app entrypoint: `backend/main.py`.
- Routes: `backend/app/api`.
- Schemas: `backend/app/schemas`.
- Services: `backend/app/services`.
- Data access: `backend/app/repositories`.

## Required Patterns
- Every response uses `{ data, error, status }`.
- Every request body uses Pydantic.
- Database access is isolated from route handlers.
- Secrets come from env only.
- CORS includes local frontend and deployed Vercel URL.
- `/health` must not depend on optional external services unless documented.

## Error Shape
```json
{
  "data": null,
  "error": {
    "code": "STRING_CODE",
    "message": "Safe message"
  },
  "status": "error"
}
```

## Do Not
- Do not return raw database rows directly.
- Do not log secrets, tokens, or user private content.
- Do not add a dependency without a clear demo-path reason.
- Do not silently change response fields without `ARCHITECTURE.md`.

## Verify
```bash
cd backend
uv run ruff check .
uv run pytest -q
```

