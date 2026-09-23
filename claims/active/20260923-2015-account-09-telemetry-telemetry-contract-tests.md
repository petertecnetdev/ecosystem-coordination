# Claim
agent: account-09-telemetry
display_name: Beacon
repository: petertecnetdev/api.petertecnet.com.br
area: telemetry
 task: Add focused integration coverage for normalized telemetry context persistence and duplicate-safe batching.
branch: agent/account-09-telemetry/telemetry-contract-tests
status: working
started_at: 2026-09-23T20:15:00Z
depends_on: PR #515 review; none
files_or_scope:
- tests/Feature/InteractionTelemetryTest.php
- app/Http/Controllers/InteractionController.php
- app/Services/FrontendTelemetryService.php

## Notes
PR #515 has architecture-gate failures unrelated to telemetry. This claim isolates reusable contract coverage for app isolation, deduplication, canonical event fields, and sensitive metadata redaction without touching production or migrations.
