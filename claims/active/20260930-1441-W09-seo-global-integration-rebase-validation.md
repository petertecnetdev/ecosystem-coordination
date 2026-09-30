# Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: discovery / SEO global
task: Revalidar e destravar integração do contexto global no gerador crawler-visible sobre a main remota atual
branch: main / isolated detached worktree
status: blocked
started_at: 2026-09-30T14:41:23-03:00
depends_on: authenticated GitHub write path for petertecnetserver
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/seo-snapshot-global-context.mjs
- scripts/check-seo-snapshot-global-readiness.mjs

## Evidence
- remote main fetched at `02aac770cb7e98ffaead5486e327526a64d09ee4`.
- local W09 commit `30a02c6c` has parent `5f14b64`; cherry-pick onto current remote main succeeded cleanly in isolated worktree, producing validation commit `dcfa4469`.
- `node --check scripts/generate-seo-snapshots.mjs`: PASS.
- `npm run smoke:seo-global`: PASS (`SEO snapshot global-readiness guard passed`).
- `npm run smoke:seo-indexability`: PASS (`7 sitemap URLs, 6 core routes protected`).
- `git diff --check HEAD^ HEAD`: PASS.
- guard grep found no legacy `America/Sao_Paulo`, fixed `pt-BR` DateTimeFormat or `event.country || "BR"` in the integrated generator.
- non-destructive push from isolated worktree failed: `could not read Username for 'https://github.com'`.
- existing VPS workspace was not reset, cleaned, overwritten or deployed.

## State
IMPLEMENTED: yes
COMMITTED: yes locally (`30a02c6c`; rebased validation `dcfa4469`)
PUSHED: no
MERGED: no
BUILT: not claimed
DEPLOYED: no
RUNTIME VERIFIED: no

## NEXT_ACTION
Restore an authenticated non-destructive GitHub write path, publish the clean integration on top of current main, rerun both SEO smokes on the remote SHA, then inspect a real non-BR Event + discovery snapshot before W10 crawler/runtime QA.
