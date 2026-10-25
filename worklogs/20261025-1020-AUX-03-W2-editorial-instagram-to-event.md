# AUX-03-W2 — SEO editorial: Instagram → página pública → produtor — 2026-10-25

owner: AUX-03-W2
priority: P1
status: COPY_READY — NOT_PUBLISHED
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO editorial, aquisição de produtores e distribuição orgânica

## Objetivo e oportunidade
Criar um artigo evergreen de intenção prática "como divulgar evento no Instagram" que conecte a busca informacional a um CTA de produtor, sem inventar eventos, prometer resultados ou interferir no PR #722 ou na landing PR #724. A pesquisa de busca por páginas site:cutinapp.petertecnet.com.br/blog não retornou páginas Cutinapp nos resultados consultados; isso não prova ausência de indexação.

## Coordenação consultada
CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/STATE.md, orchestration/assignments/AUX-03/W2.md, claim ativo 20261008-1600-AUX-03-W2-seo-public-discovery.md e worklog 20261024-1014-AUX-03-W2-blog-links-pr722-review-ready.md. Escopo respeitado: PR #722 de links editoriais segue sob AUX-03-W2 e landing PR #724 sob AUX-03-W3. Não duplicar conteúdo do CMS sem checagem final.

## Trabalho realizado e entregável
Artigo completo de divulgação de eventos no Instagram, com roteiro de Reel, sequência de Stories, checklist de destino mobile, SEO title, meta description, slug, canonical proposto, briefing OG, BlogPosting, CTA contextual, mensuração e checklist de publicação. Arquivo: [entregável editorial](../deliverables/AUX-03/20261025-W2-artigo-divulgar-evento-instagram.md). Conteúdo preparado para parser Markdown simples verificado em src/pages/blog/BlogArticlePage.js e PR #722; não foi enviado ao CMS.

## Confirmado
- PR #722 documenta renderização de links Markdown; workflows verdes relatados em 24/10, sem merge/deploy comprovado.
- PR #724 é o trabalho ativo de correção de oferta comercial da landing.
- A página do blog consome conteúdo via BlogService e define title, description, canonical e BlogPosting no cliente; comportamento real do crawler não foi verificado.
- A pesquisa web de 25/10 não trouxe artigos Cutinapp para as consultas direcionadas; o inventário real do CMS não foi acessado.

## Hipótese
Um guia acionável que ajuda a converter interesse social em visita à página pública pode atrair produtores de eventos e gerar cliques qualificados para /for-producers.

## Recomendação, canal, CTA e métrica
Canal: blog público, busca orgânica e compartilhamento de produtores.
CTA: "Conheça a Cutinapp para produtores" → /for-producers, condicionado à validação do PR #724.
Métrica primária: primeiros eventos publicados atribuídos ao artigo.
Métricas intermediárias: sessões orgânicas, CTR artigo→landing, cadastros iniciados, produções criadas.
Baseline: não medido; sem alegação de tráfego, publicação ou conversão.

## Evidências
- Coordenação: https://github.com/petertecnetdev/ecosystem-coordination
- PR links: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR landing: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Código blog: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js

## Próxima ação e dependência da conta principal
1. Verificar duplicação no inventário real do CMS e aprovar conteúdo.
2. Validar landing PR #724 e integrar PR #722 após QA mobile e revisão.
3. Inserir artigo no CMS com metadados/OG oficiais, testar indexabilidade e links.
4. Medir cliques, cadastros e primeiros eventos por origem.

Conta principal necessária: SIM — aprovação editorial, integração de PRs e publicação/QA do CMS. Sem branch nova, sem deploy, sem alterações na VPS.
