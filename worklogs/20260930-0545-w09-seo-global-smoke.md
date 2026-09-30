# Worklog
worker: W09
status: COMMITTED/PUSHED; pending runtime
priority: P1
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problem
Crawler snapshots ainda possuem hardcodes incompatíveis com produto global: America/Sao_Paulo, pt-BR, BR e organizer externo apontando para Cutinapp.

## Change
Expus o guardrail existente como comando padrão `npm run smoke:seo-global` em package.json para CI/release/local poderem executar a regressão de forma explícita.

## Evidence
- code commit: aed5ab6c98aa94e684c41e8e7c0089d3b971c834
- coordination completed claim: 3600cc930ab00c35164f0a7dcd4fdc3963ae06ab
- VPS: Remote Desktop sem device online; fallback Git usado.
- tests: NOT RUN (sem command runner disponível); não promovido para BUILT/DEPLOYED/RUNTIME VERIFIED.
- pending_deploy_vps: true

## Economic impact
Evita regressões de metadata geográfica/identidade em páginas públicas usadas para aquisição orgânica global e torna o gate reproduzível no fluxo npm.

## NEXT_ACTION
W09: corrigir `generate-seo-snapshots.mjs` para dados/configuração reais e fazer o smoke ficar verde sem enfraquecê-lo. W10: exigir `npm run smoke:seo-global` no release gate após a correção e validar snapshot não-BR + organizer externo em runtime.
