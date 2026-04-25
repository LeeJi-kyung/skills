# Operating Model

This is the team playbook for the 8-hour hackathon.

## Timebox
| Time | Goal | Output |
| --- | --- | --- |
| 0:00-0:20 | Topic lock | Product promise, target user, demo path |
| 0:20-0:40 | Contract lock | Completed `ARCHITECTURE.md` |
| 0:40-1:00 | Repo boot | Env checklist, branches, deploy shells |
| 1:00-4:30 | Parallel build | FE, BE, integration slices |
| 4:30-5:30 | Integration | API connected, smoke path working |
| 5:30-6:30 | Polish | UI, speed, error states, seed data |
| 6:30-7:15 | Deploy | Vercel/Railway production URLs |
| 7:15-8:00 | Demo | Script, fallback, final smoke |

## Team Roles
- Frontend owner: UI, primary flow, shadcn components, client API wrapper.
- Backend owner: FastAPI routes, schemas, data access, service logic.
- Integration/demo owner: env, deploy, smoke tests, seed data, presentation path.

Each owner can use agents, but the owner remains responsible for contract accuracy.

## Branches
- `main`: deployable only.
- `feat/frontend`: frontend owner.
- `feat/backend`: backend owner.
- `feat/integration`: integration and demo owner.
- Short fixes: `fix/<issue>`.

## PR Rules
- Prefer small PRs that preserve the demo path.
- PR description must include changed contract, verification run, and known risk.
- Blocking checks: contract mismatch, broken build, broken smoke path, leaked secret.
- Non-blocking checks: naming polish, refactor preference, minor visual tuning.

## Merge Freeze
- At 6:30, stop feature work.
- Only merge deploy fixes, demo path fixes, and severe visual bugs.
- If a feature is not on the happy path by freeze, hide it.

## Conflict Protocol
1. Use `ARCHITECTURE.md` as the source of truth.
2. Preserve the other owner's intent.
3. If both sides changed the contract, stop and update the contract first.
4. Prefer the smaller change that restores the demo path.

## Agent Routing
- Planning or scope: `planner`.
- UI and interaction: `frontend-builder`.
- API, schema, data: `backend-builder`.
- Env, smoke, end-to-end checks: `integration-tester`.
- Merge readiness: `reviewer`.
- Presentation and fallback: `demo-coach`.

