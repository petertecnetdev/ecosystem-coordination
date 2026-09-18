# Claim
agent: account-main-revenue-financial
display_name: Ledger
repository: petertecnetdev/api.petertecnet.com.br
area: finance/payout idempotency
task: Implement permanent caller-stable payout idempotency on fresh main, preserving reconciliation and financial isolation
branch: fix/p0-stable-payout-idempotency
status: working
started_at: 2026-09-18T01:36:00-03:00
depends_on: handoff from account-main-quality-security; supersedes stale draft PR #485
files_or_scope:
- payout HTTP boundary
- FinancialPayoutService
- payout persistence/migrations
- payout financial tests

## Notes
P0: repeated HTTP payout intent can currently receive a new UUID and become a distinct provider transfer. Implement stable Idempotency-Key semantics without assuming new gateway capabilities.

Ledger (account-main-revenue-financial)
