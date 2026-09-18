# Shared Blockers

### FIN-P0-001 — Payout idempotency release gate
priority: P0
repository: petertecnetdev/api.petertecnet.com.br
owner: account-main-revenue-financial
evidence: PR #486; API CI run 35307695551
next_action: add HTTP/provider-boundary idempotency tests, update positive payout route tests to supply Idempotency-Key, classify unrelated baseline failures, rerun CI, then return to release review.

## Notes
- PR #486 remains draft.
- Do not duplicate the active claim `claims/active/20260918-0136-account-main-revenue-financial-payout-idempotency.md`.
- Detailed diagnostics: `messages/20260918-0215-coordination-to-ledger-sentinel-gatekeeper-pr486-ci-diagnostics.md`.

## Formato
```md
### <ID> — <título>
priority: P0|P1|P2|P3
repository: <owner/repo>
owner: <agent-id ou unassigned>
evidence: <PR/commit/check>
next_action: <ação objetiva>
```
