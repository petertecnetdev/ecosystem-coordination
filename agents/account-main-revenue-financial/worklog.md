# Worklog — Tech Lead Revenue & Financial

## 2026-09-18 — P0 payout idempotency

Ledger (account-main-revenue-financial)

- Implemented caller-stable payout idempotency originally in draft PR #486 with SHA-256 key storage, app/source isolation, conflict rejection, completed replay and fail-closed ambiguous outcomes.
- Earlier CI established the positive payout tests need the new Idempotency-Key contract; release remained blocked on HTTP/provider-boundary evidence.
- Current-main review found #486 had diverged materially: 87 commits from its head to `main`, including Asaas-primary commerce/payment/settlement changes. Per CMD-003/CMD-004, did not merge the stale branch over the new financial pipeline.
- Re-read current main at `aab29dc54198c7097b7001c1fd4ebaf9e3347445` (`feat(payments): make Asaas primary for commerce`) and preserved that gateway direction; no unsupported provider capability or fallback was introduced.
- Created fresh branch `fix/p0-payout-idempotency-fresh-main` from current main and ported the P0 invariant there.
- Commits: `d070f62d67eccabb3991a02fdb379b98e148c0af` controller boundary; `af4bfd97fcb3f0acb3418f72be0dab004abebd23` idempotency service; `f48561185964462e1a53a059972389e4b7b74f61` persistence; `9c39aa0c28284a77970d8c68775ef7b5c2b8cb38` lifecycle/isolation tests.
- Opened draft PR #500 `fix(finance): reconcile payout idempotency onto current main`, based directly on `aab29dc...`; #500 supersedes #486 after validation.
- PR #500 remains draft/not mergeable at creation time. No merge attempted. HTTP/provider-boundary acceptance and CI remain required.

Economic impact: prevents duplicate Pix payout intent/retry from becoming a second transfer while preserving the newly established Asaas-primary commerce path. Protects receiver funds, settlement integrity and Peter Tecnet margin from silent payout duplication; completed replay avoids false dependence on transient provider preflight state.

Next: add/validate HTTP boundary evidence (`missing key => 428 + zero side effect`, same key/payload => at most one payout/provider call, conflicting payload => 409), update positive payout tests with stable keys, run CI on #500, classify any baseline failures, then hand off to release.
