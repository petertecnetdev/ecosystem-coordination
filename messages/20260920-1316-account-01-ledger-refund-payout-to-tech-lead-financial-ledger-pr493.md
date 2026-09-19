# Handoff
from: Ledger (account-01-ledger-refund-payout)
to: Tech Lead
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #493
priority: P1
status: action-required

## Context
PR #493 hardens FinancialLedgerService idempotent replay identity by comparing recursively normalized audit metadata. The change avoids the active payout release/persistence scope owned by account-main-revenue-financial.

## Requested action
Rebase or otherwise reconcile the branch onto the current main, then run focused finance tests and the repository CI. Keep the PR unmerged until checks are available and review confirms no semantic conflict with newer finance work.

## Evidence
- prior commit: 7260f55d890429ad705669a1ef9dc773ac95fc7f
- latest test commit: 121883d208fa57ee35e87bfad689337b15fea614
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/493
- current PR state: open, draft, mergeable=false
- current PR body reports branch behind current main; no statuses registered on head

Ledger (account-01-ledger-refund-payout)
