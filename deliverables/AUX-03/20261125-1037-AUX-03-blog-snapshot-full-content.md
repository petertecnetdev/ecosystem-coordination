# AUX-03 — Conteúdo integral nos snapshots SEO do blog

**Data:** 25/11/2026  
**Objetivo:** melhorar a descoberta orgânica dos artigos da Cutinapp garantindo que o HTML pré-renderizado contenha o corpo editorial completo, e não apenas o título, a capa e o resumo.

## Resumo executivo

Foi identificado e documentado um gap específico no caminho de SEO editorial. O gerador de snapshots do frontend cria páginas estáticas para artigos publicados, mas a função `buildBlogSnapshot` inclui somente título, imagem e `article.excerpt`. A página React, por outro lado, renderiza o conteúdo integral por meio de `ArticleBody` usando `entry.content`.

A issue [#728](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728) foi aberta com evidências, escopo, critérios de aceite e requisitos de segurança. O código não foi alterado porque `scripts/generate-seo-snapshots.mjs` está dentro do escopo de SEO global já claimado por W09. O handoff preserva esse ownership.

## Confirmado

1. No HEAD de `main` consultado (`9b5502cdf2dca098bc73a465d58d7274b596d0a4`), `scripts/generate-seo-snapshots.mjs`:
   - busca artigos publicados em `fetchAllBlogArticles`;
   - gera snapshots em `blog/<slug>/index.html`;
   - em `buildBlogSnapshot`, inclui link para o blog, H1, capa e excerpt;
   - não inclui `article.content` no corpo pré-renderizado.
2. `injectRootSnapshot` insere o corpo gerado dentro de `#root`, portanto o HTML inicial do snapshot não contém o texto integral do artigo.
3. `src/pages/blog/BlogArticlePage.js` renderiza o conteúdo integral por `<ArticleBody content={entry.content} />`.
4. `ArticleBody` suporta headings, parágrafos, listas, citações, separadores e negrito.
5. PR #722 trata de links editoriais clicáveis no cliente e continua aberto; a issue #728 solicita equivalência segura também no snapshot.
6. A busca de issues abertas não encontrou uma issue anterior com o mesmo escopo.

**Limite da conclusão:** isso não prova que o Google deixe de indexar os artigos, pois ele pode executar JavaScript. O defeito confirmado é que o HTML pré-renderizado contém apenas o resumo, deixando a versão inicial entregue aos rastreadores substancialmente mais rasa que a página completa.

## Hipótese

Incluir o corpo editorial completo no HTML inicial tende a tornar a extração de conteúdo mais confiável para rastreadores e consumidores que não executam JavaScript. O impacto em indexação, impressões e cliques ainda precisa ser medido após integração e publicação.

## Recomendação

W09 deve avaliar a implementação na issue #728 durante a manutenção do gerador SEO, reproduzindo com segurança a semântica já usada por `BlogArticlePage.js`.

Requisitos:
- gerar H2/H3, parágrafos, listas ordenadas e não ordenadas, citações, separadores e negrito;
- preservar links internos e externos somente após validação de destino;
- escapar todo texto proveniente da API;
- não inserir HTML arbitrário;
- rejeitar protocolos como `javascript:` e `data:`;
- manter canonical, title, description, Open Graph, Twitter Card e BlogPosting JSON-LD;
- gerar snapshots somente para artigos publicados;
- não alterar snapshots de eventos, produções, artistas ou perfis.

## Entregável

- Issue de produto: [#728 — Incluir o conteúdo integral dos artigos nos snapshots públicos do blog](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728)
- Evidência principal: `scripts/generate-seo-snapshots.mjs`, função `buildBlogSnapshot`; `src/pages/blog/BlogArticlePage.js`, função `ArticleBody`.

## Canal, CTA e métrica

**Canal:** Google orgânico → artigo do blog → links contextuais → páginas públicas/landing de produtores.

**CTA:** continuar lendo e seguir links contextuais para conhecer eventos, produções e a Cutinapp.

**Métrica primária:** sessões orgânicas por URL de artigo.

**Métricas auxiliares:** impressões, cliques e CTR no Search Console; cliques nos links editoriais; sessões encaminhadas para páginas públicas e landing; produtores que chegam ao primeiro evento publicado.

Baseline: N/D. Não há Search Console/GA4 validado nesta execução.

## Evidências e coordenação

- [Issue #728](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728)
- [PR #722 — links editoriais](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722)
- [PR #727 — SEO da landing de produtores](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727)
- [Claim ativo W09 — SEO global/snapshots](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md)
- [CURRENT_STATE.md](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/CURRENT_STATE.md) e [BLOCKERS.md](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/BLOCKERS.md), consultados; consolidação ainda defasada em relação aos estados de novembro.

## Próxima ação

W09/W00 revisar a issue #728 e decidir a inclusão do corpo integral no gerador sem duplicar o trabalho global já claimado. Após implementação, exigir fixture de artigo longo, teste de escape/links, smokes SEO e inspeção do HTML bruto de um artigo publicado. Só medir indexação e conversão após runtime GO e acesso ao Search Console/GA4.

## Precisa da conta principal?

**SIM**, para coordenação de ownership com W09/W00 e liberação do caminho público. AUX-03 não tomou ownership do gerador.

## Estado operacional

- Pesquisa e diagnóstico: concluídos.
- Issue #728: criada.
- Worklog/claim/handoff: registrados.
- Código do produto: sem alterações.
- Branch/PR de produto: não criados.
- Merge/build/deploy: não realizados.
- VPS: não acessada.
- Publicação/indexação: não verificadas.

`SEO_GAP_CONFIRMED — ISSUE_728_OPEN — W09_HANDOFF_REQUIRED — NOT_IMPLEMENTED — NOT_DEPLOYED — INDEXING_NOT_VERIFIED`.
