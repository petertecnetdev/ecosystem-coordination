# AUX-03 W2 — Enriquecimento SEO das páginas públicas de artistas

**Data:** 16/11/2026 11:09 BRT  
**Worker:** AUX-03-W2 — SEO, Blog & Public Discovery  
**Prioridade:** P1/P2 — descoberta orgânica e distribuição entre artista, evento e produção  
**Estado:** SPEC_READY — HANDOFF_W09 — NOT_IMPLEMENTED

## 1. Objetivo

Aumentar a utilidade orgânica das páginas públicas de artistas, conectando cada perfil aos próximos eventos confirmados e às produções relacionadas. A página de artista deve funcionar como ponto de descoberta, não apenas como uma ficha com nome, imagem e biografia.

Esta entrega amplia o handoff de 14/11 sobre o tipo de performer no Schema.org. Não cria outro artigo nem duplica o cluster editorial já preparado.

## 2. Coordenação consultada

- `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md`, `orchestration/STATE.md`, `orchestration/WORKER_REGISTRY.md`, `orchestration/assignments/AUX-03/W2.md`.
- Worklogs e entregáveis AUX-03 de 10–16/11, incluindo o cluster de publicação de 15/11 e o prospecto W3 de 16/11.
- Claims ativos W2 e W09.
- Issue Cutinapp #643 e PRs #722, #724, #725, #726 e #727.
- Main do frontend no SHA `9b5502cdf2dca098bc73a465d58d7274b596d0a4`.

Ownership: W09 mantém o gerador `scripts/generate-seo-snapshots.mjs`. Esta entrega é uma especificação/handoff e não reivindica nem altera arquivos de produto.

## 3. Confirmado — implementação atual

### Dados disponíveis na página

- `src/pages/artist/ArtistViewPage.js` carrega `cutinappService.publicArtist(slug)`.
- O componente consome `artist`, `origin_organization`, `event_summary`, `upcoming_events`, `past_events` e `pending_events`.
- A página diferencia participações confirmadas e pendentes; a lista de próximos eventos usa cartões com título, data, local/cidade e produção.
- `src/services/CutinappService.js` implementa `publicArtist(slug)` em `GET /artists/{slug}`.

### Snapshot de crawler na main

Em `scripts/generate-seo-snapshots.mjs`:

- `fetchAllArtists()` consulta a listagem pública `/artists`.
- `buildArtistSnapshot()` gera `ProfilePage`, mas fixa `mainEntity.@type = Person` para todo perfil.
- O HTML inicial do snapshot contém apenas link para `/artists`, H1, imagem e descrição.
- Não inclui os próximos eventos confirmados, links para eventos ou links para as produções relacionadas.
- O snapshot não usa `artist_type` para diferenciar artista solo de formação coletiva.
- `eventSchema()` classifica todos os performers como `MusicGroup`, independentemente de `artist_type`.

Referências de código:
- [ArtistViewPage.js](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/pages/artist/ArtistViewPage.js)
- [CutinappService.js](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/src/services/CutinappService.js)
- [generate-seo-snapshots.mjs — buildArtistSnapshot](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L476-L501)
- [generate-seo-snapshots.mjs — eventSchema performer](https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs#L330-L341)

## 4. Oportunidade

Uma pessoa que pesquisa o nome de um artista pode estar procurando biografia, agenda, apresentações futuras, local e ingressos. O snapshot atual entrega apenas parte dessa intenção, mesmo quando a página React possui dados de eventos e produções.

A oportunidade é criar uma trilha rastreável:

**Busca pelo artista → perfil público → próximo evento confirmado → página do evento → ingresso/checkout.**

Isso também cria links internos bidirecionais entre perfis artísticos, eventos e produções, usando apenas relacionamentos públicos reais.

## 5. Recomendação para W09

### 5.1 Enriquecer o snapshot com dados públicos do artista

Usar o endpoint já consumido pelo frontend, `GET /artists/{slug}`, para obter o detalhe público por artista. Se necessário, usar concorrência limitada e falha isolada por perfil; uma falha em um artista não deve cancelar toda a geração de snapshots.

### 5.2 Conteúdo HTML inicial

Para cada artista publicado, incluir:

1. H1 com nome artístico.
2. Tipo de perfil (solo, banda, duo, grupo, coletivo ou orquestra).
3. Biografia pública, sem substituir conteúdo ausente por texto promocional genérico.
4. Até três próximos eventos **confirmados e públicos**, ordenados por data.
5. Em cada evento: título, data/hora, local/cidade quando públicos e link para `/event/{slug}`.
6. Link para `/production/{slug}/public` quando houver produção pública relacionada.
7. CTA contextual: **Ver evento e ingressos**; se não houver próximo evento, **Conhecer o perfil e compartilhar**.

Não incluir `pending_events`, convites privados, dados de participantes ou eventos sem autorização/publicação pública. Não criar nomes, datas, locais, preços ou links presumidos.

### 5.3 Schema.org

- Artista solo: `Person` em `ProfilePage.mainEntity`.
- Banda/duo/orquestra: `MusicGroup` quando a natureza musical estiver confirmada.
- Grupo/coletivo de natureza não musical ou indeterminada: `PerformingGroup` quando adequado; não inferir gênero ou natureza a partir apenas do nome.
- No `Event.performer`, usar `Person` ou `PerformingGroup` conforme o tipo real do perfil.
- Manter nome, URL e demais propriedades coerentes com o conteúdo visível.
- Incluir `sameAs` somente para URLs públicas HTTP/HTTPS validadas.

Google documenta `performer` como `Person` ou `PerformingGroup` e exige que cada evento tenha URL própria e página focada naquele evento: https://developers.google.com/search/docs/appearance/structured-data/event. Schema.org define `MusicGroup` como subtipo de `PerformingGroup`: https://schema.org/MusicGroup.

### 5.4 Indexabilidade

Evitar indexar perfis vazios que só tenham um nome e descrição genérica. Propor um guard de conteúdo mínimo baseado em dados públicos diferenciadores (por exemplo, biografia útil, imagem, links públicos ou participações confirmadas). Perfis sem conteúdo suficiente devem receber `noindex,follow`; não inventar um limite numérico sem amostra real.

### 5.5 Metadados e compartilhamento

- Title: nome artístico + tipo/localidade somente quando públicos e relevantes + Cutinapp.
- Description: bio curta e, quando existir, próximo evento confirmado.
- Canonical: `/artist/{slug}`.
- OG/Twitter: foto/capa real do perfil, alt text descritivo e URL canônica.
- O HTML inicial deve conter os mesmos eventos que o snapshot declara; o JSON-LD não pode anunciar participação pendente.

## 6. Critérios de aceite

1. Fixture de artista solo com próximo evento confirmado gera `Person` e link do evento.
2. Fixture de banda gera `MusicGroup` ou `PerformingGroup` conforme classificação confirmada.
3. Fixture de coletivo/grupo não musical não é rotulada automaticamente como `MusicGroup`.
4. Evento pendente não aparece no HTML nem no Schema.org.
5. Perfil sem conteúdo público suficiente recebe `noindex,follow`.
6. Cada evento listado aponta para URL única `/event/{slug}`; produção relacionada aponta para a página pública correta.
7. Canonical, OG, Twitter, imagem e alt text são consistentes.
8. Falha de consulta de um perfil não aborta o lote completo.
9. Testar `npm run smoke:seo-global`, o guard de indexabilidade disponível e validação de Rich Results/URL Inspection após deploy.
10. Comparar snapshot gerado com o conteúdo visível em mobile para evitar divergência crawler/usuário.

## 7. Hipótese e mensuração

**Hipótese:** perfis artísticos mais completos podem captar buscas por nome de artista e encaminhar visitantes para eventos reais, ampliando a distribuição orgânica sem depender apenas de artigos.

Métricas:
- Impressões, cliques e CTR no Search Console para `/artist/*`.
- Sessões orgânicas por perfil.
- Cliques do perfil para páginas de evento.
- Visualizações de evento originadas de perfil artístico.
- Inícios de checkout atribuídos à origem `artist_profile`, se a telemetria existente permitir.

Baseline: N/D. Não há dados de Search Console ou conversão disponíveis nesta execução.

## 8. Canal, CTA e próxima ação

- **Canal:** Google Search → perfil público do artista → evento → checkout.
- **CTA primário:** Ver evento e ingressos.
- **Métrica principal:** cliques de perfil artístico para evento confirmado por sessão orgânica de perfil.
- **Próxima ação:** W09 avaliar e implementar a extensão sob o claim existente do gerador; W00 coordenar prioridade e revisão.
- **Conta principal:** necessária para integração, liberação do runtime e validação pública.

## 9. Limites desta execução

- Nenhum código de produto foi alterado.
- Nenhuma branch ou PR de produto foi criada.
- Nenhum snapshot foi gerado em build de produção.
- Nenhuma URL artística foi validada no runtime público.
- Nenhuma publicação ou indexação foi declarada.
