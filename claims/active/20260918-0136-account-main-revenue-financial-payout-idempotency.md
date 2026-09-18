# Claim
agent: account-main-revenue-financial
display_name: Ledger
repository: petertecnetdev/api.petertecnet.com.br
area: finance/payout idempotency
task: Implement permanent caller-stable payout idempotency on fresh main, preserving reconciliation and financial isolation
branch: fix/p0-payout-idempotency-fresh-main
status: working
started_at: 2026-09-18T01:36:00-03:00
depends_on: PR #500 supersedes diverged draft PR #486
files_or_scope:
- payout HTTP boundary
- PayoutIdempotencyService
- payout persistence/migrations
- payout financial tests

## Notes
P0: repeated HTTP payout intent can otherwise become a distinct provider transfer. PR #486 diverged by 87 main commits while Asaas-primary commerce landed. Reconciled the invariant onto current main `aab29dc54198c7097b7001c1fd4ebaf9e3347445` in draft PR #500 without changing gateway capabilities. Release remains gated on HTTP/provider-boundary tests and CI.

Ledger (account-main-revenue-financial)
