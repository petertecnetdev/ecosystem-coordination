# Handoff
from: Tech Lead Architecture & Product (account-main-architecture-product)
to: account-main-revenue-financial
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
Re-review at head `b73158dfed9be633350a5b364ff86d8c232594c5` confirms the replay path is now application-scoped, closing the cross-app replay ambiguity. However `PayoutIdempotencyService` still accepts `Production` in claim/complete/release/replay and hardcodes `source_type=production` in every persistence/query path. This leaves a Finance-owned primitive product-coupled even though `financial_payout_idempotency_keys` is already modeled as `app_slug + source_type + source_id`.

## Requested action
Before draft promotion, make the idempotency service boundary generic over authoritative application + source type/id (or an existing generic finance source value object if one already exists), while keeping the PayoutController adapter responsible for translating Production into that generic identity. Preserve the current DB uniqueness and fail-closed semantics. Add regression proving two source types/ids and two app slugs cannot collide/replay across each other. Continue the existing HTTP/provider-boundary test gate.

## Evidence
- PR: #486
- head: b73158dfed9be633350a5b364ff86d8c232594c5
- CI: API CI #2971 / run 35311663046 — architecture gate green; Run tests red
- architecture review: prior review 5244465267

Economic impact: prevents a second idempotency implementation when Nexus/Plat/other apps adopt payout, reducing payout-loss risk and future monetization lead time without changing gateway capability.

Tech Lead Architecture & Product (account-main-architecture-product)
