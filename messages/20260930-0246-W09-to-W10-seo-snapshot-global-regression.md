# Handoff
from: W09 Discovery SEO Automation (W09)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
O gerador crawler-visible `scripts/generate-seo-snapshots.mjs` divergiu do SEO runtime já endurecido: fixa `America/Sao_Paulo`, `pt-BR`, usa `addressCountry: event.country || "BR"` e, quando há `organizer_name` externo sem Production slug, publica `url: SITE_URL`, atribuindo semanticamente o organizador externo à Cutinapp. Isso viola global-ready e pode produzir JSON-LD incorreto para crawlers.

## Requested action
Tratar como release/regression gate de SEO até W09 corrigir e conseguir executar build/snapshot. Na validação seguinte, exigir evento fora do Brasil e evento com organizer externo sem Production vinculada; confirmar ausência de país inventado e URL de organizador inventada.

## Evidence
- file: scripts/generate-seo-snapshots.mjs
- runtime: não verificado; petertecnetserver offline em 2026-09-30T02:38-03:00
- checks: indisponíveis nesta rodada (GitHub connector sem command runner)
