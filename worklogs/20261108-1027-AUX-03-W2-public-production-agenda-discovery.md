# AUX-03-W2 — Worklog 2026-11-08 — SEO e compartilhamento de agendas públicas

## Objetivo
Transformar a rota pública `/agenda/:slug`, já existente, em canal de descoberta e distribuição para eventos publicados por produções.

## Área
SEO de páginas públicas, Open Graph/Twitter, sitemap, links internos, compartilhamento orgânico e conversão para evento/checkout.

## Oportunidade
A página pública de agenda já oferece programação semanal, próximos eventos, filtros, cópia de link e `navigator.share`. Porém, os metadados específicos são atualizados apenas depois da resposta da API; o `SeoManager` começa com title/description genéricos; o gerador de snapshots não cria `agenda/:slug`; o sitemap estático não lista agendas dinâmicas; e os botões de navegação para produção/eventos usam `navigate()`, não anchors `href`.

## Confirmado
- Li `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `COMMANDS.md`, `REVENUE_TARGET.md`, `PROFITABILITY_PLAN.md`, `claims/README.md`, claims active/completed, worklogs, messages e assignments AUX-03.
- P0 financeiro em `BLOCKERS.md` permanece com owner distinto; não alterei nem dupliquei o claim.
- `orchestration/assignments/AUX-03/W2.md` estava AVAILABLE; W2 não tinha assignment específico em andamento.
- Claim AUX-03 W2 de SEO da landing de produtores/PR #727 é separado e não foi alterado.
- Claims ativos W09 tratam SEO de produção pública e o arquivo compartilhado `scripts/generate-seo-snapshots.mjs`; nenhum claim explícito encontrado para a rota `/agenda/:slug`. Como a implementação exigiria o mesmo gerador, não editei o arquivo nem assumi ownership.
- A entrega AUX-03 W2 de 07/11 sobre páginas vazias de cidade/período foi lida; não foi repetida. Esta execução trata de agenda pública de produção, não de períodos de descoberta por cidade.
- `src/App.js` registra `/agenda/:slug` como rota pública.
- `src/pages/production/ProductionAgendaPublicPage.js` usa `cutinappService.publicProduction(slug)`, apresenta `weekly_agenda`, `upcoming`, `past`, compartilhar/copiar e filtros. O title, description e OG são alterados em `useEffect` após a resposta da API.
- Os botões "Ver produção" e "Ver evento" usam `navigate()`; as ações de compartilhar/copiar/filtro são ações apropriadas para buttons.
- `src/components/SeoManager.js` reconhece `/agenda/:slug`, mas resolve title/description genéricos a partir do slug.
- `scripts/generate-seo-snapshots.mjs` gera snapshots de eventos, produções, blog, artistas, perfis, itens e discovery; não gera `agenda/:slug`. O corpo de snapshot da produção não inclui link para agenda.
- `public/robots.txt` permite `/agenda/`.
- `public/sitemap.xml` é estático no repositório e contém sete URLs core; não contém agendas dinâmicas.
- `scripts/check-seo-indexability.mjs` verifica seis rotas core e prefixos privados; não testa agendas.
- Não consultei Google Search Console nem validei o HTML servido em produção. Não afirmo ausência de indexação, falha universal de preview ou perda de tráfego.

## Hipótese
Snapshots crawler-visible, OG/Twitter por produção e anchors reais podem aumentar a confiança no compartilhamento e facilitar a descoberta de eventos e ingressos. Sem teste A/B ou baseline.

## Trabalho realizado
- Inspecionei rota, página pública, serviço de dados, SeoManager, gerador de snapshots, sitemap, robots e smoke de indexabilidade.
- Identifiquei o ciclo de distribuição já existente: produção → agenda → share → participante → evento → checkout.
- Preparei especificação de snapshot específico, indexabilidade condicional, links rastreáveis, sitemap dinâmico, JSON-LD e copy de estado vazio.
- Preservei o ownership W09 do gerador compartilhado: apenas handoff, sem alteração de código.

## Entregável
`deliverables/AUX-03/20261108-W2-public-production-agenda-discovery-seo.md`

## Canal
Perfil público da produção → `/agenda/:slug` → WhatsApp/Instagram/Direct → página de evento → checkout.

## CTA
- Distribuição: Compartilhar agenda.
- Conversão: Ver evento e ingressos quando o status real permitir; caso contrário, Ver evento.
- Recuperação: Ver produção / Descobrir eventos em {cidade}.

## Métricas
- `agenda_share_started` / visualizações únicas.
- Sessões de referência / compartilhamentos iniciados.
- `agenda_event_click` / sessões de agenda.
- `agenda_checkout_started` / cliques em eventos originados na agenda.
- Compras atribuídas à agenda.
- Search Console: impressões, cliques, CTR e páginas indexadas em `/agenda/`.
- Baseline: N/D; não houve consulta de métricas.

## Evidências
- Agenda pública: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProductionAgendaPublicPage.js
- Rota e SEO: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js
- SeoManager: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/components/SeoManager.js
- Snapshot generator: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- Production public page: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/production/ProductionPublicPage.js
- Sitemap: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/sitemap.xml
- Robots: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/robots.txt
- Indexability smoke: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/check-seo-indexability.mjs
- W09 production SEO claim: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260927-1347-W09-public-production-seo.md
- W09 global generator claim: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md
- Google Search Central — JavaScript SEO: https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics
- Open Graph protocol: https://ogp.me/

## Próxima ação
W09 deve revisar e aceitar o escopo `/agenda/:slug` no gerador compartilhado. Conta principal coordena owner, integração de snapshots e sitemap. Depois executar smoke SEO, validação de crawler/preview e QA mobile.

## Precisa da conta principal?
SIM — integração no gerador/sitemap compartilhado e coordenação com W09.

## Estado final
OPPORTUNITY_CONFIRMED — SPEC_COMMITTED — HANDOFF_COMMITTED — PRODUCT_CODE_NOT_CHANGED — NO_PRODUCT_BRANCH — NO_PRODUCT_PR — NOT_MERGED — NOT_DEPLOYED — GSC_NOT_ACCESSED — CONVERSION_NOT_MEASURED.
