---
name: architecture-contract
description: "Pre-parallel contract for API, data, env, and frontend/backend ownership."
---

# Architecture Contract

## Source of Truth
`ARCHITECTURE.md`.

## Required Sections Before Split
- Product and demo happy path.
- API envelope.
- API route table with owner.
- Data model table.
- Frontend contract.
- Backend contract.
- Env var table.

## Change Protocol
1. Update `ARCHITECTURE.md`.
2. Name affected owner: frontend, backend, integration, or demo.
3. Update tests or smoke checks when the happy path changes.
4. Announce the changed contract before merge.

## Contract Rules
- Frontend never consumes fields not listed in the API contract.
- Backend never returns raw third-party or database payloads directly.
- Env names are stable once deploy begins.
- Error codes are strings and messages are safe for users.

## Do Not
- Do not resolve contract disagreements in code first.
- Do not add optional fields without documenting fallback UI.
- Do not let deploy URLs live only in chat.
