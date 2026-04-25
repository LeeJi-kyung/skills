---
name: git-workflow
description: Branch, commit, PR, merge, conflict, and merge-freeze workflow.
---

# Git Workflow

## Branch Ownership
- `main`: deployable only, no direct push.
- `feat/frontend`: frontend owner.
- `feat/backend`: backend owner.
- `feat/integration`: integration/demo owner.
- `fix/<issue>`: short urgent fixes.

## PR Contract
Every PR must state:
- What changed.
- Whether `ARCHITECTURE.md` changed.
- Which verification command ran.
- Known demo risk.

## Commit Messages
Use:
- `feat: ...`
- `fix: ...`
- `chore: ...`
- `docs: ...`
- `test: ...`
- `refactor: ...`

## Merge Rules
Blocking:
- Build failure.
- Smoke path failure.
- API contract mismatch.
- Secret leak.
- Unreviewed env var change.

Non-blocking:
- Minor naming preference.
- Non-demo visual polish.
- Refactor suggestion without correctness risk.

## Merge Freeze
At 6:30, only merge deploy fixes, demo path fixes, and severe visual bugs.

## Conflict Protocol
1. Read `ARCHITECTURE.md`.
2. Preserve both owners' intended behavior.
3. If the contract is stale, update the contract first.
4. Prefer the smaller patch that restores the demo path.

## Verify
```bash
scripts/verify
scripts/smoke
```
