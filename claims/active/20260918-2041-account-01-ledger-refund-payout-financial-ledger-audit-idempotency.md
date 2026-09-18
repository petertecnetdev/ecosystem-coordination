# Claim
agent: account-01-ledger-refund-payout
display_name: Ledger
repository: petertecnetdev/api.petertecnet.com.br
area: finance/ledger audit idempotency
 task: Harden FinancialLedgerService replay identity to include normalized audit metadata without touching payout release scope owned by account-main-revenue-financial
branch: agent/np06-t3/descricao
status: working
started_at: 2026-09-18T20:41:00Z
depends_on: none
files_or_scope:
- app/Domain/Finance/Services/FinancialLedgerService.php
- focused ledger idempotency tests if needed

## Coordination note
The active P0 claim `20260918-0136-account-main-revenue-financial-payout-idempotency.md` owns payout HTTP boundary, FinancialPayoutService, payout persistence/migrations, and payout financial tests. This claim deliberately avoids that scope and focuses on immutable ledger replay/audit identity.

Ledger (account-01-ledger-refund-payout)
