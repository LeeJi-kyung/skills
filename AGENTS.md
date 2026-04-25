# Hackathon Agent Harness

Codex project map for an 8-hour Vibe Coding Hackathon.

## Mission
- Track: Business & Applications
- Team size: 3
- Default stack: Next.js + FastAPI + Supabase
- Deploy: Vercel for frontend, Railway for backend
- Skill policy: Curated Minimal. Do not bulk-install third-party skills.

## Core Rule
Humans steer. Agents execute inside explicit contracts.

Before parallel work starts, fill `ARCHITECTURE.md`. If the contract changes, update it in the same PR.

## Where To Look
- `ARCHITECTURE.md`: API, data, env, frontend/backend boundaries
- `docs/harness/OPERATING_MODEL.md`: timeline, roles, branches, merge rules
- `docs/harness/QUALITY_GATES.md`: verification gates and recovery paths
- `.agents/skills/`: Codex-compatible reusable workflows
- `.codex/README.md`: Codex setup notes for this template
- `scripts/`: deterministic checks agents should run

## Default Work Split
- Frontend owner: `feat/frontend`
- Backend owner: `feat/backend`
- Integration/demo owner: `feat/integration`

Use short-lived PRs. Merge early when contracts and smoke checks pass.

## Required Loop
1. Read the relevant contract and harness docs.
2. Make the smallest working change.
3. Run the matching verification script.
4. Review against `ARCHITECTURE.md`.
5. Update docs if behavior or contracts changed.

## Commands
```bash
scripts/verify
scripts/smoke
scripts/deploy-check
scripts/qa-loop
```

## Non-Negotiables
- No direct push to `main`.
- No guessed API shapes. Use `ARCHITECTURE.md`.
- No secrets in code, logs, screenshots, commits, or docs.
- New env vars must be added to `.env.example` or `ARCHITECTURE.md`.
- Destructive commands and file deletion require explicit human approval.
- Demo path beats feature count.

