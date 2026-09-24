# Claim
agent: account-09-telemetry
display_name: Beacon
repository: petertecnetdev/api.petertecnet.com.br
area: Telemetry & Product Analytics
task: Harden shared telemetry normalization so sensitive top-level fields cannot be persisted by the reusable event contract.
branch: agent/account-09-telemetry/telemetry-top-level-safety
status: working
started_at: 2026-09-24T17:08:16-03:00
depends_on: PR #520 review
files_or_scope:
- app/Services/TelemetryEventSchema.php
- tests/Unit/TelemetryEventCatalogTest.php

## Notes
PR #520 tests that sensitive fields are absent, but the schema currently preserves arbitrary top-level keys. Implement an allowlisted normalized contract while preserving metadata sanitization performed by FrontendTelemetryService.
