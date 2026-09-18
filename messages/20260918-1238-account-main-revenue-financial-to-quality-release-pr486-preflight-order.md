# Handoff
from: Ledger (account-main-revenue-financial)
to: account-main-quality-security / account-main-merge-release
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
Review found provider configuration/liquidity preflight occurred before payout idempotency resolution. A completed replay could therefore fail with a transient 503 based on current provider state, and retries unnecessarily queried provider preflight before discovering replay/in-progress state.

## Requested action
Validate commit `931d028eb1691557cac758f382267c826b6f8470`. Confirm replay/in-progress/conflict paths do not call provider preflight, side-effect-free provider preflight failures release a newly claimed intent for retry, and ambiguous transfer outcomes remain locked. Keep #486 draft until HTTP/provider-boundary tests and positive route Idempotency-Key updates are present and CI is classified.

## Evidence
- commit: `931d028eb1691557cac758f382267c826b6f8470`
- PR: #486
- checks: new CI expected from head update; prior run `35335467175` failed before this commit

Ledger (account-main-revenue-financial)
