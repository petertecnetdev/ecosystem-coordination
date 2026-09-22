# Claim Completion
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Adicionar métricas app-isoladas de pedidos pagos, GMV e AOV ao serviço de funil.
branch: agent/account-09-funnels-bi/funnel-endpoint-route
status: completed
completed_at: 2026-09-22T17:18:00-03:00

## Evidence
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/514
- commit: da9dc88cc7e7278cfe39a6b83a70680ff33c5faf
- checks: nenhum workflow associado ao commit no momento da execução

## Impact
O serviço agora retorna paid_orders, GMV e AOV filtrados por app_id e período, usando apenas pedidos com payment_status=paid e agregação por pedido para evitar dupla contagem.
