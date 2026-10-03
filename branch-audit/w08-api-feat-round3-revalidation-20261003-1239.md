# W08 API branch hygiene — feat round 3 revalidation

Date: 2026-10-03 12:39 America/Sao_Paulo  
Worker: Navigation Weaver (cutinapp-visual-w08)  
Repository: petertecnetdev/api.petertecnet.com.br  
API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`  
Scope: the same 40 `feat/*` refs originally audited as positions 70–109. `agent/*`, `w07/*` and FIN-P0-001 are excluded.

## Admin Center status

- Inventory is still exactly `main`, `feat/media-library-admin`, `feat/cutinapp-admin-email-composer`.
- `main`: **KEEP / PROTECTION_GAP**. The previously observed `protected=false` gap remains the required owner action.
- PR #2: **MERGED / DELETE_READY_SOURCE**.
- PR #1: **KEEP / BLOCKED**. It is open and mergeable, but API PR #534 remains open; API CI run 36343439430 failed.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 28
- HIGH_RISK_SECOND_REVIEWS: 31
- UNIQUE_USEFUL_THIS_RUN: 12
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0

## Decision matrix

| Branch | Fresh comparison | Decision | Evidence |
|---|---:|---|---|
| feat/discovery-learning-loop-20260903 | +16 / -1438 | DELETE_READY / SUPERSEDED_FAMILY | v2 PR #98 merged |
| feat/discovery-learning-loop-v2-20260903 | +5 / -1430 | DELETE_READY / PR_MERGED | PR #98 merged |
| feat/document-signature-production | +1 / -1388 | DELETE_READY / PR_MERGED | PR #112 merged |
| feat/document-signature-workflow | +15 / -1407 | DELETE_READY / SUPERSEDED_FAMILY | production successor #112 merged |
| feat/duplicate-event-edit-before-create | +4 / -1073 | UNIQUE_USEFUL / KEEP | PR #203 open, not mergeable, CI failed |
| feat/ecosystem-health-readiness | +5 / -1207 | UNIQUE_USEFUL / KEEP | PR #152 open/mergeable, CI failed |
| feat/ecosystem-support-20260905-v2 | +3 / -1124 | DELETE_READY / SUPERSEDED_FAMILY | incomplete subset; full support PR #196 merged |
| feat/ecosystem-support-20260905 | +0 / -1118 | DELETE_READY / MAIN_ANCESTOR | PR #196 merged |
| feat/email-verification-deferral | +3 / -1256 | DELETE_READY / PR_MERGED | PR #141 merged |
| feat/enforce-entitlement-limits | +3 / -720 | DELETE_READY / PR_MERGED | PR #338 merged |
| feat/event-addons-management-20260906 | +0 / -1042 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-addons-producer-management-20260906 | +1 / -1042 | UNIQUE_USEFUL / KEEP_SELECTIVE | exclusive EventManagementController delta |
| feat/event-ai-image-fallback-20260919 | +6 / -132 | UNIQUE_USEFUL / KEEP | PR #503 open/mergeable; no workflow run returned |
| feat/event-catalog-addons | +0 / -911 | DELETE_READY / MAIN_ANCESTOR | PR #241 merged |
| feat/event-date-item-redemption | +0 / -1115 | DELETE_READY / MAIN_ANCESTOR | PR #199 merged |
| feat/event-lifecycle-generic-20260903-2 | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-lifecycle-generic-20260903 | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-lifecycle-implementation | +20 / -1419 | DELETE_READY / SUPERSEDED_HIGH_RISK | historical refund/lifecycle integration; PR #102 closed |
| feat/event-lifecycle-implementation-2 | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-lifecycle-implementation-3 | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-lifecycle-working | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/event-manager-211-20260918 | +1 / -140 | UNIQUE_USEFUL / KEEP_SELECTIVE | exclusive artist-filter controller delta |
| feat/event-media-pipeline | +6 / -782 | UNIQUE_USEFUL / KEEP_SELECTIVE | exclusive image variants pipeline |
| feat/event-no-show-metrics-20260905 | +10 / -1206 | DELETE_READY / PR_MERGED | PR #156 merged |
| feat/event-poster-normalization-fallback | +7 / -2 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #528 open/mergeable; CI run 36274631466 failed |
| feat/event-share-preview-20260907 | +3 / -919 | DELETE_READY / SUPERSEDED_FAMILY | final family branch retained |
| feat/event-share-preview-final-20260907 | +3 / -910 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #246 open/mergeable; CI run 34149545256 failed |
| feat/explicit-checkout-recovery-intent | +3 / -1183 | DELETE_READY / SUPERSEDED_FAMILY | later checkout recovery merged |
| feat/feed-post-media | +8 / -1 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #532 open/mergeable; CI run 36322300163 failed |
| feat/flyer-date-consistency | +11 / -2 | DELETE_READY / PR_MERGED | PR #531 merged |
| feat/forecasting-core | +2 / -172 | UNIQUE_USEFUL / KEEP_HIGH_RISK | PR #491 open/mergeable; CI run 35378125403 failed; migrations/jobs |
| feat/generic-account-settlement | +7 / -1430 | UNIQUE_USEFUL / KEEP_CLAIM_ADJACENT | financial/ledger/migration delta; no integration |
| feat/generic-app-messaging | +26 / -1155 | DELETE_READY / SUPERSEDED_FAMILY | current messaging architecture supersedes historical family |
| feat/generic-establishment-conversion-20260903 | +157 / -1571 | DELETE_READY / SUPERSEDED_HISTORICAL | 113-file obsolete integration |
| feat/generic-event-lifecycle-protection | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-event-lifecycle-protection-final | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-event-lifecycle-protection-impl | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-event-lifecycle-protection-v2 | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-fulfillment-lifecycle | +158 / -1571 | DELETE_READY / SUPERSEDED_HIGH_RISK | 112-file obsolete commerce/finance integration |
| feat/generic-item-ai-content | +5 / -302 | UNIQUE_USEFUL / KEEP_SELECTIVE | exclusive creative text generator and tests |

## Classification summary

- MAIN_ANCESTOR: 13
- PR_MERGED: 6
- SUPERSEDED_FAMILY / SUPERSEDED_HISTORICAL: 9
- UNIQUE_USEFUL: 12

## High-risk second review

Thirty-one refs touched or implicated auth, signatures, checkout/refunds, finance/entitlements/settlement, fulfillment, migrations, jobs, media, or broad historical integrations.

- Merged signature, entitlement, checkout, flyer and catalog work is retained on main through its merged PRs; historical source refs remain deletion candidates.
- `feat/generic-account-settlement` is preserved because it changes settlement, Mercado Pago, finance routes and a ledger migration. FIN-P0-001 remains excluded.
- `feat/forecasting-core` is preserved because it adds tables, jobs and routes.
- `feat/generic-fulfillment-lifecycle` and `feat/generic-establishment-conversion-20260903` are not safe merge candidates: both are more than 1,500 commits behind and alter broad finance/commerce/auth/migration surfaces.
- No financial, auth, webhook or migration branch was merged.
- No ref was deleted because delete-ref remains unavailable.

## Owner actions

1. Review/rebase the 12 preserved deltas selectively; do not bulk merge.
2. Fix CI before considering PRs #152, #203, #246, #491, #528 or #532.
3. Recheck every head immediately before executing this 28-ref delete allowlist.
