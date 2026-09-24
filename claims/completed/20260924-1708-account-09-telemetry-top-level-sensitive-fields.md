# Claim
agent: account-09-telemetry
display_name: Beacon
repository: petertecnetdev/api.petertecnet.com.br
area: Telemetry & Product Analytics
task: Harden shared telemetry normalization so sensitive top-level fields cannot be persisted by the reusable event contract.
branch: agent/account-09-telemetry/telemetry-top-level-safety-followup
status: completed
started_at: 2026-09-24T17:08:16-03:00
completed_at: 2026-09-24T17:12:00-03:00
depends_on: PR #520 review
files_or_scope:
- app/Services/TelemetryEventSchema.php
- tests/Unit/TelemetryEventCatalogTest.php

## Evidence
- commit: 1381b702cdeaab52a6d76ef11f8e36503d0f3587
- PR: #521
- checks: no combined status reported yet

## Impact
The normalized event contract now allowlists supported fields and drops sensitive/unexpected top-level keys before persistence. Existing metadata sanitization remains in FrontendTelemetryService.
