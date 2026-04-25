# Architecture Contract

Fill this in during the first 20 minutes after the topic is chosen. Frontend and backend work must not diverge from this file.

## Product
- Name: [FILL]
- One-line promise: [FILL]
- Target user: [FILL]
- Pain point: [FILL]
- Demo happy path:
  1. [FILL]
  2. [FILL]
  3. [FILL]

## Stack
- Frontend: Next.js App Router, TypeScript, Tailwind CSS, shadcn/ui
- Backend: FastAPI, Python, Pydantic
- Data: Supabase PostgreSQL, optional Supabase Auth
- Deploy: Vercel + Railway

## Repository Boundaries
- `frontend/`: UI, routes, client API wrapper, browser-only state
- `backend/`: API routes, Pydantic schemas, data access, service logic
- `docs/`: product, architecture, harness, demo notes
- `scripts/`: deterministic verification commands

## API Envelope
All backend responses must use:

```json
{
  "data": {},
  "error": null,
  "status": "ok"
}
```

Error responses must use:

```json
{
  "data": null,
  "error": {
    "code": "STRING_CODE",
    "message": "Human readable message"
  },
  "status": "error"
}
```

## API Contract
| Method | Path | Owner | Request | Success data | Errors | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| GET | `/health` | Backend | none | `{ "status": "healthy" }` | none | Required before deploy |
| [FILL] | [FILL] | [FILL] | [FILL] | [FILL] | [FILL] | [FILL] |

## Data Model
| Entity | Fields | Source of truth | Notes |
| --- | --- | --- | --- |
| [FILL] | [FILL] | Supabase | [FILL] |

## Frontend Contract
- Primary route: [FILL]
- Primary user action: [FILL]
- API client location: `frontend/src/lib/api`
- Loading state: every async user action shows visible progress
- Error state: every failed API call shows a recoverable message

## Backend Contract
- FastAPI app entrypoint: `backend/main.py`
- Routers live under: `backend/app/api`
- Pydantic schemas live under: `backend/app/schemas`
- Supabase access lives under: `backend/app/repositories`
- Business logic lives under: `backend/app/services`

## Environment Variables
| Name | Owner | Required for local | Required for deploy | Notes |
| --- | --- | --- | --- | --- |
| `NEXT_PUBLIC_API_URL` | FE | yes | yes | Railway backend URL |
| `NEXT_PUBLIC_SUPABASE_URL` | FE | if auth/data used | if auth/data used | Public Supabase URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | FE | if auth/data used | if auth/data used | Public anon key |
| `DATABASE_URL` | BE | if DB used | if DB used | Prefer Supabase pooled URL |
| `SUPABASE_URL` | BE | if Supabase used | if Supabase used | Server-side Supabase URL |
| `SUPABASE_SERVICE_KEY` | BE | if privileged access used | if privileged access used | Never expose to frontend |
| `CORS_ORIGINS` | BE | yes | yes | Comma-separated origins |

## Contract Change Protocol
1. Update this file first.
2. State which owner is affected.
3. Update tests or smoke checks if the demo path changes.
4. Announce the change before merging.

