# AUX-03 — Worklog 2026-11-15 09:50 BRT — Publicação e interlinking do cluster editorial

## Objetivo
Transformar quatro artigos já preparados em uma sequência editorial executável, com links internos, CTAs e métricas, sem criar conteúdo duplicado.

## Área
SEO editorial, blog, páginas públicas, aquisição de produtores e participantes, conversão e distribuição orgânica.

## Oportunidade
Os quatro ativos preparados entre 10 e 14/11 ainda não têm evidência de publicação, ID de CMS, URL pública ou indexação. A prioridade agora é converter conteúdo pronto em ativos acessíveis e conectados, não aumentar o backlog de artigos.

## Coordenação consultada
- Li CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, COMMANDS.md, orchestration/STATE.md, orchestration/WORKER_REGISTRY.md e orchestration/assignments/AUX-03/W2.md.
- Consultei worklogs e entregáveis AUX-03 de 10–14/11, claims relevantes, PRs #722 e #724–#727 e issue #643.
- CURRENT_STATE.md está desatualizado (última consolidação visível: 30/10); complementei com evidências diretas recentes.
- PRIORITIES.md define landing comercial/SEO de alta intenção como P1 e expansão editorial como P2 após os gates principais.
- BLOCKERS.md não espelha issue #643, que continua OPEN. Não editei arquivo de W00.
- W2 está AVAILABLE; W1 está BLOCKED por mídia pública; W3 já encaminhou a landing de produtores por PR #724.
- O claim ativo W2 de SEO da landing/PR #727 foi mantido aberto; apenas atualizei a evidência de CI.

## Confirmado
- Quatro artigos existentes: ingresso QR (10/11), descoberta de eventos (11/11), check-in QR para produtores (13/11) e line-up (14/11). Nenhum tem ID de CMS ou publicação confirmada nos worklogs consultados.
- Na main, BlogArticlePage.js (blob 95a8cac0e95f7c020a64b0f46594d8638f57feb9) não renderiza links Markdown clicáveis.
- PR #722 permanece OPEN; sua branch está atrás da main conforme o corpo do PR. O branch do PR contém BlogInlineText.js (blob 3c06fc136d81ede72f5c46389aa2cb35741c74b6), com links internos/externos seguros. Os últimos runs registrados no PR (39959804379 e 39959804361) passaram, mas não comprovam checks de um HEAD atualizado.
- PR #724 e #727 permanecem OPEN. Os jobs de #727 foram consultados: Validate 41459268768 SUCCESS e Lighthouse 41459268813 SUCCESS. #727 depende de #724 ou do mesmo release.
- Issue #643 permanece OPEN e documenta que Nginx/HTTPS serve SHA diferente do release no filesystem.
- A pesquisa pública desta rodada não retornou página de evento Cutinapp verificável. Não concluí que não existam eventos; apenas não usei exemplos sem evidência.
- Não houve acesso ao CMS, Search Console ou telemetria de conversão.

## Hipótese
Publicar primeiro os dois guias de produtores pode aproximar o tráfego editorial da ação comercial e da ativação, enquanto os guias de participantes devem aguardar inventário e páginas de evento verificáveis. Não há dados de uplift.

## Trabalho realizado
1. Revalidei o claim ativo de W2 para a landing de produtores e confirmei que os jobs Validate e Lighthouse de #727 terminaram com SUCCESS; #724 continua aberto.
2. Comparei o renderizador de artigos na main com o conteúdo do PR #722 e confirmei a dependência para links Markdown clicáveis.
3. Consolidei os quatro artigos existentes sem reescrevê-los.
4. Defini ordem de publicação: check-in produtor → line-up produtor/artista → descoberta participante → ingresso QR participante.
5. Criei mapa de interlinks e CTAs condicionado a runtime GO, integração de PRs e existência de URLs reais.
6. Defini critérios de CMS, canonical, OG, BlogPosting, HTML inicial, mobile, sitemap e Search Console.
7. Registrei handoff objetivo para W00, W09 e operador editorial.

## Entregável
deliverables/AUX-03/20261115-AUX-03-publicacao-cluster-conteudo-cutinapp.md

## Canal
Google Search → artigo Cutinapp → link contextual → página pública de evento ou landing de produtor → cadastro/checkout.

## CTA
- Produtor: Cadastrar minha produção → /for-producers, somente após #724/#727 integrados e runtime GO.
- Participante: Explorar eventos → /eventos, somente após runtime GO e inventário verificável.
- Métrica principal: produtores atribuídos ao conteúdo que publicam o primeiro evento em até 7 dias.

## Métricas
article_primary_cta_click; article_related_link_click; producer_signup; first_event_published_7d; event_detail_view; checkout_started; Search Console impressions/clicks/CTR. Baseline N/D.

## Evidências
- PR #722: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722
- PR #724: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- PR #727: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/727
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- BlogArticlePage main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/blog/BlogArticlePage.js
- PR #722 BlogInlineText: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/722/files
- Quatro artigos: links listados no entregável.

## Próxima ação
W00/conta principal resolver #643 e coordenar #722/#724/#727; W09 confirmar snapshots do blog; operador editorial criar rascunhos e retornar IDs/URLs; AUX-03-W2 validar SEO após runtime GO.

## Precisa da conta principal?
SIM — runtime público, integração dos PRs e autorização de publicação no CMS.

## Estado final
PUBLICATION_PLAN_READY — EXISTING_CONTENT_REUSED — NO_NEW_ARTICLE — NOT_PUBLISHED — NOT_INDEXED — NO_SOCIAL_SCHEDULED — NO_PRODUCT_CODE_CHANGED — NO_BRANCH — NO_MERGE — NO_DEPLOY — NO_VPS — CONVERSION_NOT_MEASURED.
