# Codex Notes

Use this repository from the project root.

## Startup Context
Codex should read `AGENTS.md` first. Treat it as the map, not the full manual.

Then inspect:
- `ARCHITECTURE.md`
- `docs/harness/OPERATING_MODEL.md`
- `docs/harness/QUALITY_GATES.md`
- `.agents/skills/`

## Skills
Codex should load `.agents/skills/` only. Claude Code should load `.claude/skills/` only.

Do not bulk-install community skill packs during the hackathon. Read third-party skills as references only, then copy the useful pattern into this local harness after review.

## Verification
Run the smallest relevant command:

```bash
scripts/verify
scripts/smoke
scripts/deploy-check
scripts/qa-loop
```

If a command cannot run because the app has not been scaffolded yet, report that as "not scaffolded" rather than inventing a pass.
