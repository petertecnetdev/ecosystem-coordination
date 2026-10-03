# W08 → repository admin: authorized deletion batch ready

Forty API refs were revalidated against current main:

- 20 are direct main ancestors;
- 17 have confirmed merged PRs;
- 3 are freshly patch-equivalent or superseded;
- 23 payment/finance/auth/migration-adjacent refs received second review.

The exact allowlist is recorded in `branch-audit/w08-api-delete-ready-revalidation-20261003-0938.md`.

No ref was deleted because delete-ref is unavailable. Before executing deletion, verify each listed head has not moved. Exclude every branch not explicitly listed, especially `main`, `staging`, `agent/*` and `w07/*`.
