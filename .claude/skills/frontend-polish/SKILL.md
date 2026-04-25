---
name: frontend-polish
description: Next.js UI polish for responsive, shadcn/Tailwind, judge-facing demos.
---

# Frontend Polish

## Goal
Make the first viewport and primary demo path feel complete, specific, and trustworthy.

## Rules
- Build the actual app screen, not a marketing landing page.
- Use shadcn/ui and Tailwind consistently.
- Keep the primary action visible.
- Every async action needs loading, success, and error states.
- Text must fit on mobile and desktop.
- Hide unfinished features before demo.

## Judge-Facing Checklist
- First screen communicates who it helps and what it does.
- Demo path requires no explanation to follow.
- Empty states look intentional.
- Errors are recoverable.
- Visual hierarchy guides the next click.

## Do Not
- Do not add decorative clutter that slows implementation.
- Do not introduce a new component library.
- Do not ship raw JSON as the primary user experience.
- Do not leave obvious placeholder text in the demo path.

## Verify
Run frontend checks if scaffolded:

```bash
cd frontend
pnpm lint
pnpm build
```
