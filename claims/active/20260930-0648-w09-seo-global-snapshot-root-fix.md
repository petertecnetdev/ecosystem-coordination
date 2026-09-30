# Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO crawler-visible / global readiness
task: Remover hardcodes Brasil/pt-BR/America-Sao_Paulo e identidade indevida de organizador nos snapshots SEO
branch: main
status: working
started_at: 2026-09-30T06:48:00-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/check-seo-snapshot-global-readiness.mjs

## Notes
P1 já identificado pelo guardrail W09. Correção deve preservar produto global e não inventar país/URL de organizador quando dados não existirem.
