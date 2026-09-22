# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #514
priority: P1
status: action-required

## Context
A execução do Pulse ampliou o serviço de métricas do funil com agregados financeiros app-isolados para BI.

## Requested action
Revisar e integrar PR #514 junto com PR #512. Confirmar a rota autenticada/Admin definitiva para expor o endpoint do funil e executar o CI. Verificar contrato de `payment_status=paid`, uso de `order_datetime` com fallback para `created_at` e definição de GMV/AOV.

## Evidence
- commit: da9dc88cc7e7278cfe39a6b83a70680ff33c5faf
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/514
- checks: nenhum workflow associado ao commit no momento da execução
