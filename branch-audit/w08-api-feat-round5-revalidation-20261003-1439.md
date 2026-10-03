# W08 API branch hygiene — feat round 5 revalidation

Date: 2026-10-03 14:39 America/Sao_Paulo  
Worker: Navigation Weaver (cutinapp-visual-w08)  
Repository: petertecnetdev/api.petertecnet.com.br  
API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`  
Scope: 40 historical `feat/*` refs originally audited as positions 150–189. W07 prefixes and FIN-P0-001 excluded.

## Admin Center status

- Exactly three branches remain.
- `main`: **KEEP / PROTECTION_GAP**.
- PR #2: **MERGED / DELETE_READY_SOURCE**.
- PR #1: **KEEP / BLOCKED** by open API #534 and failed API CI run 36343439430.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 37
- HIGH_RISK_SECOND_REVIEWS: 32
- UNIQUE_USEFUL_THIS_RUN: 3
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0

## MAIN_ANCESTOR — DELETE_READY (7)

- `feat/payflow-domain-v2` (+0/-1870; PR #16 merged)
- `feat/plat-production-ready-staging` (+0/-1572)
- `feat/profit-checkout-recovery-20260905` (+0/-1160)
- `feat/rasoio-reassign-atendimento` (+0/-1951)
- `feat/resource-visibility-platform` (+0/-1459)
- `feat/resource-visibility-platform-temp` (+0/-1479)
- `feat/revenue-funnel-metrics` (+0/-1199; PR #157 merged)

## PR_MERGED_MAIN — DELETE_READY (21)

- `feat/payflow-mvp-complete` — PR #17
- `feat/payment-recovery-state` — PR #218
- `feat/plat-plan-entitlements-main` — PR #339
- `feat/production-discovery-cards-20260905` — PR #177
- `feat/production-public-experience-195` — PR #367
- `feat/profitability-action-queue-20260907` — PR #237
- `feat/profitability-loss-guardrail` — PR #226
- `feat/profitability-net-payment-margin` — PR #220
- `feat/profitability-revenue-attribution` — PR #211
- `feat/public-auth-config` — PR #100
- `feat/public-resource-availability` — PR #76
- `feat/rasoio-dashboard-tempo-real` — PR #14
- `feat/recovery-channel-observed-economics-v2` — PR #281
- `feat/recovery-channel-profitability-20260908` — PR #274
- `feat/recovery-channel-specific-cost-ceiling` — PR #288
- `feat/recovery-click-attribution` — PR #299
- `feat/recovery-confidence-guardrail` — PR #271
- `feat/recovery-cost-ceiling` — PR #273
- `feat/recovery-require-cost-ceiling` — PR #286
- `feat/recovery-segment-safe-ceilings` — PR #291
- `feat/rent-pix-payments` — PR #117

## SUPERSEDED / DUPLICATE / CLOSED OBSOLETE — DELETE_READY (9)

- `feat/peter-platform-v1-architecture`: PR #40 closed; 151 ahead/1571 behind and 127 files.
- `feat/plat-plan-entitlements`: older config-only branch superseded by merged #339.
- `feat/plat-production-ready`: PR #36 closed; staging successor #37 integrated and head is now ancestral.
- `feat/production-owner-transfer-20260904`: SAME_HEAD as canonical retained PR #143 branch.
- `feat/profitability-risk-priority`: superseded by merged recovery confidence/cost guardrail family.
- `feat/recovery-channel-observed-economics`: superseded by v2 PR #281.
- `feat/profitability-break-even-revenue-gap`: PR #236 now closed without merge after finance review; obsolete/equivalent.
- `feat/public-catalog-hardening-20260903`: PR #89 now closed without merge; 25 commits/21 files and 1457 behind current catalog.
- `feat/recovery-surface-revenue-economics`: PR #333 now closed without merge after recovery-economics consolidation.

## UNIQUE_USEFUL — preserve (3)

| Branch | Evidence | Decision |
|---|---|---|
| feat/platform-readiness-health-20260904 | PR #137 open/non-mergeable; +12/-1260; CI 33921979174 failed | KEEP_SELECTIVE |
| feat/production-owner-transfer-ready-20260904 | PR #143 open/non-mergeable; +4/-1253; CI 33925436985 failed; canonical identical head | KEEP_CANONICAL |
| feat/public-developer-platform | PR #97 open/non-mergeable; +53/-1430; CI 33809276153 failed; auth/webhook/migrations | KEEP_HIGH_RISK |

## High-risk second review

Thirty-two refs touching payments, PayFlow, entitlements, auth, webhooks, migrations, profitability, checkout recovery, PIX or deployment/readiness were reviewed twice.

- No financial, auth, webhook, payment or migration code was merged.
- Active payout/payment claims remain authoritative.
- The duplicate owner-transfer branch is delete-ready only because comparison with the retained canonical branch is `identical` at SHA `4d89a16aba631149c31eecc285217fc70838b3fd`.
- Closed PRs #236, #89 and #333 moved from preserve to delete-ready only after their later owner review disposition.
- No ref was deleted because delete-ref remains unavailable.

## Next actions

1. Rebase and obtain green current-main CI for the three preserved branches before any integration.
2. Recheck all 37 heads immediately before executing this delete allowlist.
