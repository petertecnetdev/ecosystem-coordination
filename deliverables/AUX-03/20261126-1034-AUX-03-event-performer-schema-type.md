# AUX-03 — 26/11/2026 — Tipagem de artistas no Schema.org de eventos

## Objetivo
Melhorar a precisão semântica das páginas públicas de eventos da Cutinapp, representando corretamente artistas solo e formações coletivas na propriedade `performer` do JSON-LD `Event`.

## Área
SEO de páginas públicas, Schema.org, descoberta orgânica de eventos e conversão de participantes.

## Oportunidade
A página de artista já diferencia seis valores de `artist_type`, mas a função runtime que gera o JSON-LD do evento classifica todos os performers como `MusicGroup`. Isso descreve incorretamente artistas solo e não distingue grupos/coletivos de formações musicais.

## Confirmado
- `src/utils/eventSeo.js`, função `eventPerformers`: atribui `"@type": "MusicGroup"` a todo artista com nome.
- `src/pages/artist/ArtistViewPage.js`: reconhece `solo`, `band`, `duo`, `group`, `collective` e `orchestra`; usa `artist_type` para diferenciar perfil solo e grupo.
- `SeoManager` usa `buildEventSeo` na página pública `/event/:slug` depois de carregar os dados do evento.
- O Google orienta que `Event.performer` seja representado por `Person` ou `PerformingGroup`, um registro por performer. A documentação de Event structured data não exige que todo artista seja MusicGroup.
- O worklog AUX-03 de 16/11 já documentou a tipagem incorreta no gerador de snapshots e encaminhou esse caminho a W09. A issue #729 limita-se ao caminho runtime `src/utils/eventSeo.js`, sem alterar o escopo de W09.

## Hipótese
Representar os performers com tipos coerentes melhora a precisão dos dados estruturados das páginas de evento e reduz inconsistências entre a identidade do artista exibida na página e a entidade declarada ao mecanismo de busca. Não há prova de ganho de ranking ou rich result.

## Recomendação / regra proposta
Usar `artist.artist_type` quando disponível:
- `solo` → `Person`;
- `band`, `duo`, `orchestra` → `MusicGroup`;
- `group`, `collective` → `PerformingGroup`;
- ausente/desconhecido → `PerformingGroup` como fallback conservador.

Preservar nome, URL pública do perfil, ordenação e exclusão de registros sem nome. Não inferir tipo quando a API não fornecer dado reconhecido.

## Trabalho realizado
1. Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, worklogs recentes e claims relevantes.
2. Confirmei que CURRENT_STATE/PRIORITIES ainda têm consolidação de 30/10 e BLOCKERS.md não espelha a issue #643.
3. Consultei a issue #728: permanece aberta e sem comentários/aceite de W09 nesta leitura.
4. Relembrei o worklog AUX-03 de 16/11: o problema análogo no gerador está documentado e pertence ao claim ativo W09.
5. Inspecionei `eventSeo.js`, `SeoManager.js` e os tipos reconhecidos em `ArtistViewPage.js`.
6. Pesquisei issues abertas e não encontrei issue equivalente para o caminho runtime.
7. Criei a issue #729 com evidência, mapeamento sugerido e critérios de aceite.
8. Não alterei código, não criei branch e não toquei no gerador de snapshots.

## Entregável
- Issue #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- Especificação desta entrega.

## Canal e CTA
Canal: Google Search → página pública do evento → detalhes/ingressos → checkout.
CTA: **Ver ingressos e detalhes do evento**, conforme disponibilidade real do evento.

## Métrica
- Primária: impressões, cliques e CTR orgânicos por URL de evento no Search Console.
- Intermediárias: sessões orgânicas por página; evento existente `event_detail_viewed`; intenção de compra `event_ticket_intent_clicked`; início de checkout.
- Baseline: N/D. Não houve acesso ao Search Console/GA4 nesta execução.

## Evidências
- Issue #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- Runtime JSON-LD: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/utils/eventSeo.js
- Tipos de perfil: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/artist/ArtistViewPage.js
- Uso em SEO de rota: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/SeoManager.js
- Google Event structured data: https://developers.google.com/search/docs/appearance/structured-data/event
- Issue #728 / snapshots: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
- Claim W09 do gerador: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md

## Próxima ação
Owner de SEO/runtime revisar e implementar #729 com testes para os seis tipos; W09 continua o trabalho independente do gerador de snapshots; após runtime GO, validar JSON-LD no Rich Results Test/URL Inspection e medir Search Console.

## Precisa da conta principal
SIM — para coordenar owner da issue #729, priorização e validação pública após implementação; a issue já foi criada sem alterar produto.

## Estado
ISSUE_729_CREATED — RUNTIME_SCHEMA_FIX_PENDING — W09_SNAPSHOT_SCOPE_PRESERVED — NOT_IMPLEMENTED — NOT_DEPLOYED.
