# AUX-03 — Worklog 2026-11-14 10:23 BRT — Guia SEO de line-up e descoberta de artistas

## Objetivo
Criar um ativo editorial original para aquisição de produtores e distribuição entre artistas, sem repetir os materiais de check-in QR, ingresso digital, busca por eventos, página do evento ou prospecções recentes.

## Área
SEO editorial, páginas públicas, aquisição de produtores, distribuição e descoberta de artistas.

## Coordenação consultada
- Li `CURRENT_STATE.md`, `PRIORITIES.md`, `BLOCKERS.md` e `COMMANDS.md`.
- Consultei diretórios de claims ativos/concluídos, worklogs, mensagens e entregáveis AUX-03.
- Consultei os claims e worklogs de 13/11 (Funclube) e 14/11 (Noite Infame) para evitar duplicar prospecção.
- `CURRENT_STATE.md` permanece consolidado em 30/10; complementei com o estado direto de issue #643, PRs #722 e #724–#727, código na main e Metricool.
- Issue #643 permanece OPEN. PR #722 permanece OPEN; PRs #724–#726 OPEN; PR #727 OPEN/Draft e dependente de #724 ou do mesmo release.
- A claim ativa `20261008-1600-AUX-03-W2-seo-public-discovery.md` trata da landing de produtores e do PR #727; este artigo evergreen de line-up não altera nem duplica esse escopo.
- A alocação global CMD-008 mantém W09 como owner do gerador/SEO compartilhado; AUX-03 não editou esses arquivos.

## Oportunidade
O produto já possui um fluxo de line-up com convites, aceite explícito, tipo de participação, palco, horário previsto, ordem, atração principal e descrição. A página pública do evento apresenta os artistas retornados pelo endpoint público e liga os cards aos perfis artísticos.

Isso permite um conteúdo que atende uma intenção específica de produtor e cria um ciclo de descoberta: produtor organiza line-up → evento apresenta artistas → visitante acessa perfis → artista pode compartilhar o evento.

## Confirmado — evidências de código na main
- `src/pages/event/EventLineupPage.js`: pesquisa perfil, convite por e-mail quando não há conta, aceite explícito, participação, palco, horário, ordem, headliner e descrição; existe ação para gerar descrição com IA.
- `src/pages/event/EventViewPage.js`: chama `publicEventArtists(slug)`, renderiza seção Line-up e navega para `/artist/:slug`.
- `src/services/CutinappService.js`: método `publicEventArtists` consulta `/events/public/:slug/artists`.
- `src/pages/artist/ArtistViewPage.js`: tipos `solo`, `band`, `duo`, `group`, `collective`, `orchestra`.
- `src/utils/eventSeo.js`: já adiciona `performer` no JSON-LD de Event, mas serializa todos os artistas como `MusicGroup`.
- Google Search Central aceita `Person` ou `PerformingGroup` para `performer` e recomenda URL única por evento: https://developers.google.com/search/docs/appearance/structured-data/event

## Recomendação específica para W09
Revisar `eventPerformers` para mapear `artist_type=solo` como `Person` e tipos coletivos como `MusicGroup`/tipo de grupo apropriado. Confirmar que `response.event.artists` usado no JSON-LD contém somente artistas publicamente confirmados e é consistente com o endpoint público que alimenta a seção Line-up. Não foi feita alteração de código; a claim/ownership de SEO compartilhado permanece com W09.

## Entregável
`deliverables/AUX-03/20261114-AUX-03-guia-lineup-artistas-divulgacao.md`

Inclui artigo completo, metadados SEO, mapa de links internos, carrossel, Reel, Stories, resposta de Direct, CTA, métricas e gate de publicação.

## Canal, CTA e métrica
- Canal primário: blog Cutinapp.
- Canais derivados: Instagram carrossel, Reel e Stories.
- CTA editorial: Conhecer a Cutinapp para produtores (`/for-producers`, somente após GO).
- CTA social: salvar/compartilhar o checklist; palavra LINE-UP no Direct se houver equipe disponível.
- Métrica principal: produtores qualificados originados pelo artigo que publicam o primeiro evento em até 30 dias / produtores qualificados originados pelo artigo.
- Indicadores: sessões orgânicas, CTR, clique CTA, respostas LINE-UP, demonstrações aceitas, produções criadas, convites e aceite de artistas.
- Baseline: N/D.

## Runtime e distribuição
- Home pública retorna página que pede JavaScript; `/for-producers` e `/eventos` não foram acessíveis pela ferramenta de pesquisa. Isso não comprova indisponibilidade universal.
- Issue #643 permanece aberta e bloqueia GO.
- PR #722 de links editoriais clicáveis continua aberto.
- Metricool marca Cutinapp (ID 7119630) tem `gbpData`, mas não `instagramData`; agenda de 14–21/11 vazia.
- Não foi possível verificar evento atual publicado na própria Cutinapp; artigo evergreen não usa exemplos inventados.

## Próxima ação
1. Conta principal/infra resolve #643 e comprova release pública.
2. W00 coordena #722 e #724–#727.
3. W09 revisa performer schema e coerência entre JSON-LD e line-up público.
4. Operador editorial cadastra rascunho, adiciona links reais e valida canonical/OG.
5. AUX-03 distribui após GO e mede o funil.

## Precisa da conta principal?
SIM — runtime público, aprovação dos PRs de aquisição e autorização de publicação/distribuição social.

## Estado
`ARTICLE_READY — SOCIAL_COPY_READY — W09_SEO_HANDOFF_PENDING — NOT_PUBLISHED — NOT_INDEXED — NOT_SCHEDULED — NO_PRODUCT_CODE — NO_MERGE — NO_DEPLOY`.
