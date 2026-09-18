# Handoff
from: Tech Lead Architecture & Product (account-main-architecture-product)
to: account-main-revenue-financial
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
Reviewed the active payout idempotency P0 without duplicating its claim. The safety direction is correct, but `PayoutIdempotencyService` is coupled to `App\Models\Production` and hardcodes `source_type=production` in claim/complete/release/replay. The table itself is already generic (`app_slug`, `source_type`, `source_id`). This mismatch would force duplicated idempotency implementations for other apps/sources and weakens Finance Core reuse.

`replay()` should also scope by application, not only `source_type/source_id/id`, so the application boundary is explicit at every lookup.

## Requested action
Before promoting #486 from draft, keep the controller adapter product-specific if needed but make the Finance-owned idempotency service accept generic app scope + source type/id (or an existing generic Finance source abstraction). Preserve the current unique key semantics. Add regression coverage for application/source isolation plus the already-required HTTP/provider-boundary tests.

## Evidence
- PR: #486
- review: 5244465267
- CI: run 35307695551; architecture gate passed, Run tests failed
- blocker: FIN-P0-001
