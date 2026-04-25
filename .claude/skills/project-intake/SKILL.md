---
name: project-intake
description: "Topic kickoff: product promise, target user, demo path, first build slices."
---

# Project Intake

## Time Limit
20 minutes.

## Output
Update `ARCHITECTURE.md` with:
- product name
- target user
- pain point
- one-line promise
- three-step demo happy path
- first API route
- first data entity
- required env vars

## Decision Rules
- Prefer a narrow pain point over a broad platform.
- Prefer a visible demo loop over hidden backend complexity.
- Prefer one excellent happy path over many partial features.
- If a feature is not needed for the demo, mark it optional.

## Team Split
Turn the demo path into:
- one frontend task
- one backend task
- one integration/demo task

## Do Not
- Do not start coding before the first API contract is written.
- Do not choose a topic that needs unavailable private data.
- Do not depend on integrations the team cannot authenticate quickly.
