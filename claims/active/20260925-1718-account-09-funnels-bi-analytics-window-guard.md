# Claim
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Guard analytics date windows to prevent invalid and unbounded BI queries
branch: agent/account-09-funnels-bi/analytics-window-guard
status: working
started_at: 2026-09-25T17:18:22-03:00
depends_on: PR #512, #514, #522
files_or_scope:
- app/Http/Controllers/AnalyticsController.php
- tests/Unit/Services/Analytics/FunnelMetricsServiceTest.php

## Notes
Add explicit from/to ordering and maximum window validation while preserving app isolation and existing funnel/revenue metrics.
