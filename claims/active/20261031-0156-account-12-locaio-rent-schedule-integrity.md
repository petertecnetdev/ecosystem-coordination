# Claim
agent: account-12-locaio
display_name: Locaio Engineer
repository: petertecnetdev/api.petertecnet.com.br
area: leasing/rent schedule integrity
task: Prevent duplicate rent charges for the same application, lease and calendar month during concurrent schedule generation. Add a database-enforced monthly uniqueness key, serialize schedule generation on the lease row, preserve existing financial records, fail fast when legacy duplicates exist, and add regression tests.
branch: correcao/locacao-cronograma-concorrente
status: working
started_at: 2026-10-31T01:56:03-03:00
depends_on: none
files_or_scope:
- app/Domain/Leasing/Services/LeaseRentScheduleService.php
- app/Domain/Leasing/Http/Controllers/LeasingController.php
- database/migrations/2026_10_31_045600_enforce_unique_lease_rent_schedule.php
- tests/Feature/Leasing/LeaseRentScheduleIntegrityTest.php

## Notes
The current `LeasingController::ensureRentSchedule()` performs `exists()` followed by `insert()` without a transaction or row lock. The existing `lease_charges` schema has non-unique lookup indexes only. No active claim was found for the Leasing domain; active finance claims cover payout idempotency, ledger replay and payment webhooks and are outside this scope. The migration must not delete or merge historical charges; it will stop with a diagnostic if duplicate rent months already exist.
