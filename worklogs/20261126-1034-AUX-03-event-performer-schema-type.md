# AUX-03 — Worklog 2026-11-26 10:34 BRT — Schema.org performer por tipo de artista

## Objetivo
Corrigir a representação semântica dos artistas no JSON-LD das páginas públicas de evento, sem duplicar a correção já encaminhada a W09 no gerador de snapshots.

## Área
SEO de páginas públicas, Schema.org, descoberta de eventos e conversão de participantes.

## Coordenação consultada
- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`.
- Worklogs AUX-03 de 16, 18, 20, 23, 24 e 25/11.
- Claim ativo W09 `20260930-0838-w09-seo-global-snapshot-root-cause.md`.
- Issue #728 e comentários.
- Issues #636, #637, #643 e #729 após criação.
- PRs #722, #724, #725, #726, #727 e #718.

## Confirmado
- CURRENT_STATE.md e PRIORITIES.md continuam consolidados em 30/10; BLOCKERS.md lista FIN-P0-001, mas não espelha #643.
- Issue #643 permanece aberta; runtime público continua sem GO.
- Issue #728 permanece aberta e sem comentários/aceite visível na consulta.
- O claim ativo W09 cobre `scripts/generate-seo-snapshots.mjs` e helpers de SEO global. O trabalho de snapshots não foi alterado.
- O worklog AUX-03 de 16/11 já registrou o problema de `MusicGroup` para todos os performers no gerador de snapshots; a correção desse caminho continua com W09.
- `src/utils/eventSeo.js` contém outra função `eventPerformers` no caminho runtime e atribui `MusicGroup` a todos os artistas.
- `src/pages/artist/ArtistViewPage.js` reconhece `solo`, `band`, `duo`, `group`, `collective` e `orchestra`.
- `SeoManager.js` usa `buildEventSeo` na rota pública `/event/:slug`.
- Não foi encontrada issue aberta equivalente para o caminho runtime.
- Issue #636 permanece CLAIMED por `cutinapp-growth-producer`; não foi tocada.
- Issue #637 permanece reservada à atribuição first-touch; não foi tocada.

## Hipótese
Tipar corretamente `Person` e `PerformingGroup` melhora a precisão do JSON-LD Event e evita declarar artistas solo como grupos musicais. Não há prova de aumento de ranking, rich results ou conversão.

## Trabalho realizado
1. Consultei os arquivos de coordenação e o histórico recente de AUX-03.
2. Consultei o claim ativo W09 e preservei seu ownership do gerador.
3. Inspecionei `src/utils/eventSeo.js`, `src/components/SeoManager.js` e `src/pages/artist/ArtistViewPage.js`.
4. Confirmei o mapeamento de `artist_type` já reconhecido pelo perfil.
5. Pesquisei issues para evitar duplicação.
6. Criei a issue #729 no repositório Cutinapp, com mapeamento proposto, testes e critérios de aceite.
7. Não editei código, não criei branch/PR, não fiz merge/build/deploy e não acessei a VPS.

## Entregável
- Issue #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- Especificação: `deliverables/AUX-03/20261126-1034-AUX-03-event-performer-schema-type.md`

## Canal e CTA
Google Search → página pública de evento → ingressos/detalhes → checkout.
CTA: **Ver ingressos e detalhes do evento**.

## Métrica
Impressões, cliques e CTR orgânicos por URL de evento; sessões orgânicas; `event_detail_viewed`; `event_ticket_intent_clicked`; início de checkout.
Baseline: N/D.

## Evidências
- #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- `eventSeo.js`: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/utils/eventSeo.js
- `ArtistViewPage.js`: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/artist/ArtistViewPage.js
- `SeoManager.js`: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/SeoManager.js
- Google Event structured data: https://developers.google.com/search/docs/appearance/structured-data/event
- W09 active claim: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md
- #728: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
- #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643

## Próxima ação
Owner de SEO/runtime revisar #729 e implementar o mapeamento com testes; W09 finalizar o gerador de snapshots; após GO público, validar JSON-LD e medir Search Console/GA4.

## Precisa da conta principal
SIM — coordenação do owner, priorização e validação pública pós-implementação.

## Estado
ISSUE_729_CREATED — SPEC_RECORDED — W09_SNAPSHOT_OWNERSHIP_PRESERVED — NOT_IMPLEMENTED — NOT_DEPLOYED.
