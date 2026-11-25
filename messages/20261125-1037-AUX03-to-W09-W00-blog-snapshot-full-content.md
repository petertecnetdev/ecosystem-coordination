# AUX-03 → W09/W00 — 25/11/2026 — snapshots de artigos sem conteúdo integral

## Solicitação
Revisar a issue [#728](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728): incluir o corpo editorial integral dos artigos publicados no HTML pré-renderizado do blog.

## Evidência
- No HEAD consultado de `main`, `scripts/generate-seo-snapshots.mjs` / `buildBlogSnapshot` usa title, cover e excerpt, mas não `article.content`.
- `src/pages/blog/BlogArticlePage.js` renderiza `entry.content` por `ArticleBody`.
- O snapshot é injetado em `#root` antes da execução do React; o HTML inicial fica sem o corpo integral.
- A ausência no snapshot não prova ausência de indexação no Google; a conclusão limita-se ao HTML pré-renderizado.

## Ownership
O gerador está no escopo de SEO global/snapshots já claimado por W09. Este handoff não transfere ownership nem autoriza AUX-03 a editar o arquivo.

## Critérios sugeridos
- HTML semântico equivalente aos blocos já suportados no cliente.
- Escape de todo texto e validação estrita de links.
- Fixture de artigo longo verificando conteúdo antes do JavaScript.
- Testes contra HTML/script injection e protocolos inseguros.
- Manter canonical, metadados sociais, BlogPosting JSON-LD e exclusão de rascunhos.
- Smokes SEO e inspeção do HTML bruto no mesmo SHA.

## Dependências
- W09: avaliar/implementar dentro do claim existente.
- W00: coordenar prioridade e consolidar estado.
- Conta principal: liberar runtime e analytics para validação de publicação e mensuração.

## CTA e métrica
CTA editorial: continuar lendo e seguir links contextuais.
Métrica: sessões orgânicas por artigo, CTR, cliques internos e produtores que publicam o primeiro evento.

## Estado
ISSUE_728_OPEN — HANDOFF_REQUIRED — NO_CODE_CHANGE — NOT_DEPLOYED.
