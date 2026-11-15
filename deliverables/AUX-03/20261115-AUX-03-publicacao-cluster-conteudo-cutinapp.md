# AUX-03-W2 — Plano de publicação e interlinking do conteúdo Cutinapp

**Data:** 15/11/2026  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Prioridade:** P1 — destravar aquisição editorial já produzida  
**Estado:** PUBLICATION_PLAN_READY — NOT_PUBLISHED

## Objetivo

Converter os quatro ativos editoriais já preparados em um cluster de aquisição com ordem de publicação, links internos, CTAs e métricas definidos. Evitar produzir mais artigos enquanto os conteúdos existentes continuam sem ID de CMS, URL publicada ou indexação comprovada.

## Coordenação consultada

- Li `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `COMMANDS.md`, `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md` e `orchestration/assignments/AUX-03/W2.md`.
- Consultei os worklogs e entregáveis AUX-03 de 10–14/11, o claim ativo de W2 para SEO da landing de produtores, os PRs #722 e #724–#727 e a issue #643.
- `CURRENT_STATE.md` está consolidado em 30/10 e não reflete todos os registros de novembro; usei evidências mais recentes dos worklogs, GitHub e checks.
- `PRIORITIES.md` classifica landing comercial e SEO de alta intenção como P1; expansão editorial é P2 depois dos gates P0/P1.
- `BLOCKERS.md` lista FIN-P0-001, mas não espelha a issue pública P0 #643. Não alterei o arquivo de W00.
- Assignment AUX-03/W2 está AVAILABLE, sem override W00 ativo. W1 está BLOCKED por dependência de mídia pública para distribuição social. W3 concluiu o handoff da landing de produtores no PR #724.
- O claim ativo `20261008-1600-AUX-03-W2-seo-public-discovery.md` permanece aberto até a integração coordenada de #724/#727. Atualizei-o com a evidência dos checks de #727, sem encerrá-lo.

## Confirmado — backlog editorial existente

Os quatro materiais abaixo já estão preparados e não devem ser recriados:

| Prioridade | Conteúdo existente | Público | Slug proposto | Estado |
|---|---|---|---|---|
| 1 | Como organizar o check-in de um evento com QR Code | Produtores | `como-fazer-check-in-em-evento-com-qr-code` | Artigo preparado; não publicado |
| 2 | Como organizar e divulgar o line-up de um evento | Produtores e artistas | `como-organizar-line-up-de-evento` | Artigo preparado; não publicado |
| 3 | Como encontrar eventos perto de você na Cutinapp | Participantes | `como-encontrar-eventos-perto-de-voce` | Artigo preparado; não publicado |
| 4 | Como usar seu ingresso digital com QR Code na Cutinapp | Participantes | `como-usar-ingresso-digital-qr-code` | Artigo preparado; não publicado |

Evidências dos materiais:
- [Guia de ingresso digital](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261110-W2-guia-ingresso-digital-qr-code.md)
- [Guia de descoberta](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261111-AUX-03-guia-encontrar-eventos-perto-de-voce.md)
- [Guia de check-in para produtores](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261113-AUX-03-guia-checkin-qr-code-para-produtores.md)
- [Guia de line-up](https://github.com/petertecnetdev/ecosystem-coordination/blob/main/deliverables/AUX-03/20261114-AUX-03-guia-lineup-artistas-divulgacao.md)

Não encontrei nesta rodada uma página de evento da Cutinapp com publicação, data e URL verificáveis para usar como exemplo. Isso não prova que não existam eventos publicados; significa que não havia evidência pública verificável disponível para esta execução. Nenhum nome, data, local, artista ou preço foi inventado.

## Confirmado — dependências de publicação

### 1. Links editoriais ainda não estão prontos na main

- Na `main`, `src/pages/blog/BlogArticlePage.js` (blob `95a8cac0e95f7c020a64b0f46594d8638f57feb9`) renderiza parágrafos, títulos, listas, citações e negrito, mas não converte links Markdown em âncoras.
- O PR [#722 — links editoriais clicáveis](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722) contém `BlogInlineText.js` (blob `3c06fc136d81ede72f5c46389aa2cb35741c74b6`), que converte rotas internas em `Link` e URLs HTTP/HTTPS em âncoras externas com `noopener noreferrer`.
- #722 continua OPEN e seu próprio corpo informa que a branch está atrás da main. Os últimos runs registrados no PR — Validate `39959804379` e Lighthouse `39959804361` — concluíram SUCCESS, mas são evidência dos SHAs daqueles runs, não de uma atualização posterior da branch. É necessário atualizar/revisar o PR e repetir CI antes da integração.

### 2. Landing de produtores

- PR [#724](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724) continua OPEN e alinha a copy visível à oferta por transação, com CTA “Cadastrar minha produção”.
- PR [#727](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727) continua OPEN e alinha title, description e Schema.org à mesma oferta.
- Revalidei os jobs de #727: Validate run `41459268768` e Lighthouse run `41459268813`, ambos SUCCESS. #727 não deve ser integrado antes de #724 ou no mesmo release.
- O claim W2 correspondente foi atualizado com os resultados, sem marcar merge ou publicação.

### 3. Runtime público

A issue P0 [#643 — Nginx da Cutinapp serve release antigo](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643) continua OPEN. A evidência da issue descreve divergência entre o release no filesystem e o SHA servido pelo Nginx/HTTPS. Enquanto o SHA público não coincidir com o release aprovado, não há GO para ativar CTAs, publicar conteúdo ou afirmar que páginas e snippets estão funcionando em produção.

## Hipótese

Publicar primeiro os dois guias de produtores tende a gerar intenção comercial mais próxima da ativação do que ampliar imediatamente o topo do funil de participantes. Isso é uma hipótese baseada na intenção de busca e na proximidade da necessidade operacional; não há baseline nem uplift medido.

## Trabalho realizado — ordem e arquitetura editorial

### Ordem de publicação recomendada

**1º — Check-in com QR Code (produtores)**  
Motivo: responde a uma necessidade operacional concreta e demonstra uma função do produto. CTA principal: “Cadastrar minha produção”. Publicar depois do GO de runtime e da integração coordenada de #724/#727.

**2º — Line-up de evento (produtores e artistas)**  
Motivo: complementa o primeiro artigo e explica como a programação conecta produção, artistas e participantes. CTA principal: “Cadastrar minha produção”. Link contextual para o guia de check-in e para o diretório público de artistas, desde que a rota esteja acessível.

**3º — Encontrar eventos perto de você (participantes)**  
Motivo: conteúdo de descoberta de topo de funil. Publicar quando houver inventário público verificável e a jornada `/eventos` e `/cidades` estiver validada. Não inserir exemplos locais sem evento real.

**4º — Ingresso digital e QR Code (participantes)**  
Motivo: conteúdo de uso pós-compra e retenção. Publicar junto de páginas de evento funcionais; CTA secundário para explorar outros eventos.

### Mapa de links internos

| Origem | Âncora contextual | Destino | Condição |
|---|---|---|---|
| Guia de descoberta | encontrar eventos por cidade | `/cidades` | Runtime GO |
| Guia de descoberta | explorar eventos disponíveis | `/eventos` | Runtime GO e inventário real |
| Guia de descoberta | como usar o ingresso digital | artigo QR do participante | Artigo publicado e links clicáveis |
| Guia de ingresso QR | encontrar outro evento | `/eventos` | Runtime GO |
| Guia de ingresso QR | descobrir eventos por cidade | `/cidades` | Runtime GO |
| Guia de check-in | cadastrar minha produção | `/for-producers` | #724 + #727 integrados e runtime GO |
| Guia de check-in | organizar o line-up | artigo de line-up | Artigo publicado e links clicáveis |
| Guia de line-up | cadastrar minha produção | `/for-producers` | #724 + #727 integrados e runtime GO |
| Guia de line-up | conhecer artistas | `/artists` | Rota validada e perfis públicos disponíveis |
| Guia de line-up | organizar o check-in | artigo de check-in | Artigo publicado e links clicáveis |

Não usar links para slugs fictícios de eventos ou artistas. Quando um evento real estiver publicado, inserir link para sua URL canônica somente após verificar a página.

### Padrão de publicação por artigo

1. Conferir duplicidade no CMS e obter ID do artigo/rascunho.
2. Confirmar o slug efetivo e usar canonical correspondente à URL real do CMS.
3. Preencher title, meta description, excerpt, categoria, tags e imagem de capa própria.
4. Manter um H1, H2/H3 descritivos e conteúdo integralmente visível.
5. Inserir links Markdown somente depois da integração de #722 e validar que resultem em `<a href>`/links React Router no HTML servido.
6. Conferir Open Graph/Twitter, imagem HTTPS, BlogPosting, `datePublished`, `dateModified` e `mainEntityOfPage`.
7. Conferir snapshot/HTML inicial com W09; não depender apenas de metadados injetados depois do carregamento React.
8. Validar mobile 320/360/390/430 px e testar todos os CTAs.
9. Só então solicitar publicação e verificar URL pública, sitemap e indexação no Search Console.

## Canal, CTA e métrica

**Canal:** Google Search → artigo → link contextual → página pública Cutinapp → evento ou landing de produtor → cadastro/checkout.

**CTAs:**
- Produtores: **Cadastrar minha produção** → `/for-producers`, somente após GO.
- Participantes: **Explorar eventos** → `/eventos`, somente após GO.
- Conteúdo complementar: abrir o próximo artigo relacionado do cluster.

**Métrica principal para os dois guias de produtores:**
- `article_primary_cta_click` por slug;
- cadastros atribuídos ao artigo;
- produtores que publicam o primeiro evento em até 7 dias.

**Métricas dos guias de participantes:**
- sessões orgânicas;
- CTR do Google;
- cliques em `/eventos` e `/cidades`;
- visualizações de página de evento;
- início de checkout.

**Métrica de interlinking:** cliques únicos em links internos / sessões do artigo, segmentados por origem, destino e posição.

**Baseline:** N/D. Não houve acesso ao Search Console, CMS ou telemetria de conversão nesta execução.

## Próxima ação

1. **W00/conta principal:** resolver #643 e comprovar o mesmo SHA no filesystem, HTTP local do Nginx e HTTPS público.
2. **W00/owner de #722:** atualizar a branch atrás da main, repetir Validate/Lighthouse e concluir a revisão do renderizador de links.
3. **W00/conta principal:** revisar #724 e #727 como uma única liberação comercial; os checks de #727 estão verdes, mas o PR continua aberto.
4. **W09:** confirmar que snapshots/HTML inicial do blog exponham conteúdo, canonical, OG e BlogPosting.
5. **Operador editorial autorizado:** cadastrar os dois guias de produtores como rascunhos primeiro, retornar IDs/URLs e validar os links; depois seguir com os dois guias de participantes.
6. **AUX-03-W2:** conferir SEO on-page e indexação após cada URL pública estar disponível.

## Precisa da conta principal?

**SIM** — para resolver o P0 público, coordenar a integração de #722 e #724/#727 e autorizar a publicação no CMS. Nenhuma ação na VPS foi realizada.

## Limites

- Nenhum artigo foi publicado.
- Nenhum rascunho/ID de CMS foi criado ou confirmado.
- Nenhum post Instagram foi agendado.
- Nenhum evento ou artista foi inventado.
- Nenhum código do produto foi alterado.
- Nenhuma branch de produto foi criada.
- Nenhum merge, build ou deploy foi realizado.
- Nenhuma VPS foi acessada.
- Nenhuma métrica de tráfego ou conversão foi presumida.

## Estado final

`PUBLICATION_PLAN_READY — EXISTING_CONTENT_REUSED — PR722_LINK_RENDERING_OPEN — PR724_PR727_OPEN — ISSUE643_OPEN — CMS_NOT_ACCESSED — NOT_PUBLISHED — NOT_INDEXED — NO_PRODUCT_CODE_CHANGED — NO_MERGE — NO_DEPLOY — CONVERSION_NOT_MEASURED`.
