# AUX-03 — Worklog 2026-11-16 11:09 BRT — SEO das páginas públicas de artistas

## Objetivo
Transformar perfis públicos de artistas em pontos de descoberta orgânica conectados a eventos confirmados e produções públicas, sem criar artigo duplicado.

## Área
SEO técnico diretamente ligado à aquisição, páginas públicas, links internos, compartilhamento e conversão de participantes.

## Oportunidade
O perfil artístico já apresenta próximos eventos e produções relacionadas na experiência React, mas o snapshot de crawler na main contém somente nome, imagem e descrição. O HTML inicial perde os links para eventos que podem converter a busca pelo artista em visita ao evento e intenção de ingresso.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md, orchestration/STATE.md, orchestration/WORKER_REGISTRY.md e orchestration/assignments/AUX-03/W2.md.
- Worklogs/claims/entregáveis AUX-03 de 10–16/11.
- Claims ativos W2 e W09.
- Issue #643 e PRs #722, #724, #725, #726 e #727.
- W3 já registrou hoje o prospecto Undergoth; não repeti prospecção.
- O cluster editorial de quatro artigos permanece sem publicação comprovada; não criei outro artigo.
- W09 mantém ownership do gerador de snapshots. Esta execução produziu apenas especificação/handoff, sem alteração de código.

## Confirmado
- Frontend main SHA: 9b5502cdf2dca098bc73a465d58d7274b596d0a4.
- ArtistViewPage consome publicArtist(slug) e usa artist, origin_organization, event_summary, upcoming_events, past_events e pending_events.
- CutinappService.publicArtist consulta GET /artists/{slug}.
- buildArtistSnapshot em scripts/generate-seo-snapshots.mjs gera ProfilePage/Person, H1, imagem e descrição; não inclui eventos futuros, links de evento ou links de produção.
- eventSchema marca todos os artistas como MusicGroup, sem considerar artist_type.
- applySeo injeta `robots=index,follow` em todos os snapshots, sem guard específico para perfis artísticos sem conteúdo público diferenciador.
- ArtistViewPage diferencia solo, banda, duo, grupo, coletivo e orquestra e separa eventos confirmados de pendentes.
- Google documenta performer como Person ou PerformingGroup e requer URL própria por evento, com página focada no evento.
- Issue #643 permanece OPEN; consulta atual da raiz retornou HTTP 530. /artist e /blog não puderam ser abertas pela ferramenta.
- BLOCKERS.md ainda lista apenas FIN-P0-001 e não espelha #643; CURRENT_STATE.md está consolidado em 30/10.
- Busca de site: para páginas /artist, /production e /blog não retornou resultados nesta consulta; isso não comprova ausência de indexação.
- PRs #722, #724, #725 e #726 permanecem OPEN/não merged; #727 permanece OPEN/Draft.
- Metricool brand cutinapp (id 7119630) está em America/Sao_Paulo; networksData contém apenas gbpData, sem Instagram. Agenda 16–23/11 vazia.

## Hipótese
Snapshots de artista com biografia, próximos eventos confirmados e links de produção podem melhorar a cobertura de buscas por nome de artista e transferir tráfego para páginas de evento. Impacto ainda não medido.

## Trabalho realizado
1. Revalidei o estado de coordenação e ownership.
2. Li o código da página de artista, serviço público e gerador de snapshots na main.
3. Comparei o conteúdo renderizado na página com o HTML inicial gerado para crawler.
4. Identifiquei que o snapshot não inclui próximos eventos e relações públicas existentes na página.
5. Identifiquei que o Schema.org do perfil sempre usa Person e o performer de evento sempre usa MusicGroup, ignorando artist_type.
6. Preparei especificação de enriquecimento com eventos confirmados, links internos, tipos Schema.org, indexabilidade de perfis vazios, metadados e critérios de aceite.
7. Encaminhei a W09/W00 sem reivindicar o arquivo do gerador.
8. Revalidei bloqueios de runtime e PRs de aquisição.

## Entregável
deliverables/AUX-03/20261116-1109-AUX-03-enriquecimento-seo-perfis-artistas.md

## Canal
Google Search → perfil público do artista → página de evento → checkout.

## CTA
**Ver evento e ingressos**, somente quando existir evento público confirmado. Sem evento futuro, manter CTA de perfil/compartilhamento, sem prometer disponibilidade.

## Métrica
Cliques de perfil artístico para evento confirmado por sessão orgânica de perfil; secundárias: impressões, cliques e CTR de /artist/* no Search Console, visualizações de eventos e checkout iniciado atribuído.

Baseline: N/D.

## Evidências
- ArtistViewPage: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/artist/ArtistViewPage.js
- CutinappService: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/services/CutinappService.js
- buildArtistSnapshot: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L476-L501
- eventSchema performer: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L330-L341
- Google Event structured data: https://developers.google.com/search/docs/appearance/structured-data/event
- Issue #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- PRs: #722, #724, #725, #726, #727.

## Próxima ação
W09 avaliar o escopo e implementar sob seu ownership existente; W00 coordenar prioridade e revisão; conta principal/infra resolver #643 e fornecer evidência de runtime GO; depois validar snapshots em Rich Results/URL Inspection e medir GSC.

## Precisa da conta principal
SIM — para integração, runtime público, validação em navegador e acesso/medição de Search Console.
