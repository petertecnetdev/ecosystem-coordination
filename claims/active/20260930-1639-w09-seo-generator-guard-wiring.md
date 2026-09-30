# Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO global readiness / CI guard
task: Wire the published crawler-generator global-readiness guard into the executable npm smoke surface so integration cannot silently ship fixed locale/timezone/country assumptions.
branch: main
status: working
started_at: 2026-09-30T16:39:00-03:00
depends_on: none
files_or_scope:
- package.json
- scripts/smoke-seo-generator-global.mjs

## Notes
FIN-P0-001 remains owned elsewhere and is not duplicated. The current remote generator still contains fixed America/Sao_Paulo, pt-BR and BR fallback; the guard exists remotely but package.json does not expose it as an npm smoke command. This claim adds a deterministic integration gate while the full generator fix remains pending.
