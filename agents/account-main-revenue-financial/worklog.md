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
- Added payout idempotency lifecycle regression coverage in commit `dd20382037dbd8201cd7edf24d9a826f7eb146a6`: completed intents must replay the original payout id, validation-only release permits a safe retry, and release cannot delete a completed intent. This strengthens the invariant that post-side-effect intents stay locked while pre-side-effect validation failures remain retryable.
- CI run `35335467175` on `dd203820...` completed failure; structural/migration gates remain healthy but payout route tests still need the new header contract and baseline failures remain to be classified.
- Found an additional retry/replay integrity issue: provider configuration/liquidity preflight ran before the idempotency claim, so a completed replay could incorrectly return 503 when current provider liquidity/config changed and every retry unnecessarily touched provider preflight. Fixed in commit `931d028eb1691557cac758f382267c826b6f8470`: claim/conflict/in-progress/replay now resolve before provider preflight; side-effect-free preflight failures release a newly claimed intent for safe retry; ambiguous transfer outcomes remain locked.
- Latest CI run `35363858132` on head `931d028eb1691557cac758f382267c826b6f8470` completed failure. Composer, syntax, Laravel caches, clean migrations, migration audit, canonical routes and architecture gate all passed; `Run tests` failed and final enforcement failed consequently. GitHub published no workflow artifacts, so the exact current test failure set cannot be safely inferred beyond previously established diagnostics.
- GitHub currently reports PR #486 open/draft and not mergeable; release gate remains closed and no merge was attempted.
- PR #486 remains draft. Do not merge until HTTP/provider-boundary regression coverage is added, the positive payout routes supply stable keys, and CI is rerun/classified.
- #485 remains superseded conceptually and must not be merged as-is.

Economic impact: protects receiver funds and Peter Tecnet settlement integrity against duplicate Pix and cross-application replay ambiguity. Replay is now independent of transient provider liquidity/configuration, avoiding false payout failures after an intent is already complete, while pre-transfer failures do not strand funds behind a stale idempotency claim. This deliberately prioritizes prevention of silent financial loss over payout availability.

Next: update positive payout route tests with stable keys; add missing-key/no-side-effect and duplicate-request/one-provider-call coverage; rerun CI; hand off green payout evidence to release.
