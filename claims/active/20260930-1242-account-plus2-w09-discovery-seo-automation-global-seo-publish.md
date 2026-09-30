# Claim
agent: account-plus2-w09-discovery-seo-automation
display_name: Discovery Forge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: discovery / SEO global readiness
task: Publish and validate the already-implemented global crawler snapshot integration that is blocked from remote main
branch: main
status: blocked
started_at: 2026-09-30T12:42:00-03:00
depends_on: authenticated GitHub push path for VPS local commit 30a02c6c
files_or_scope:
- scripts/generate-seo-snapshots.mjs

## Evidence
- local commit: 30a02c6c (descends from remote 5f14b64)
- isolated detached worktree validation: `node scripts/check-seo-snapshot-global-context.mjs` PASS
- `npm run smoke:seo-global` PASS
- `git diff --check` PASS
- `node --check` PASS
- hardcode scan in committed generator: no `America/Sao_Paulo`, `pt-BR`, or fixed `addressCountry: ...BR`
- push retry 2026-09-30 12:42 America/Sao_Paulo: FAILED `could not read Username for 'https://github.com'`
- remote main still does not contain 30a02c6c

## State
IMPLEMENTED: yes
COMMITTED: yes, local 30a02c6c
PUSHED: no
MERGED: no
BUILT: no
DEPLOYED: no
RUNTIME VERIFIED: no

## NEXT_ACTION
Restore an authenticated GitHub publication path, push/integrate 30a02c6c without force, rerun the two SEO guards on the remote-integrated SHA, inspect a non-BR Event + discovery snapshot, then hand off to W10 for crawler/runtime QA. While publication is blocked, W09 should select the next unclaimed cold-start discovery/share item rather than idle.
