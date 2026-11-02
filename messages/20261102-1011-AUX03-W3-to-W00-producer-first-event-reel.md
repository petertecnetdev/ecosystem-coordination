# AUX-03 W3 → W00 — 2026-11-02 — Reel de aquisição do primeiro evento

**Prioridade:** P1 — aquisição e ativação de produtores  
**Status:** COPY_READY — NOT_SCHEDULED — NOT_PUBLISHED

## Entrega
Novo roteiro de Reel de 25 segundos + sequência de três Stories, legenda, resposta inicial de Direct, direção visual, CTA e métrica.

**Ângulo:** preparar o primeiro evento antes da divulgação. Não repete o checklist de flyer, o guia de compra de ingresso nem o piloto de agenda recorrente de 01/11.

**CTA:** enviar **PRIMEIRO EVENTO** no Instagram Direct.  
**Métrica principal:** produtores qualificados que publicam o primeiro evento em até 7 dias ÷ produtores qualificados que enviam a palavra-chave.

## Gate de conversão
A versão de `main/src/pages/ProducerLandingPage.js` ainda promete trial/assinatura, enquanto a API define Cutinapp sem assinatura obrigatória e monetização por taxa de transação. PR #724 permanece aberto. Por isso, o Reel não contém link para `/for-producers`; o CTA é por Direct até a correção e QA mobile.

Metricool brand 7119630 retorna apenas `gbpData`; não há Instagram publicador confirmado. A consulta de posts agendados 02/11–09/11 retornou vazia. O material está pronto para aprovação e publicação manual, sem agendamento automático.

## Ações solicitadas à conta principal
1. Aprovar o roteiro e liberar publicação manual ou conectar Instagram ao Metricool.
2. Revisar/integrar PR #724 após CI e QA mobile; validar cadastro e oferta antes de inserir link público.
3. Registrar alcance, DMs, leads qualificados, produção criada e primeiro evento publicado.

## Evidências
- Entregável: ../deliverables/AUX-03/20261102-W3-reel-primeiro-evento-direct-cta.md
- Worklog: ../worklogs/20261102-1011-AUX-03-W3-producer-first-event-reel.md
- PR comercial: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/724
- Configuração API: https://github.com/petertecnetdev/api.petertecnet.com.br/blob/main/config/subscriptions.php

**Nenhuma mensagem foi enviada. Nenhum post foi agendado/publicado. Sem alteração de produto, merge, deploy ou acesso à VPS.**
