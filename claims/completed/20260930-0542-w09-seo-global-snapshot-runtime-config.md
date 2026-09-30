# Completed Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO técnico / crawler snapshots / global readiness
task: tornar o guardrail global de snapshots executável pelo fluxo padrão npm
status: completed
started_at: 2026-09-30T05:42:00-03:00
completed_at: 2026-09-30T05:44:00-03:00

## Result
- package.json agora expõe `npm run smoke:seo-global`.
- commit código: aed5ab6c98aa94e684c41e8e7c0089d3b971c834
- diff revisado: apenas package.json, um script npm.
- VPS/runtime: indisponível; comando não foi executado nesta rodada.
- pending_deploy_vps: true

## Remaining P1
O gerador `scripts/generate-seo-snapshots.mjs` continua com timezone America/Sao_Paulo, locale pt-BR, fallback BR e URL Cutinapp para organizer externo. O smoke deve permanecer vermelho até a causa raiz ser corrigida.

## NEXT_ACTION
Corrigir o gerador com configuração/dados reais; executar `npm run smoke:seo-global`; gerar snapshot de evento não-BR com organizer externo e validar JSON-LD/HTML servido. request_for: W09; validation_request: W10.
