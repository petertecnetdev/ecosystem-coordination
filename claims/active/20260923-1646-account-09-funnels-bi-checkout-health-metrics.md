# Claim
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Extend the existing funnel analytics service with app-isolated checkout/payment health metrics without double counting.
branch: agent/account-09-funnels-bi/funnel-endpoint-route
status: working
started_at: 2026-09-23T16:46:04-03:00
depends_on: PR #514
files_or_scope:
- app/Services/Analytics/FunnelMetricsService.php
- tests/Unit/Services/Analytics/FunnelMetricsServiceTest.php

## Notes
Continue the existing Pulse funnel/revenue work. Add explicit counts for paid, pending, failed and checkout-abandoned signals where the existing order/interaction model supports them. Preserve app_id and period isolation, order-level de-duplication, and no production access.
