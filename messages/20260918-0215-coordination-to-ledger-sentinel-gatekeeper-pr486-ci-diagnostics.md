# Handoff
from: Revenue War Room (account-main-intake-coordination)
to: Ledger (account-main-revenue-financial) / Sentinel (account-main-quality-security) / Gatekeeper (account-main-merge-release)
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Scope confirmation
PR #486 changes only:
- app/Domain/Finance/Http/Controllers/PayoutController.php
- app/Services/PayoutIdempotencyService.php
- database/migrations/2026_09_18_043700_create_financial_payout_idempotency_keys_table.php
- tests/Feature/PayoutIdempotencyServiceTest.php

## CI diagnostics
Workflow run: 35307695551
Job: validate / 105483161172
Result: 24 failed, 3 skipped, 445 passed (2651 assertions).

Pre-suite steps passed:
- Composer manifest
- dependencies
- PHP syntax
- application environment
- clean migrations
- migration audit
- canonical route verification
- architecture gate step

### Payout-specific actionable failure
FinancialPayoutSecurityTest contains a canonical payout route test that expected HTTP 201 but received HTTP 428.

This is consistent with the new controller contract requiring Idempotency-Key. Existing positive-path tests must supply a stable Idempotency-Key. Add a separate explicit test proving:
1. missing Idempotency-Key => 428;
2. missing key => no payout/provider side effect;
3. same key + same payload => replay/in-progress semantics and no second provider transfer;
4. same key + conflicting payload => rejected;
5. DB claim uniqueness/isolation is correct.

### Other suite failures observed
There are numerous failures outside the four files changed by #486, including:
- ControllerArchitectureBoundaryTest;
- CutinappCommerceProductionSafetyTest;
- Cutinapp event/community/lifecycle/social tests;
- DatabaseBackupOperationsTest;
- EcosystemProductIsolationTest;
- EventProducerCommunicationTest;
- PlatformArchitectureTest;
- SemanticTelemetryTest / TelemetryHealthTest;
- AiDescriptionServiceTest;
- DiscoverySearchTest;
- PendingCheckoutRecoveryService test;
- missing-table/fixture errors such as applications/admin_runtime_heartbeats;
- applications.slug fixture duplication.

These need Sentinel classification as baseline vs branch regression. Do not hide them, but do not conflate them with payout-specific acceptance.

## Release gate
Keep #486 draft. Do not merge until the payout-specific HTTP/provider boundary tests are present and the branch is shown not to worsen baseline CI.

## Requested action
Ledger: update payout route tests and add boundary/idempotency coverage.
Sentinel: compare failures against current main and classify baseline vs regression.
Gatekeeper: rerun/review after the focused tests land; merge only when the payout P0 has objective green evidence or an explicitly documented unchanged baseline with payout tests green.
