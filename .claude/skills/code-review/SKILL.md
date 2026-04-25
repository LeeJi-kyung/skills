---
name: code-review
description: Pre-merge review for blockers: contract drift, secrets, demo risk.
---

# Code Review

## Review Order
1. Read `ARCHITECTURE.md`.
2. Inspect the diff.
3. Check contract, security, env, tests, and demo path.
4. Separate blocking issues from recommendations.

## Blocking Issues
- API response does not use `{ data, error, status }`.
- Frontend calls an undocumented route or field.
- Backend accepts unvalidated input.
- Secret appears in code, docs, logs, or screenshots.
- Main demo path is broken.
- Required env var is undocumented.

## Recommendations
- Naming, small refactors, minor visual polish.
- Test expansion outside the demo path.
- Performance improvements that do not affect demo safety.

## Output
```markdown
## Review

### Blocking
- [file:line] issue and required fix

### Recommendations
- [file:line] improvement

### Passed
- Contract:
- Security:
- Demo path:
```

## Do Not
- Do not request broad rewrites during merge freeze.
- Do not block on style if the demo path is safe.
- Do not approve if contract drift is unresolved.
