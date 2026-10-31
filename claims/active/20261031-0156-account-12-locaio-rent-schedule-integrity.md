# Claim
agent: account-12-locaio
display_name: Locaio Engineer
repository: petertecnetdev/api.petertecnet.com.br
area: leasing/rent schedule integrity
task: Prevent duplicate rent charges for the same application, lease and calendar month across schedule generation and initial-payment onboarding. Enforce monthly uniqueness in the database, serialize writes on the lease row only around database work, preserve existing financial records, fail fast when legacy duplicates exist, normalize the first-rent reference month from its due date, and add regression tests.
branch: correcao/locacao-cronograma-concorrente
status: working
started_at: 2026-10-31T01:56:03-03:00
depends_on: none
files_or_scope:
- app/Domain/Leasing/Services/LeaseRentScheduleService.php
- app/Domain/Leasing/Http/Controllers/LeasingController.php
- app/Domain/Leasing/Http/Controllers/LeasePaymentWorkflowController.php
- app/Domain/Leasing/Http/Middleware/SerializeLeaseChargeWrites.php
- routes/leasing.php
- database/migrations/2026_10_31_045600_enforce_unique_lease_rent_schedule.php
- tests/Feature/Leasing/LeaseRentScheduleIntegrityTest.php

## Notes
The current schedule generator previously performed exists-then-insert without a transaction or row lock. The existing lease_charges schema had lookup indexes only. The initial-payment workflow also stamped the first rent charge with request-time reference_date instead of the due-date month, so the generated monthly uniqueness key could represent the wrong competence. Its route-level lock wrapped the entire request, including email delivery; the revised flow moves the lock into the database-only transaction so external mail is outside retryable transaction work. The migration must not delete or merge historical charges; it stops with a diagnostic if duplicate rent months already exist. Active finance claims for payout idempotency, ledger replay and payment webhooks remain outside this scope.
