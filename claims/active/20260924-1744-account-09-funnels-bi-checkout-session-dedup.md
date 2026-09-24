# Claim
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Corrigir a métrica de abandono de checkout para deduplicar por session_key e excluir somente sessões com conclusão correspondente, evitando subtração agregada incorreta.
branch: agent/account-09-funnels-bi/checkout-session-dedup
status: working
started_at: 2026-09-24T17:44:28-03:00
depends_on: PR #514
files_or_scope:
- app/Services/Analytics/FunnelMetricsService.php
- tests/Unit/Services/Analytics/FunnelMetricsServiceTest.php

## Notes
PR #514 calcula abandono como started - completed, o que pode errar quando as sessões se sobrepõem ou quando eventos duplicados aparecem. A correção ficará restrita ao cálculo analítico e aos testes, sem operações de produção.
