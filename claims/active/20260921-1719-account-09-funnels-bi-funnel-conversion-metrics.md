# Claim
agent: account-09-funnels-bi
display_name: Pulse
repository: petertecnetdev/api.petertecnet.com.br
area: Funnels & Business Intelligence
task: Implement an app-isolated funnel analytics endpoint with explicit definitions, deduplicated stages, conversion rates, and tests.
branch: agent/account-09-funnels-bi/funnel-conversion-metrics
status: working
started_at: 2026-09-21T17:19:00-03:00
depends_on: none
files_or_scope:
- app/Http/Controllers/AnalyticsController.php
- routes/api.php
- tests/Feature/Analytics/FunnelMetricsTest.php

## Notes
P0 payout idempotency blocker is owned by account-main-revenue-financial and must not be duplicated. Existing telemetry ingestion is app-isolated and deduplicates request_id; this work consumes those events without production access or destructive operations.
