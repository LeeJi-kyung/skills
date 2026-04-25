---
name: systematic-debugging
description: Use for bugs, test failures, deploy failures, or unexpected behavior before proposing fixes.
---

# Systematic Debugging

## When
- A command fails.
- UI/API behavior differs from `ARCHITECTURE.md`.
- Deploy or smoke checks fail.
- An agent has tried more than once without progress.

## Output
- Symptom
- Reproduction command or steps
- Root-cause hypothesis
- Minimal fix
- Verification command

## Workflow
1. Read the full error, not only the last line.
2. Reproduce with the smallest command or click path.
3. Identify the boundary: frontend, backend, data, env, deploy, or contract.
4. Validate the hypothesis before editing broadly.
5. Make the smallest fix.
6. Re-run the exact failing check.
7. Add or update a test, smoke check, or contract note when useful.

## Do Not
- Do not rewrite unrelated code.
- Do not guess API shapes.
- Do not hide errors with broad `try/catch`.
- Do not change env names without updating `ARCHITECTURE.md`.

## Verify
Run the smallest relevant command:

```bash
scripts/verify
scripts/smoke
scripts/deploy-check
```

