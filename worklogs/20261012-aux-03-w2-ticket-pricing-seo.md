# AUX-03-W2 — SEO editorial: cálculo do preço de ingressos — 2026-10-12

agent: AUX-03-W2
area: SEO editorial / blog / aquisição de produtores
repository: petertecnetdev/cutinapp.petertecnet.com.br
status: ARTICLE_READY_NOT_PUBLISHED
claim: claims/active/20261008-1600-AUX-03-W2-seo-public-discovery.md

## Objetivo
Atrair produtores que pesquisam como calcular preço de ingresso de evento e converter a leitura em visita qualificada à landing /for-producers.

## Coordenação e evidências
- Lidos CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/assignments/AUX-03/W2.md (AVAILABLE), claim ativo AUX-03-W2 e worklog de 2026-10-11.
- Respeitado o escopo W09: sem alteração em scripts/generate-seo-snapshots.mjs, sitemap ou schema.
- Código atual de src/pages/blog/BlogArticlePage.js na main ainda apresenta links Markdown como texto, portanto publicação de artigo com CTA em Markdown depende de integração da branch feat/blog-internal-links-seo ou de CTA nativo validado.
- public/sitemap.xml inclui /for-producers, /eventos, /productions, /artists e /blog.
- Site público e API de conteúdo não acessíveis na consulta desta execução: inventário do CMS, eventos reais, indexação e runtime não verificados. Nenhum dado inventado.
- Trabalho anterior sobre divulgação de eventos e escolha de plataforma já existe; tema escolhido é distinto (precificação e ponto de equilíbrio).

## Oportunidade e entregável
Artigo original completo em Markdown produzido nesta execução, arquivo entregue ao usuário: 20261012-AUX-03-W2-guia-preco-ingressos.md.
Título: Como calcular o preço do ingresso de um evento: custos, taxas e ponto de equilíbrio.
Slug: como-calcular-preco-ingresso-evento.
Intenção: informacional de alta afinidade comercial; volume de buscas não verificado.
SEO title: Como calcular o preço do ingresso de um evento | Cutinapp.
Meta description: Veja como calcular custos, taxas e ponto de equilíbrio para definir o preço dos ingressos do seu evento, com exemplo prático e checklist.
Inclui fórmula com taxas percentuais/fixas, exemplo numérico explicitamente hipotético, ponto de equilíbrio, lotes, FAQ, checklist e CTA. Não atribui taxas à Cutinapp.
Canonical proposto: https://cutinapp.petertecnet.com.br/blog/como-calcular-preco-ingresso-evento.
Links internos verificados em rotas do código: /for-producers, /eventos, /productions.
OG: título editorial, descrição e arte oficial 1200×630 pendente.
Schema.org: BlogPosting com datas reais de publicação/modificação e imagem real somente quando disponível.

## Canal, CTA e métricas
Canal: blog público / busca orgânica.
CTA principal: Conheça a Cutinapp para produtores -> /for-producers.
Métrica primária: cliques do artigo para /for-producers divididos por sessões do artigo, quando mensurável.
Métricas de resultado: producer_signup_completed e primeiro evento publicado, apenas com atribuição válida.
Hipótese: busca por precificação de ingressos alcança produtores em fase de planejamento; impacto ainda não medido.

## Próxima ação
1. Conferir inventário do CMS para evitar duplicação e validar condições comerciais da landing (há handoff P1 anterior sobre trial/assinatura).
2. Validar integração de links Markdown e HTML inicial indexável com owners existentes; não duplicar claim W09.
3. Cadastrar artigo, revisar fórmulas e mobile, gerar imagem OG com logo oficial, publicar somente após QA.
4. Medir cliques qualificados e conversões. Nenhum deploy VPS realizado.

## Conta principal
SIM: revisão editorial, publicação CMS, aprovação de marca e integração das correções de conversão/SEO existentes.
