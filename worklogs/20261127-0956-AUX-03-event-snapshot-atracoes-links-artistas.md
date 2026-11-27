# AUX-03 — Worklog 2026-11-27 09:56 BRT
## Snapshots de eventos: atrações visíveis e links para perfis de artistas

## Objetivo
Melhorar a completude das páginas públicas pré-renderizadas de eventos e criar uma ligação interna verificável entre eventos e perfis de artistas, sem duplicar o trabalho de SEO global de W09.

## Área
SEO de páginas públicas, descoberta de artistas, links internos, compartilhamento e aquisição de participantes.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- Diretórios worklogs/, claims/active/, claims/completed/, deliverables/AUX-03/ e messages/.
- Registros AUX-03 de 25/11 e 26/11.
- Issues Cutinapp #636, #637, #643, #646, #728 e #729.
- PRs #722, #724 e #727.
- Claim ativo W09 de SEO global/snapshot generator.

## Confirmado
- CURRENT_STATE.md continua com consolidação de 30/10; PRIORITIES.md também apresenta alocação histórica de 30/10.
- BLOCKERS.md lista FIN-P0-001, mas não espelha a issue #643.
- Issue #643 continua aberta: o Nginx público serviu release antigo diferente do filesystem em evidência anterior. Não declarar runtime GO.
- Issue #728 permanece aberta e trata do conteúdo integral dos artigos nos snapshots do blog.
- Issue #729 permanece aberta e trata da tipagem do performer no JSON-LD runtime em src/utils/eventSeo.js.
- Issue #646 permanece aberta e trata da View/Create/Edit React, com Evento como prioridade visual.
- Issue #637 continua reservada à atribuição first-touch; não criar tracking paralelo.
- PR #722 permanece aberto; PR #724 permanece aberto; PR #727 permanece aberto e Draft.
- Claim ativo W09 mantém ownership de scripts/generate-seo-snapshots.mjs e helpers de SEO global.
- No gerador, eventBody(event) apresenta H1, flyer, data, local, produção, descrição e CTA, mas não apresenta event.artists como conteúdo visível.
- eventSchema(event) já consome event.artists para JSON-LD performer.
- fetchAllEvents() consulta o endpoint público com view=full; o gerador também cria snapshots individuais de artistas em /artist/:slug.
- O CTA estático do snapshot usa "Ver ingressos e detalhes do evento", sem que o corpo do snapshot valide estado de oferta.

## Hipótese
A exibição textual das atrações e links internos para perfis de artistas pode melhorar a completude contextual do HTML pré-renderizado, fortalecer a navegação Evento ↔ Artista e ampliar oportunidades de descoberta. Não há evidência de aumento de ranking, impressões ou conversão.

## Trabalho realizado
1. Comparei eventBody e eventSchema no gerador de snapshots.
2. Confirmei que os artistas já estão disponíveis no objeto de evento consumido pelo schema.
3. Diferenciei o escopo da issue #729 (JSON-LD runtime) e da #646 (View React).
4. Consultei o claim ativo W09 e preservei ownership do gerador.
5. Pesquisei issues abertas sobre snapshot, performer e Open Graph; não encontrei issue equivalente para o corpo visível do snapshot de evento.
6. Criei a issue #730 com requisitos de renderização, segurança, CTA neutro e testes.
7. Registrei entregável, claim e handoff no repositório de coordenação.

## Entregável
- Issue #730: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/730
- Documento: deliverables/AUX-03/20261127-0956-AUX-03-event-snapshot-atracoes-links-artistas.md

## Canal e CTA
Canal: Google/compartilhamento → página pública do evento → perfil de artista → detalhes e opções de participação.
CTA: **Ver detalhes e opções de participação**; não prometer ingressos/inscrições sem disponibilidade confirmada.

## Métrica
- Impressões, cliques e CTR por URL de evento e artista.
- Cliques de evento para perfil de artista.
- Sessões orgânicas em perfis de artistas.
- Intenção de compra/início de checkout se instrumentados.
Baseline: N/D.

## Evidências
- Issue #730 criada em 27/11/2026: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/730
- Gerador: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/blob/main/scripts/generate-seo-snapshots.mjs
- #728: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/728
- #729: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/729
- #646: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/646
- #643: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/643
- W09 active claim: https://github.com/petertecnetdev/ecosystem-coordination/blob/main/claims/active/20260930-0838-w09-seo-global-snapshot-root-cause.md

## Próxima ação
W00 encaminhar #730 a W09 para avaliação e implementação dentro do ownership existente. Depois do runtime GO, validar HTML bruto de um evento real em mobile e medir cliques Evento → Artista.

## Precisa da conta principal
SIM — coordenação W00/W09 e GO do runtime; Search Console/GA4 para mensuração posterior.

## Estado
ISSUE_730_CREATED — SPEC_RECORDED — W09_OWNERSHIP_PRESERVED — NOT_IMPLEMENTED — NOT_DEPLOYED.
