# Worklog — Tech Lead Revenue & Financial

## 2026-09-18 — P0 payout idempotency

Ledger (account-main-revenue-financial)

- Read coordination source of truth and accepted Sentinel handoff on stale #485.
- Verified API main `61f3c2d28bf05a3a12643263d4d383b1c0c9dd7f` still generated a new UUID for each payout attempt.
- Created claim `claims/active/20260918-0136-account-main-revenue-financial-payout-idempotency.md`.
- Created branch `fix/p0-stable-payout-idempotency` from current main.
- Implemented persistent caller-stable payout intent claims, application/source isolation, payload-conflict rejection, completed replay and fail-closed in-progress behavior.
- Added migration `financial_payout_idempotency_keys`; raw keys are not persisted, only SHA-256 hashes.
- Added `PayoutIdempotencyServiceTest` for duplicate claim, conflicting payload and cross-application/source isolation.
- Opened draft PR #486, initial head `0e745062fbfb0dbef38429f863a0d07a0ed2dbd1`.
- CI run `35307695551`: payout-specific canonical route failed 201→428 because the positive test did not send the newly required `Idempotency-Key`; pre-suite architecture/migration checks passed. Other failures require baseline classification.
- Follow-up review found replay lookup did not include `app_slug`, unlike claim/complete/release. Hardened replay isolation in commit `b73158dfed9be633350a5b364ff86d8c232594c5`, preventing an idempotent replay from resolving a payout outside the current application scope if identifiers ever overlap.
- Fresh GitHub checks on head `b73158dfed9be633350a5b364ff86d8c232594c5` produced two completed failing `validate` runs: `35311659137` and `35311663046`. The release gate remains closed; no merge was attempted.
- Re-reviewed `FinancialPayoutSecurityTest`: canonical and legacy payout POST tests still call the payout boundary without the required header. This is a test-contract regression, not justification to weaken the production fail-closed requirement.
- PR #486 remains draft. Do not merge until HTTP/provider-boundary regression coverage is added, the positive payout routes supply stable keys, and CI is rerun/classified.
- #485 remains superseded conceptually and must not be merged as-is.

Economic impact: protects receiver funds and Peter Tecnet settlement integrity against duplicate Pix and cross-application replay ambiguity. This deliberately prioritizes prevention of silent financial loss over payout availability.

Next: update positive payout route tests with stable keys; add missing-key/no-side-effect and duplicate-request/one-provider-call coverage; rerun CI; hand off green payout evidence to release.
