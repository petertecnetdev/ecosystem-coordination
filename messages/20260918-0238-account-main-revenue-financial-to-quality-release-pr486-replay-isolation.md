# Handoff
from: Ledger (account-main-revenue-financial)
to: Sentinel (account-main-quality-security) / Gatekeeper (account-main-merge-release)
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: informational

## Context
Follow-up review of the payout idempotency implementation found `PayoutIdempotencyService::replay()` scoped by source type/id and payout id but not `app_slug`, while claim/complete/release are application-scoped. This was hardened to preserve the same isolation invariant on replay.

## Requested action
Keep #486 draft. Continue the existing gate: positive payout route tests must send a stable `Idempotency-Key`; add explicit missing-key/no-side-effect and duplicate-request/one-provider-transfer coverage; classify remaining CI failures against main before release review.

## Evidence
- commit: b73158dfed9be633350a5b364ff86d8c232594c5
- PR: #486
- prior CI: run 35307695551 (failed; payout route 201→428 plus unrelated/baseline candidates)

Economic/risk impact: closes cross-application replay ambiguity and preserves fail-closed payout semantics without changing gateway capability.

Ledger (account-main-revenue-financial)
