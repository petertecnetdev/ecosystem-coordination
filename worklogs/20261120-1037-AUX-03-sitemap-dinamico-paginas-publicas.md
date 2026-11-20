# AUX-03 W2 — Worklog 2026-11-20 — sitemap dinâmico de páginas públicas

## Objetivo
Verificar se o sitemap da Cutinapp acompanha os snapshots públicos gerados no build e preparar uma correção acionável para aquisição orgânica.

## Área
SEO editorial/técnico, descoberta pública, páginas de eventos, produções, artistas, blog e categorias/cidades.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- orchestration/WORKER_REGISTRY.md e orchestration/STATE.md.
- Assignment permanente AUX-03 W2; estado AVAILABLE, sem override W00.
- Worklogs/commits AUX-03 mais recentes, incluindo campanhas W1/W3 de 17–19/11 e script de descoberta comercial de 19/11.
- Entrega W2 de 08/11 sobre agenda pública.
- Handoff W2 de 07/11 sobre páginas cidade/período vazias.
- Main do frontend Cutinapp, gerador SEO, robots.txt, sitemap.xml e smoke de indexabilidade.

## Confirmado
- CURRENT_STATE.md continua consolidado em 30/10; commits e worklogs recentes foram usados para complementar.
- PRIORITIES.md mantém P0 financeiro/auth/segurança antes de P1/P2; esta ação foi classificada P2 porque a ausência no sitemap não prova ausência de indexação.
- BLOCKERS.md lista FIN-P0-001; não alterei o arquivo de ownership de W00.
- WORKER_REGISTRY confirma AUX-03 W2 como SEO, Blog & Public Discovery.
- A main do frontend consultada está em SHA 6db85d5f80c14acd2ed185ebf9e4afa535e14288.
- public/sitemap.xml (blob 2b64332876a613f354de221264eb5dfbe0bbb53a) tem somente sete URLs core e nenhuma URL dinâmica.
- scripts/generate-seo-snapshots.mjs (blob b94de8800be96b236faff3cc08539f986cab55fd) gera snapshots de eventos, produções, artigos, artistas, perfis, itens e discovery por cidade/período/categoria (linhas 694–789), mas encerra gravando somente o marcador .cutinapp-seo-snapshots (linhas 790–793), sem gerar sitemap.
- scripts/check-seo-indexability.mjs (blob d7364471440b4675074efd5445ee3df14a844009) valida rotas core, origem, duplicidade e prefixos privados, mas não valida paridade de URLs dinâmicas.
- A página /agenda/:slug continua dependente de snapshot/escopo W09; não foi incluída como se já estivesse implementada.
- O handoff de 07/11 já cobre noindex para períodos vazios; não repliquei esse escopo, apenas exigi que o sitemap consuma a elegibilidade resultante.
- O handoff de 08/11 cobre snapshots de agenda; não repliquei esse escopo.
- Search Console não foi consultado. Não há prova de que URLs dinâmicas estejam fora do índice.
- A abertura pública de /sitemap.xml não foi acessível na ferramenta de pesquisa; runtime não foi validado.

## Hipótese
O sitemap limitado a rotas core pode reduzir a facilidade de descoberta/atualização de páginas dinâmicas importantes, embora links internos possam permitir rastreamento. Não há baseline nem perda de tráfego comprovada.

## Trabalho realizado
1. Releitura das fontes de coordenação e do registry AUX-03.
2. Revisão de commits recentes AUX-03 para não duplicar conteúdo social/comercial.
3. Inspeção da main e dos caminhos de geração de snapshots.
4. Comparação entre public/sitemap.xml, robots.txt, gerador e smoke de indexabilidade.
5. Separação explícita deste escopo dos handoffs anteriores de páginas temporais vazias e agenda pública.
6. Especificação de sitemap dinâmico derivado do mesmo inventário e das mesmas regras de indexabilidade dos snapshots.
7. Definição de exclusões, canonical, lastmod, deduplicação, sitemap index e critérios de teste.
8. Handoff para W09/W00; sem edição do gerador compartilhado.

## Entregável
deliverables/AUX-03/20261120-AUX-03-sitemap-dinamico-paginas-publicas.md

## Canal
Google Search → páginas públicas dinâmicas → descoberta de eventos → página do evento.

## CTA
Participante: Ver evento e ingressos, conforme disponibilidade real.
Produtor: Conhecer a Cutinapp para produtores / Cadastrar minha produção, somente após GO do runtime.

## Métrica
Principal: cliques orgânicos para páginas de evento a partir de impressões de URLs dinâmicas.
Complementares: URLs enviadas/descobertas/indexadas por tipo, impressões, cliques, CTR e início de checkout orgânico.
Baseline: N/D; Search Console não consultado.

## Evidências
- Gerador main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L675-L800
- Sitemap main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/public/sitemap.xml
- Validador main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/check-seo-indexability.mjs
- Handoff 07/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/messages/20261107-1054-AUX03-W2-to-W09-empty-city-period-indexability.md
- Especificação 08/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261108-W2-public-production-agenda-discovery-seo.md
- Google Search Central sitemap: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview

## Próxima ação
W09 aceitar o escopo e implementar geração de sitemap no fluxo dos snapshots; W00 coordenar sem duplicar regras anteriores. Após runtime GO, conta principal/operador submete o sitemap no Search Console e AUX-03 compara URLs enviadas, descobertas e indexadas.

## Precisa da conta principal
SIM — coordenação W09 e acesso/validação do Search Console após publicação.

## Limites
Nenhum código do produto, branch, PR, merge, build, deploy, VPS, CMS ou publicação social alterados nesta execução.
