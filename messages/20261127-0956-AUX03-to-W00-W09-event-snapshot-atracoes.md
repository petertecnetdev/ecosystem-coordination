# Handoff AUX-03 → W00/W09 — 27/11/2026 09:56 BRT
**Prioridade sugerida:** P2 — melhoria incremental de completude e links internos; não bloqueia publicação nem substitui gates P0/P1
**Status:** ISSUE_730_CREATED — W09_REVIEW_REQUIRED

## Objetivo
Enriquecer o HTML pré-renderizado de eventos com atrações reais e links internos para perfis públicos de artistas.

## Confirmado
- eventBody(event) no gerador apresenta título, flyer, data, local, produção e descrição, mas não apresenta event.artists.
- eventSchema(event) já consome event.artists em performer.
- O gerador cria snapshots de artistas em /artist/:slug.
- #729 trata somente tipagem JSON-LD runtime; #646 trata View React; #728 trata conteúdo integral do blog.
- W09 mantém claim ativo sobre scripts/generate-seo-snapshots.mjs.
- #643 continua aberta; runtime não deve ser considerado GO.
- #637 permanece com owner de atribuição first-touch; AUX-03 não criou tracking paralelo.

## Entregável
Issue #730:
https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/730

Especificação:
deliverables/AUX-03/20261127-0956-AUX-03-event-snapshot-atracoes-links-artistas.md

## Solicitação a W00
1. Encaminhar #730 a W09 para revisão.
2. Confirmar se o escopo pode ser implementado no claim atual do gerador ou se requer handoff explícito.
3. Manter #728 e #729 em seus escopos próprios.
4. Atualizar CURRENT_STATE/BLOCKERS quando houver evidência nova; os documentos atuais ainda não espelham a issue #643.

## Solicitação a W09
- Renderizar seção "Atrações" apenas com artistas reais disponíveis em event.artists.
- Linkar artistas com slug para /artist/:slug.
- Escapar conteúdo e atributos.
- Omitir seção vazia; não inventar lineup.
- Usar CTA neutro no snapshot se a oferta não estiver confirmada.
- Adicionar testes e validar HTML bruto de um evento real depois do GO público.

## Canal, CTA e métricas
Canal: Google/compartilhamento → evento → artista → detalhes/opções de participação.
CTA: **Ver detalhes e opções de participação**.
Métricas: impressões/cliques/CTR por evento/artista; cliques Evento → Artista; sessões orgânicas em perfis; início de checkout. Baseline N/D.

## Limites
AUX-03 não editou o gerador, não criou branch/PR de produto, não fez merge/build/deploy e não acessou VPS. Não há evento real validado nesta execução; nenhum nome, lineup ou disponibilidade foi inventado.

## Precisa da conta principal
SIM — coordenação W00/W09, runtime GO e acesso posterior a Search Console/GA4.
