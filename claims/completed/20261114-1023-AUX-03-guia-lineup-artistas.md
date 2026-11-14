# Claim concluído — AUX-03 — Guia SEO de line-up e descoberta de artistas

**Claim:** 20261114-1023-AUX-03-guia-lineup-artistas  
**Worker:** AUX-03 — SEO, Blog & Public Discovery  
**Data:** 14/11/2026 10:23 BRT  
**Status:** COMPLETED — EDITORIAL ASSET AND SEO HANDOFF ONLY

## Objetivo
Criar um ativo evergreen para atrair produtores que pesquisam como organizar e divulgar o line-up de um evento, aproveitando funcionalidades reais da Cutinapp e conectando eventos a perfis artísticos.

## Área
SEO editorial, páginas públicas, aquisição de produtores, descoberta de artistas e distribuição.

## Confirmado
- O produtor pode localizar um perfil artístico existente ou convidar por e-mail quando a pessoa ainda não tem conta.
- O convite permanece pendente até aceite explícito do artista ou gestor autorizado.
- A participação suporta tipo, palco, horário previsto, ordem, atração principal e descrição.
- Há ação para gerar descrição de participação com IA; o texto precisa ser revisado.
- A página pública do evento apresenta a seção Line-up e cards que direcionam aos perfis públicos dos artistas retornados pelo endpoint público.
- `eventSeo.js` já inclui `performer` no JSON-LD, mas mapeia todos os artistas como `MusicGroup`; `ArtistViewPage.js` distingue `solo` e tipos de grupo.

## Hipótese
Um conteúdo que ensina produtores a estruturar line-ups pode gerar leads qualificados e estimular compartilhamento entre artistas. Não há conversões ou uplift medidos.

## Entregável
`deliverables/AUX-03/20261114-AUX-03-guia-lineup-artistas-divulgacao.md`

## Canal e CTA
- Canal primário: blog.
- Canais derivados: Instagram carrossel, Reel, Stories e Direct.
- CTA editorial: Conhecer a Cutinapp para produtores, após GO do runtime.
- CTA social: salvar/compartilhar checklist; resposta LINE-UP no Direct, somente com equipe disponível.

## Métrica principal
Produtores qualificados originados pelo artigo que publicam o primeiro evento em até 30 dias / produtores qualificados originados pelo artigo. Indicadores intermediários: sessões orgânicas, CTR, cliques CTA, leads, demonstrações, produção criada, convites e aceite de artistas. Baseline N/D.

## Evidências
- `src/pages/event/EventLineupPage.js`
- `src/pages/event/EventViewPage.js`
- `src/services/CutinappService.js`
- `src/pages/artist/ArtistViewPage.js`
- `src/utils/eventSeo.js`
- Google Search Central: https://developers.google.com/search/docs/appearance/structured-data/event
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs #722 e #724–#727.

## Limites
Nenhum evento real publicado na própria Cutinapp foi validado nesta execução; o artigo é evergreen e não inventa exemplos. A home pública pede JavaScript e as rotas comerciais não foram validadas pela ferramenta de pesquisa; isso não prova indisponibilidade universal. Metricool mostra GBP conectado, sem Instagram listado, e agenda de 14–21/11 vazia.

Nenhuma alteração de código, branch, PR, merge, build, deploy ou VPS.

## Próxima ação
- Conta principal/infra: resolver #643 e comprovar runtime.
- W00: coordenar PRs de aquisição e links editoriais.
- W09: revisar mapeamento Schema.org `performer` e consistência entre dados do JSON-LD e line-up público.
- Operador editorial: cadastrar rascunho e validar links/canonical/OG.
- AUX-03: distribuir e medir após GO.

**Precisa da conta principal:** SIM.

**Estado:** `EDITORIAL_ASSET_READY — SEO_REVIEW_HANDED_OFF — NOT_PUBLISHED — NOT_INDEXED — NOT_SCHEDULED — NOT_DEPLOYED`.
