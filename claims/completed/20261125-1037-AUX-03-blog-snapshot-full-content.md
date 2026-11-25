# Claim — AUX-03 — conteúdo integral nos snapshots SEO do blog

agent: AUX-03
status: completed
area: organic acquisition / editorial SEO / blog indexability
repository: petertecnetdev/ecosystem-coordination
product_repository: petertecnetdev/cutinapp.petertecnet.com.br
product_issue: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
deliverable: deliverables/AUX-03/20261125-1037-AUX-03-blog-snapshot-full-content.md
worklog: worklogs/20261125-1037-AUX-03-blog-snapshot-full-content.md

## Objetivo
Documentar um gap de SEO editorial confirmado no HTML pré-renderizado dos artigos e encaminhar a correção ao owner do gerador sem duplicar o claim W09.

## Feito
- Comparado o corpo do snapshot produzido por `buildBlogSnapshot` com o conteúdo integral renderizado em `BlogArticlePage.js`.
- Confirmado que o snapshot inclui apenas title, cover e excerpt, sem `article.content`.
- Pesquisadas issues abertas; nenhuma duplicata encontrada.
- Criada a issue #728 com evidências, requisitos de segurança e critérios de aceite.
- Preservado ownership de W09 sobre `scripts/generate-seo-snapshots.mjs`; AUX-03 não editou o gerador.

## Guardrails
- Não afirmar que o Google deixou de indexar os artigos; o Google pode renderizar JavaScript.
- Não editar o gerador nem abrir branch concorrente enquanto W09 mantém claim ativo.
- Não inserir HTML arbitrário de conteúdo editorial.
- Não alterar sitemap, snapshots de outras entidades, runtime ou VPS.
- Não duplicar issue #637 de atribuição first-touch.

## Próxima ação
W09/W00 avaliar a issue #728 e implementar/validar o conteúdo integral no snapshot dentro do ownership existente. Após runtime GO, inspecionar HTML bruto e medir Search Console/GA4.

## Estado
completed — diagnóstico e handoff registrados; issue #728 permanece OPEN; correção não implementada.
