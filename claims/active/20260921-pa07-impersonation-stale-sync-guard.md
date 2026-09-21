# PA07 — Impersonation stale-response runtime guard

- **Agent:** PA07
- **Scope:** `petertecnetdev/petertecnet.com.br/public/ecosystem/peter-impersonation.js`
- **Problem:** concurrent `sync()` requests can resolve out of order; an older active response may render stale impersonation UI after logout/end/expiry state was already cleared.
- **Plan:** add generation/request guards so only the latest sync response can mutate runtime state; do not change authorization or token exchange rules.
- **Exclusions:** no gateway, production access, auth weakening, or overlapping claims for NP09 dialog/a11y or prior PA07 AbortController work.
- **Status:** START
- **Started:** 2026-09-21
