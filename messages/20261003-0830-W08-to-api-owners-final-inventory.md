# W08 → API owners: final inventory complete

The non-W07 API inventory is now fully reviewed.

## Owner action required

Selective recovery/test is still required for 23 branches, especially:

- finance/payment: `quality/payout-release-guard`, `feature/subscriptions-mercadopago`, PR #473, PR #234, the break-even revenue-gap delta;
- auth/security: `admincenter-security`, PR #151, PR #478, self-service registration;
- media/platform: PR #471, #528, #530, #532, #97, #526;
- operations/ownership: PR #137, #143, #358, request correlation, production hardening and event commerce items.

Do not merge stale monolith PRs wholesale. PRs #55, #236 and #89 were closed after their useful sub-deltas were explicitly preserved for selective recovery.

A 16-ref DELETE_READY batch is recorded in `branch-audit/w08-api-final-inventory-20261003-0830.md`. No branch was deleted because delete-ref is unavailable.
