# Handoff AUX-03/W2 → W09/W00 — Enriquecimento SEO dos perfis artísticos

**Data:** 16/11/2026 11:09 BRT  
**Origem:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Destino:** W09 (ownership do gerador) e W00 (coordenação)

## Pedido
Avaliar e priorizar o enriquecimento dos snapshots públicos de artistas com próximos eventos confirmados e links para produções públicas. A especificação é aditiva ao handoff de 14/11 sobre tipos de performer; não solicita um novo artigo nem transfere ownership.

## Evidência na main
SHA: `9b5502cdf2dca098bc73a465d58d7274b596d0a4`.

- `ArtistViewPage.js` consome `upcoming_events`, `past_events`, `pending_events`, `event_summary` e produções relacionadas.
- `CutinappService.publicArtist(slug)` chama `GET /artists/{slug}`.
- `buildArtistSnapshot()` no gerador inclui somente nome, foto e descrição; não liga para eventos/produções.
- `eventSchema()` usa `MusicGroup` para todos os performers, sem consultar `artist_type`.
- A página React diferencia participações confirmadas e pendentes; snapshots não devem incluir pending_events.

## Mudança proposta
1. Obter detalhe público de cada artista via endpoint já consumido pelo frontend, com concorrência limitada e falha isolada.
2. Renderizar até três próximos eventos confirmados com data, título, local/cidade públicos e âncoras para `/event/{slug}`.
3. Incluir link para `/production/{slug}/public` quando a relação for pública.
4. Mapear `artist_type` para Person/MusicGroup/PerformingGroup sem inferir natureza musical não confirmada.
5. Enriquecer title, description, canonical, OG/Twitter, alt text e ProfilePage JSON-LD.
6. Aplicar guard de indexabilidade a perfis sem conteúdo público diferenciador.
7. Testar que eventos pendentes nunca aparecem no HTML ou JSON-LD.

## Por que importa
A busca por nome de artista pode chegar diretamente a um perfil, mas o snapshot atual não entrega a agenda que a página React já apresenta. Links para eventos confirmados criam caminho orgânico até a página de ingresso e fortalecem a relação artista → evento → produção.

## CTA e métrica
- CTA: **Ver evento e ingressos** para evento público confirmado.
- Métrica principal: cliques do perfil para evento por sessão orgânica de perfil.
- Secundárias: impressões/cliques/CTR de /artist/*, visualizações de evento e checkout iniciado atribuído.

## Critérios de aceite
Ver entregável completo: `deliverables/AUX-03/20261116-1109-AUX-03-enriquecimento-seo-perfis-artistas.md`.

## Gate
Issue #643 continua OPEN. Consulta de 16/11 à raiz pública retornou HTTP 530; /artist e /blog não puderam ser abertas. PRs #722/#724/#725/#726 OPEN; #727 OPEN/Draft. Nenhum link de conversão deve ser distribuído até runtime GO. Nenhuma publicação/indexação foi comprovada.

## Ownership
W09 mantém `scripts/generate-seo-snapshots.mjs`. AUX-03-W2 não reivindica esse arquivo e não fez alteração de produto.

## Próxima ação
W09 revisar e aceitar/rejeitar escopo; W00 coordenar prioridade; conta principal/infra resolver #643 e validar runtime; depois Rich Results/URL Inspection e Search Console.

**Precisa da conta principal:** SIM — integração, runtime GO e acesso a evidências públicas/medição.
