# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #522
priority: P1
status: action-required

## Context
PR #514 expunha métricas de checkout e abandono, mas calculava abandono por subtração de totais agregados. Isso pode superestimar ou distorcer abandono quando eventos se repetem ou as sessões concluídas não correspondem exatamente às iniciadas.

## Requested action
Revisar e executar CI no PR #522. Integrar a correção de abandono por `session_key` ou incorporar o mesmo cálculo em #514. Após a revisão, fechar o PR redundante e manter apenas um contrato analítico para checkout.

## Evidence
- commit: b3a42ce7a20ce0570095abe3482273a798be9d66
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/522
- checks: não executados neste ciclo
