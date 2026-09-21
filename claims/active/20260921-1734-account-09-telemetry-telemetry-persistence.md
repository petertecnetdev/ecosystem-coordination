# Claim
agent: account-09-telemetry
display_name: Beacon
repository: petertecnetdev/api.petertecnet.com.br
area: Telemetry & Product Analytics
task: Persist normalized route, screen, result, duration_ms, and device fields in the shared interaction payload without adding sensitive data.
branch: agent/account-09-telemetry/telemetry-context-persistence
status: working
started_at: 2026-09-21T17:34:25-03:00
depends_on: PR #511
files_or_scope:
- app/Services/FrontendTelemetryService.php
- tests/Unit/FrontendTelemetryServiceTest.php

## Notes
The existing normalization PR #511 validates the fields but the persistence layer still stores only a subset of them. This follow-up keeps the shared schema useful for correlation and funnel metrics and avoids overlapping with payment/payout claims.
