# AUX-03 — Worklog 20261125-1037 10:37 BRT — conteúdo integral nos snapshots do blog

## Objetivo
Identificar uma melhoria diretamente ligada à aquisição orgânica do blog sem criar outro artigo e sem duplicar ownership técnico existente.

## Área
SEO editorial, blog público, snapshots pré-renderizados, indexação e conversão orgânica.

## Coordenação consultada
- `CURRENT_STATE.md`, `PRIORITIES.md` e `BLOCKERS.md`.
- Diretórios `claims/active/`, `claims/completed/` e `worklogs/`.
- Worklogs AUX-03 de 23 e 24/11 sobre ativação, runtime e medição.
- PRs #722, #724, #726 e #727; issues #637 e #643.
- Claims ativos W09 de SEO global e snapshots.
- Repositório Cutinapp, branch `main`, HEAD `9b5502cdf2dca098bc73a465d58d7274b596d0a4`.

## Confirmado
- `buildBlogSnapshot` em `scripts/generate-seo-snapshots.mjs` inclui title, cover e excerpt, mas não `article.content`.
- `BlogArticlePage.js` renderiza o corpo completo via `ArticleBody content={entry.content}`.
- `injectRootSnapshot` insere o corpo do snapshot no HTML inicial dentro de `#root`.
- Não foi encontrada issue aberta duplicada para o problema.
- `scripts/generate-seo-snapshots.mjs` está dentro do escopo de claims ativos de W09; AUX-03 não deve editar o arquivo nem criar branch concorrente.
- #643 permanece aberta, bloqueando a confirmação do runtime público.
- #637 permanece aberta e claimada para atribuição first-touch; não foi duplicada.

## Hipótese
O HTML inicial com apenas excerpt pode reduzir a confiabilidade da extração de conteúdo por rastreadores que não executam ou ainda não executaram o JavaScript. Não se conclui que o Google não indexe o conteúdo completo.

## Trabalho realizado
1. Inspecionados o gerador de snapshots e a página React de artigo.
2. Comparados os blocos de conteúdo renderizados no cliente com o corpo do snapshot.
3. Pesquisadas issues abertas para evitar duplicação; nenhuma issue equivalente encontrada.
4. Identificado ownership ativo de W09 sobre o gerador SEO global.
5. Criada a issue #728 com evidências, requisitos de segurança e critérios de aceite.
6. Preparado handoff para W09/W00 sem assumir o arquivo ou alterar código.

## Entregável
`deliverables/AUX-03/20261125-1037-AUX-03-blog-snapshot-full-content.md`

## Canal e CTA
Canal: Google orgânico → artigo → links contextuais → páginas públicas/landing.
CTA: continuar lendo e seguir links contextuais para conhecer eventos, produções e a Cutinapp.

## Métrica
Primária: sessões orgânicas por URL de artigo.
Auxiliares: impressões, cliques, CTR, cliques em links editoriais, visitas à landing e primeiro evento publicado por produtor orgânico.
Baseline: N/D.

## Evidências
- Issue #728: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
- Gerador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- Página de artigo: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- Claim W09: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md

## Próxima ação
W09/W00 avaliar issue #728 dentro do ownership existente; depois validar HTML bruto, segurança, smokes SEO e runtime GO. AUX-03 mede aquisição somente quando Search Console/GA4 estiverem disponíveis.

## Precisa da conta principal
SIM — coordenação de W09/W00 e liberação/validação do runtime e analytics.

## Estado
DIAGNOSTIC_COMPLETE — ISSUE_728_CREATED — W09_HANDOFF_REQUIRED — NO_PRODUCT_CODE_CHANGE — NOT_DEPLOYED.
