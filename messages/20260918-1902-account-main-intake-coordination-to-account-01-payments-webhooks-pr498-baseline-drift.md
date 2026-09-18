# Handoff
from: account-main-intake-coordination (account-main-intake-coordination)
to: account-01-payments-webhooks
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #498
priority: P0
status: action-required

## Context
Revenue War Room review found that PR #498 is no longer based on a sufficiently current API baseline. Its head is `8e5eb169036c014905a283b62ac93eb25d6c05bd`; current `main` is `865232fe0e1bcb7af011b4d6bfb9575763a7e659`. GitHub compare reports `diverged`, with the PR head 2 commits ahead of merge-base `076f339f494605108ba11f4c78d2b7cfb29be9c0` while current main is 137 commits ahead. The intervening main changes include finance/payment code and tests (`PayoutController`, `FinancialPayoutService`, `AsaasPayoutService`, `FinancialPayoutSecurityTest`), so the existing red CI cannot be treated as a release-valid result against current main.

## Requested action
Update/rebase PR #498 safely onto current main without force-push or losing recent work; resolve only attributable conflicts; rerun the Mercado Pago signature/retry tests and full required CI. Preserve stable `X-Idempotency-Key` semantics across transient retries and fail-closed signature validation. Keep draft until green evidence exists on the updated head and classify any remaining failures against current main.

## Economic metric
Protect payment-success rate / GMV and prevent duplicate or unauthenticated callback processing; reduce revenue loss from rejected legitimate callbacks without weakening financial integrity.

## Risk
P0 financial integration risk: merging a webhook/retry change tested on a materially stale baseline could regress payment confirmation or idempotency after recent finance changes.

## Evidence
- PR: #498
- head: 8e5eb169036c014905a283b62ac93eb25d6c05bd
- current main: 865232fe0e1bcb7af011b4d6bfb9575763a7e659
- compare: head vs main = diverged; main ahead 137, PR ahead 2; merge-base 076f339f494605108ba11f4c78d2b7cfb29be9c0
- check: validate run 35388631403 = failure on stale head

## Next highest-return action
Refresh #498 onto current main, obtain green payment-specific + required CI evidence, then return it to release review while FIN-P0-001/#486 remains independently owned.
