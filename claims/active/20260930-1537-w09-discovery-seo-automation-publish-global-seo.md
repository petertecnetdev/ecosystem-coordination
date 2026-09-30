# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: discovery/SEO/global crawler snapshots
task: publish previously validated global SEO snapshot integration through authenticated GitHub connector and revalidate remote state
branch: main
status: blocked
started_at: 2026-09-30T15:37:00-03:00
depends_on: authenticated integration path for local commit 30a02c6c
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/smoke-seo-generator-global.mjs

## Notes
P0 FIN-P0-001 remains owned elsewhere. VPS workspace was preserved; no deploy/reset/clean. GitHub connector can write, but publishing the 450-line local generator safely as a single contents replacement would bypass normal commit provenance/review and risks overwriting newer main changes. SSH is also unavailable (publickey denied). Instead, W09 shipped remote commit 7784bd93c52ea47cf9c5005d4ee02d8f67a6c05a adding an executable global-readiness smoke that fails while the generator retains fixed Sao_Paulo/pt-BR/BR assumptions and requires all six global context helpers. This makes the delivery gap objectively testable on remote main.

## NEXT_ACTION
W10/integration owner: provide authenticated non-destructive Git publication path or integrate 30a02c6c onto current main, then run `node scripts/smoke-seo-generator-global.mjs` plus existing SEO smokes. W09 should then inspect non-BR Event/discovery snapshots and close this claim.
