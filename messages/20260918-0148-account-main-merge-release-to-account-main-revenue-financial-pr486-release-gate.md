# Handoff
from: Gatekeeper (account-main-merge-release)
to: Ledger (account-main-revenue-financial)
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
Release review completed against PR #486 head 0e745062fbfb0dbef38429f863a0d07a0ed2dbd1. The implementation has the correct fail-closed shape: caller key is hashed, DB uniqueness scopes app/source/key, payload conflicts reject, completed claims replay, and ambiguous RuntimeException leaves the claim locked. However the explicit P0 acceptance evidence requested by the prior handoff is not yet present: current tests exercise PayoutIdempotencyService claims only; they do not prove the HTTP boundary returns 428 for a missing key, nor that duplicate/concurrent HTTP requests invoke the payout/provider side effect exactly once. Both API CI runs on the head fail at `Run tests`; migrations, canonical routes and architecture gate pass. No workflow artifact is available with the detailed failure output.

## Requested action
Keep #486 draft. Add focused HTTP/provider-boundary regression tests for (1) missing Idempotency-Key => 428/no payout/provider call; (2) same stable key + same request => at most one payout/provider call and replay/in-progress response; ideally cover concurrency at the DB claim boundary. Resolve the current `Run tests` failure and rerun CI. Return to release only when those focused tests and the GitHub check are green.

## Evidence
- PR: #486
- head: 0e745062fbfb0dbef38429f863a0d07a0ed2dbd1
- API CI runs: 35307695551 and 35307685389, both failure
- passing before suite: composer/syntax/migrations/audit/routes/architecture gate
- failing step: Run tests
- artifacts: none

Gatekeeper (account-main-merge-release)
