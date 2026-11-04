# Handoff AUX-03 W3 → W00 — 2026-11-04

## Entrega
Runbook de go-live para converter os ativos de aquisição já prontos em distribuição, leads qualificados e publicação do primeiro evento.

**Entregável:** deliverables/AUX-03/20261104-W3-producer-funnel-go-live-runbook.md  
**Worklog:** worklogs/20261104-0951-AUX-03-W3-producer-funnel-go-live.md  
**Claim:** claims/completed/20261104-0951-AUX-03-W3-producer-funnel-go-live.md

## Confirmado
- Stories W1 de 03/11 seguem sem publicação/Insights confirmados; playbook W3 de Direct está pronto, mas nenhuma DM foi enviada.
- Metricool brand 7119630 retorna somente gbpData, sem instagramData; agendamentos 04/11–11/11 vazios.
- PR #724/#725/#726: open, mergeable, not merged, ready-for-review. PR #727: open, mergeable, draft, not merged; depende de #724.
- Configuração comercial da API: subscription_enabled=false, monetization_model=transaction_fee, plans=[]; não há percentual de taxa no bloco consultado.
- Busca pública não localizou página de evento Cutinapp indexada nesta execução; isso não prova ausência de eventos no banco.
- A raiz da SPA retorna instrução para ativar JavaScript no crawler; /for-producers não foi recuperada pela ferramenta. Isso não prova indisponibilidade em navegador real.

## Hipótese
A maior barreira demonstrável agora é execução/distribuição e caminho público não validado. Produzir novas peças antes de publicar os ativos já preparados não resolve a ausência de dados de alcance, leads e ativação.

## Ação solicitada à conta principal
1. Revisar e validar #724, #725 e #726 em smartphone real; decidir integração.
2. Integrar #727 no mesmo release ou após #724, respeitando a dependência registrada.
3. Testar landing → cadastro/login → produção → evento → publicação com uma conta autorizada.
4. Publicar os três Stories W1 já preparados, inserir stickers nativos e registrar Insights após 24h.
5. Confirmar acesso autorizado ao Instagram Direct. AUX-03 responderá apenas a interações voluntárias e aplicará o playbook já entregue.
6. Não ampliar tráfego pago nem anunciar eventos sem uma página pública real e validada.

## CTA e métrica
- CTA: responder PREPARAR.
- Métrica principal: produtores qualificados que publicam primeiro evento em até 7 dias ÷ produtores qualificados que responderam à campanha.
- Baseline: N/D; nenhuma publicação/Insight/conversão foi comprovada.

## Estado
HANDOFF_REQUIRED — RUNBOOK_READY — STORIES_NOT_PUBLISHED — NO_DM_SENT — NO_PR_MERGE — NOT_DEPLOYED.