# AUX-03 — 27/11/2026
## Enriquecimento SEO dos snapshots públicos de eventos

**Objetivo:** tornar as páginas pré-renderizadas de eventos mais úteis para descoberta orgânica e compartilhamento, exibindo atrações reais e conectando cada artista ao seu perfil público.

## Área
SEO editorial e técnico de páginas públicas, links internos, descoberta de artistas, distribuição de eventos e conversão de participantes.

## Oportunidade
O HTML estático de evento já apresenta título, flyer, data, local, produção e descrição. O JSON-LD também recebe `event.artists` em `performer`, mas o corpo visível do snapshot não apresenta essa programação como texto nem oferece links para os perfis de artistas.

Isso cria uma diferença entre o contexto estruturado e o conteúdo visível do snapshot, além de perder a ligação interna Evento ↔ Artista.

## Confirmado
- `scripts/generate-seo-snapshots.mjs` contém `eventBody(event)`.
- `eventBody` renderiza H1, flyer, data, local, produção, descrição e CTA; não renderiza a lista de artistas.
- `eventSchema(event)` já lê `event.artists` e gera `performer`.
- `fetchAllEvents()` solicita `view=full`; o gerador também materializa snapshots públicos de artistas em `/artist/:slug`.
- A issue #729 trata exclusivamente da tipagem de performers no JSON-LD runtime em `src/utils/eventSeo.js`.
- A issue #646 trata da View/Create/Edit React; esta entrega não altera a composição visual React.
- O gerador permanece sob ownership ativo de W09. A issue #730 é handoff, não autorização para AUX-03 editar o gerador.

## Hipótese
Exibir atrações reais em texto e ligar seus nomes aos perfis públicos pode ampliar a relevância contextual das páginas de evento, melhorar a navegação entre entidades e criar mais caminhos de descoberta. Não há evidência de ganho de ranking ou conversão ainda.

## Trabalho realizado
1. Consultei CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
2. Consultei os worklogs, claims, entregáveis e handoffs AUX-03 de 25 e 26/11.
3. Revalidei as issues #636, #637, #643, #646, #728 e #729.
4. Confirmei os PRs #722, #724 e #727 ainda abertos; #727 permanece Draft.
5. Consultei o claim ativo W09 e preservei o ownership de `scripts/generate-seo-snapshots.mjs`.
6. Inspecionei `eventBody`, `eventSchema`, `fetchAllEvents` e a geração de snapshots de artistas.
7. Criei a issue #730 com escopo restrito ao HTML visível do snapshot de evento, critérios de segurança e testes.
8. Não alterei código, não criei branch/PR de produto, não fiz merge/build/deploy e não acessei a VPS.

## Entregável
Issue #730 — [SEO] Enriquecer snapshots de eventos com atrações e links para artistas:
https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/730

### Correção solicitada
- Renderizar seção "Atrações" quando existirem artistas válidos no inventário do evento.
- Linkar artistas com slug para `/artist/:slug`; sem slug, mostrar somente o nome.
- Escapar nomes e atributos; não inserir HTML arbitrário.
- Omitir a seção quando não houver lineup; não inventar artistas.
- Preservar os metadados, canonical, flyer, produção e JSON-LD atuais.
- Usar CTA neutro "Ver detalhes e opções de participação", salvo quando o inventário confirmar oferta ativa.
- Cobrir múltiplos artistas, nomes com caracteres especiais, ausência de slug e lista vazia nos testes.

## Canal e CTA
**Canal:** Google Search e compartilhamento de evento → página pública do evento → perfil do artista → evento e opções de participação.

**CTA:** Ver detalhes e opções de participação. A página transacional deve apresentar compra/inscrição somente quando a disponibilidade real estiver confirmada.

## Métricas
- Impressões, cliques e CTR orgânicos por URL de evento e perfil de artista.
- Cliques Evento → Artista.
- Sessões orgânicas em perfis de artistas.
- Intenção de compra e início de checkout, quando já instrumentados.

**Baseline:** N/D. Não houve acesso ao Search Console ou GA4 nesta execução.

## Evidências
- Código: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- Issue #730: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/730
- Issue #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- Issue #728: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
- Issue #646: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/646
- Claim W09: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md

## Próxima ação
W00 encaminhar a issue #730 a W09 para revisão e implementação dentro do ownership existente. Após runtime GO, validar o HTML bruto de uma página real de evento e acompanhar cliques Evento → Artista e tráfego orgânico.

## Precisa da conta principal
**SIM** — coordenação/aceite de W00 e W09, GO do runtime e acesso posterior ao Search Console/GA4.

## Estado
ISSUE_730_CREATED — SNAPSHOT_ARTIST_LINKS_SPECIFIED — W09_OWNERSHIP_PRESERVED — NOT_IMPLEMENTED — NOT_DEPLOYED — NOT_INDEXED_VERIFIED.
