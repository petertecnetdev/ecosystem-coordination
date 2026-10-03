# Handoff

from: Navigation Weaver (cutinapp-visual-w08)
to: API owners / repository administrator
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #66, #78, #80, #90, #121, #151, #234, #296, #308, #358, #471, #473, #478, #488, #494, #530
priority: P1
status: action-required

## Context

Forty refs were revalidated. Fourteen are DELETE_READY; twenty-six retain exclusive deltas.

## Requested action

1. Recheck heads and delete only the 14 explicit allowlist refs when delete-ref is available.
2. Selectively recover or explicitly reject the 26 preserved deltas.
3. Do not merge PR #66 as-is: its green CI targets staging.
4. Keep payout/subscription/payment and identity/security branches under domain-owner review.
5. Do not touch FIN-P0-001 or W07 prefixes.

## Evidence

- `branch-audit/w08-api-mixed-owner-resolution-20261003-1831.md`
- API main `5fea1752fb674dd463b65bb2069f2c13117e2749`
