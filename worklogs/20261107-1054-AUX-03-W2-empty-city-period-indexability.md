# AUX-03 W2 — Worklog 2026-11-07 — Páginas temporais vazias de descoberta

## Objetivo
Transformar as páginas públicas de descoberta por cidade/período em landing pages orgânicas úteis, impedindo que rotas sem eventos sejam geradas como páginas indexáveis e sem conteúdo.

## Área
SEO, blog e descoberta pública; páginas de cidade/período; indexabilidade; links internos.

## Oportunidade
A geração atual cria páginas de `hoje`, `amanha`, `fim-de-semana` e `proximos-7-dias` para cada cidade identificada. O filtro pode retornar zero eventos, mas a página continua sendo gravada e recebe robots indexável.

## Confirmado
- Consultei `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `claims/README.md`, claim ativo W3 conhecido, assignment W2 e commits/worklogs recentes de 05–07/11.
- `orchestration/assignments/AUX-03/W2.md`: W2 = AVAILABLE, sem assignment específico.
- `orchestration/assignments/AUX-03/W3.md`: assignment de landing de produtores DONE; fallback à função-base.
- `claims/active/20261009-1600-AUX-03-W3.md`: claim genérico de aquisição de produtores; não cobre SEO de cidade/período.
- W3 concluiu em 07/11 a sequência pós-cadastro de produtores. Não repeti copy, gatilhos, prospecção nem mensagens.
- PR #692 está closed/merged; trata previews sociais de eventos encerrados, não indexabilidade de páginas temporais vazias.
- PRs #724, #725, #726 e #727 continuam open/not merged na consulta; #727 draft. Não alterei escopo desses PRs.
- `scripts/generate-seo-snapshots.mjs` na main: blob `b94de8800be96b236faff3cc08539f986cab55fd`.
- Linhas 266–282: `applySeo` sempre define robots `index, follow, max-image-preview:large`.
- Linhas 635–655: `buildDiscoverySnapshot` usa esse padrão em todas as páginas.
- Linhas 745–760: cada cidade recebe snapshots para quatro períodos; cada snapshot é escrito mesmo quando `filtered.length === 0`.
- Linhas 627–633: corpo da página não apresenta estado vazio e a página de cidade liga incondicionalmente para hoje, amanhã e fim de semana.
- Linhas 597–625: `discoverySchema` cria ItemList com `numberOfItems: events.length`, inclusive zero.
- Não consultei Google Search Console; não afirmo que páginas vazias já foram indexadas.
- `CURRENT_STATE.md`/ `PRIORITIES.md` têm consolidação de 30/10; commits/worklogs recentes complementaram o estado.

## Hipótese
Páginas vazias indexáveis podem diluir a utilidade do conjunto de páginas de descoberta e gerar visitas sem resultado. Aplicar noindex às páginas temporais vazias e retirar links internos para elas tende a concentrar descoberta em rotas com inventário real. Impacto não medido.

## Trabalho realizado
- Inspecionei o gerador SEO na main e localizei o caminho exato que cria snapshots vazios.
- Diferenciei esta lacuna do PR #692 (previews sociais de eventos encerrados) e dos trabalhos pendentes de landing/blog/artista.
- Preparei especificação com alteração mínima em applySeo, noindex condicional, estado vazio, links condicionais, cuidado com sitemap e critérios de regressão.
- Não alterei o gerador compartilhado por ser escopo anteriormente atribuído a W09.

## Entregável
`deliverables/AUX-03/20261107-W2-empty-city-period-indexability.md`

## Canal
Google Search → páginas de cidade/período → página de evento → detalhes/ingressos.

## CTA
- Com inventário: abrir um evento real.
- Sem inventário no período: **Ver agenda completa de {cidade}**.

## Métrica
- Aceite: zero páginas temporais vazias com robots indexável.
- Negócio: cliques em eventos / sessões das páginas de cidade; impressões, cliques e CTR no GSC.
- Baseline: N/D. GSC e conversões não foram consultados.

## Evidências
- Gerador SEO: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- PR #692 (merged, escopo diferente): https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/692
- Assignment W2: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/orchestration/assignments/AUX-03/W2.md
- Handoff W3 07/11: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/worklogs/20261107-1003-AUX-03-W3-producer-post-signup-activation-sequence.md
- Google Search Central — robots meta: https://developers.google.com/search/docs/crawling-indexing/robots-meta-tag

## Próxima ação
W09 / owner do gerador: implementar e testar noindex/follow para períodos vazios, estado vazio e links internos condicionais; verificar exclusão de noindex do sitemap. Conta principal deve coordenar o owner e aprovar integração.

## Precisa da conta principal?
SIM — coordenação/autoridade para alterar o gerador SEO compartilhado.

## Estado final
DIAGNOSIS_CONFIRMED — SPEC_PREPARED — WORKLOG_COMMITTED — NOT_IMPLEMENTED — NOT_MERGED — NOT_DEPLOYED — NO_VPS_ACCESS — GSC_NOT_ACCESSED — CONVERSION_NOT_MEASURED.
