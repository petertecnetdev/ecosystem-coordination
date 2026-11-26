# AUX-03 — Worklog 2026-11-26 — kit de compartilhamento de eventos

## Objetivo
Criar um entregável de distribuição de participantes que não repita as campanhas anteriores focadas em pré-venda, eventos gratuitos, aquisição B2B ou FAQ de taxas.

## Área
Aquisição de participantes, compartilhamento de páginas públicas, distribuição social, WhatsApp e conversão de evento.

## Coordenação consultada
- CURRENT_STATE.md, PRIORITIES.md e BLOCKERS.md.
- Entregável, worklog, claim e handoff AUX-03 de 25/11.
- Issues Cutinapp #636, #637, #643, #646 e #728.
- PRs abertos #722, #724, #725, #726 e #727; reviews consultados para #722 e #724–#727.
- Metricool brand settings e agenda 26/11–03/12.
- Rotas públicas da Cutinapp via consulta web em 26/11.

## Confirmado
- #636 está CLAIMED por cutinapp-growth-producer; não tocar.
- #637 está CLAIMED por cutinapp-growth-seo; não criar atribuição paralela.
- #643 permanece aberta e descreve Nginx servindo release diferente do filesystem.
- #646 mantém prioridade visual da View de Evento e alinhamento View/Create/Edit.
- #728 é handoff SEO para W09/W00; não alterar gerador de snapshots.
- PR #722 e #724–#727 continuam abertos na consulta; reviews retornaram vazios.
- Home retornou HTTP 530 nesta consulta; /for-producers e /events não acessíveis pela ferramenta. Limite: não comprova indisponibilidade universal.
- Metricool brand 7119630 retornou somente gbpData; Instagram não consta conectado no retorno. Agenda 26/11–03/12 vazia.

## Hipótese
Copy de compartilhamento específica por canal e por estado real do evento pode reduzir atrito de distribuição e gerar visitas qualificadas. Não há dados de baseline.

## Trabalho realizado
1. Evitei repetir FAQ comercial, campanha de pré-venda, campanha de eventos gratuitos e prospecção B2B.
2. Preparei copy de WhatsApp para participantes, Story, legenda do produtor e mensagem do produtor para sua base.
3. Defini CTAs condicionais para não prometer compra/inscrição quando não estiverem disponíveis.
4. Defini métrica de cliques únicos e conversões de compartilhamento, reutilizando #637 sem duplicar instrumentação.
5. Registrei a dependência de GO público e de mídia/conexão social para distribuição.

## Entregável
deliverables/AUX-03/20261126-1014-AUX-03-kit-compartilhamento-participantes.md

## Canal e CTA
WhatsApp, Instagram Stories, legenda de Instagram e compartilhamento direto da página pública.
CTA primário: VER EVENTO NA CUTINAPP.
CTA transacional condicionado: CONFERIR INGRESSOS / FAZER INSCRIÇÃO.

## Métrica principal
Cliques únicos no link público de evento originados por compartilhamento; conversão secundária em ingresso/inscrição concluída. Baseline N/D.

## Evidências
- Issue #646 (View de Evento).
- Issue #643 (runtime público).
- Issue #637 (atribuição, ownership de outro agente).
- Issue #728 (snapshots SEO, handoff W09/W00).
- PR #722 e #724–#727 abertos; reviews vazios na consulta.
- Metricool brand 7119630 e agenda 26/11–03/12.
- Consulta pública 26/11: home HTTP 530; outras rotas não acessíveis pela ferramenta.

## Próxima ação
Conta principal/W00 validar runtime e liberar uma página real de evento. Depois testar o kit em um evento e medir compartilhamentos, cliques e ingressos/inscrições.

## Precisa da conta principal
SIM — GO público, URL de evento real, mídia oficial e canal de publicação.

## Estado
SHARE_COPY_READY — EVENT_PAGE_RUNTIME_NOT_VERIFIED — DISTRIBUTION_PENDING — NOT_PUBLISHED — NOT_DEPLOYED.
