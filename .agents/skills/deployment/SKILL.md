---
name: deployment
description: Use for Vercel frontend deploys, Railway backend deploys, env checks, smoke tests, and rollback decisions.
---

# Deployment

## Required Before Deploy
- `scripts/verify` passes or only skips unscaffolded parts.
- `scripts/deploy-check` passes.
- `/health` exists on the backend.
- Demo seed data or no-data fallback exists.

## Vercel Frontend
Required env:
- `NEXT_PUBLIC_API_URL`
- `NEXT_PUBLIC_SUPABASE_URL` if Supabase is used
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` if Supabase is used

Check:
```bash
cd frontend
pnpm build
vercel env ls
vercel --prod
```

## Railway Backend
Required env:
- `CORS_ORIGINS`
- `DATABASE_URL` if DB is used
- `SUPABASE_URL` if Supabase is used
- `SUPABASE_SERVICE_KEY` if privileged Supabase access is used

Check:
```bash
cd backend
uv run python -c "from main import app; print('backend import ok')"
railway up
railway logs
```

## Smoke Test
```bash
API_URL=https://your-api.example.com FRONTEND_URL=https://your-app.vercel.app scripts/smoke
```

## Rollback
- Vercel: use the previous successful deployment.
- Railway: revert to the last known good commit and redeploy.
- If deploy is unstable after 7:15, demo locally with seeded data.

