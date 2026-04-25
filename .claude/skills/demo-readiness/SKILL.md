---
name: demo-readiness
description: Final-hour demo prep: flow, seed data, fallback materials, risk burn-down.
---

# Demo Readiness

## Output
- 60-second product story.
- 3-minute click script.
- Seed data checklist.
- Production URL and local fallback.
- Known risks and recovery line.

## Demo Script
1. State the user and pain.
2. Show the input or trigger.
3. Show the AI/product result.
4. Show business value.
5. Mention what is real: deployed app, live API, real data, or controlled demo data.

## Readiness Checklist
- Happy path works twice in a row.
- Seed data is present.
- Broken non-demo surfaces are hidden.
- Network fallback exists.
- Presenter knows what to do if the API is slow.

## Do Not
- Do not add new features in the final hour.
- Do not depend on live third-party data without fallback.
- Do not show admin/debug screens to judges.

## Verify
```bash
scripts/smoke
```
