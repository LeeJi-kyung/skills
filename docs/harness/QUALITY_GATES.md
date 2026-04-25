# Quality Gates

Use these gates to keep speed without losing the demo.

## Before Parallel Build
- `ARCHITECTURE.md` has product, demo path, first API contract, env table.
- Each team member has an owned branch.
- The happy path can be described in under 30 seconds.

## Frontend Gate
- Main route renders without backend by using loading, empty, or mock-safe states.
- All API calls go through the shared API client.
- User can recover from API failure.
- Primary viewport looks presentable at desktop and mobile widths.

## Backend Gate
- `/health` returns the standard API envelope.
- All responses follow `{ data, error, status }`.
- Pydantic validates request and response shapes.
- CORS allows local frontend and deployed Vercel URL.
- Secrets are only read from env.

## Integration Gate
- Frontend points to `NEXT_PUBLIC_API_URL`.
- Backend accepts frontend origin.
- One happy path works with real API calls.
- `scripts/smoke` passes or documents the exact blocker.

## Deploy Gate
- `scripts/deploy-check` passes.
- Vercel env vars are set.
- Railway env vars are set.
- Production `/health` responds.
- Demo seed data exists or the app has a no-data fallback.

## Demo Gate
- One primary story is rehearsed.
- Fallback path exists: screenshots, seeded data, or local run.
- Risky unfinished features are hidden.
- Presenter knows the exact first click, final result, and recovery line.

## Failure Recovery
- Build failure: run `scripts/verify`, fix the first root cause only.
- API contract failure: update `ARCHITECTURE.md`, then FE/BE code.
- Deploy failure: keep local demo ready while one person fixes deploy.
- UI failure: reduce scope to the happy path and hide broken surfaces.
- Agent loop: stop after 3 failed iterations and ask a human for the missing decision.

