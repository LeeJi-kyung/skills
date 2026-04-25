---
name: test-first-contract
description: Use before feature implementation to define contract-level tests for frontend/backend parallel work.
---

# Test-First Contract

## Purpose
Hackathon TDD is contract-first, not exhaustive test-first. Define the shape that lets frontend and backend work in parallel.

## When
- New API route.
- New user action.
- New data model.
- Bug fix on the demo path.

## Output
- Contract section in `ARCHITECTURE.md`.
- One success scenario.
- One failure scenario.
- The verification command that proves the slice works.

## Frontend Contract Test
- API client handles success envelope.
- API client handles error envelope.
- UI shows loading and recoverable error state.

## Backend Contract Test
- Route validates request body.
- Route returns standard success envelope.
- Route returns standard error envelope.

## Do Not
- Do not create broad tests for unbuilt features.
- Do not mock an API shape that is not in `ARCHITECTURE.md`.
- Do not block the demo for non-critical coverage.

## Verify
```bash
scripts/verify
scripts/smoke
```

