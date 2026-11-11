# AUX-03 — Worklog 2026-11-11 10:21 BRT — Guia de descoberta de eventos para participantes

## Objetivo
Preparar um conteúdo de aquisição orgânica para participantes que pesquisam eventos por cidade, localização, data, preço, formato ou gênero.

## Área
SEO editorial, descoberta pública, participantes, blog e distribuição social.

## Oportunidade
O conteúdo de 10/11 cobre o uso do ingresso digital/QR Code depois da compra. O kit de 11/11 às 10:15 cobre aquisição de produtores e qualidade da página do evento. Esta entrega ocupa outra etapa e público: descoberta de eventos antes de escolher/comprar.

## Coordenação consultada
- Li CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, COMMANDS.md, REVENUE_TARGET.md e PROFITABILITY_PLAN.md.
- Li os worklogs recentes, claims active/completed relevantes, o kit de página de evento criado em 11/11 às 10:15 e o handoff correspondente.
- CURRENT_STATE.md permanece com consolidação visível de 30/10; complementei com os registros recentes e o estado atual do GitHub.
- O claim AUX-03 do kit de página de evento de 11/11 está concluído. Não alterei nem dupliquei esse entregável.
- Issue Cutinapp #643 permanece OPEN, atualizada em 10/11 13:44 UTC; descreve divergência entre SHA do filesystem e SHA servido pelo Nginx/HTTPS público. Não há evidência de resolução nesta consulta.
- PRs #724, #725, #726 e #727 continuam OPEN/NOT MERGED; #727 permanece Draft.
- O worklog de 11/11 às 10:15 registra Metricool brand cutinapp sem instagramData e agenda 11/11–18/11 vazia. Isso não prova ausência de posts publicados diretamente no Instagram.
- Nenhum evento Cutinapp específico foi confirmado por busca pública nesta execução; o artigo não usa exemplos de eventos, cidades, preços ou artistas.

## Confirmado — funcionalidades no código
- src/App.js blob 6db85d5f80c14acd2ed185ebf9e4afa535e14288: rotas /search, /cidades, /eventos, /eventos/:citySlug, /eventos/:citySlug/categoria/:categorySlug e /eventos/:citySlug/:periodSlug.
- src/pages/search/GlobalSearchPage.js blob 37c1be658c6db8cfc8ccc455d31bf1fb3e4e4963: busca global por eventos, produções, artistas, pessoas, publicações, itens, locais e promoters; filtros rápidos Hoje/Amanhã/Fim de semana/Gratuitos/Com ingresso/Perto de mim; filtros de cidade, preço máximo, raio, formato e gênero.
- src/pages/location/CitiesDirectoryPage.js blob 6eabf5affa475f16e30a81047bf2be8aa961c836: consulta cidades com eventos futuros e apresenta somente as cidades retornadas pela API.
- src/pages/event/EventDiscoverySeoPage.js blob 88c058790e20a7e260f66df416658523cfbf8e36: páginas de descoberta por cidade/período/categoria, lista de eventos e CTA “Ver evento e ingressos”.
- Esses dados são confirmação de código, não de runtime público.

## Hipótese
Um guia que ensina participantes a usar os filtros reais pode aumentar o avanço da busca para páginas de evento. Não há baseline ou resultado de conversão medido.

## Trabalho realizado
1. Cruzei o conteúdo já preparado para evitar repetição: QR Code (pós-compra), compra segura e kit de produtores.
2. Inspecionei rotas, busca global, filtros e diretório de cidades na main.
3. Preparei artigo SEO completo, carrossel de seis telas, legenda e sequência de Stories.
4. Defini CTAs e métricas de avanço para páginas de evento e checkout.
5. Mantive o gate NO-GO: não publicar links até validação da issue P0 #643.

## Entregável
deliverables/AUX-03/20261111-AUX-03-guia-encontrar-eventos-perto-de-voce.md

## Canal
Blog → busca/cidades → página de evento → checkout; distribuição complementar por Instagram carrossel e Stories após GO.

## CTA
Artigo: **Explorar eventos** / **Ver cidades com eventos**.  
Social: salvar e compartilhar; sticker de busca apenas depois do GO público.

## Métrica principal
Sessões que chegam a uma página de evento a partir do artigo ÷ sessões orgânicas do artigo.

Secundárias: impressões, cliques, CTR, uso da busca, filtros aplicados, visualizações de eventos, início de checkout e compras atribuídas.

Baseline: N/D.

## Evidências
- App routes: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/App.js
- Global search: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/search/GlobalSearchPage.js
- City directory: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/location/CitiesDirectoryPage.js
- Public discovery pages: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/event/EventDiscoverySeoPage.js
- P0 public serving issue: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- Producer page kit 11/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261111-AUX-03-kit-pagina-evento-que-converte.md
- QR guide 10/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md

## Próxima ação
Conta principal/infra resolver issue #643 e validar /search, /cidades e /eventos em smartphone por Wi-Fi e rede móvel. Depois, owner editorial publica o artigo como rascunho e agenda o carrossel/Stories com links rastreáveis.

## Precisa da conta principal?
SIM — runtime público, aprovação editorial e publicação dos ativos.

## Estado final
ARTICLE_COMMITTED — WORKLOG_COMMITTED — CLAIM_COMPLETED — HANDOFF_COMMITTED — NOT_PUBLISHED — NOT_INDEXED — PUBLIC_RUNTIME_NO_GO — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY — NO_VPS_ACCESS.
