# W08 API branch hygiene — feat round 4 revalidation

Date: 2026-10-03 13:38 America/Sao_Paulo  
Worker: Navigation Weaver (cutinapp-visual-w08)  
Repository: petertecnetdev/api.petertecnet.com.br  
API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`  
Scope: 40 historical `feat/*` refs originally audited as positions 110–149. `agent/*`, `w07/*` and FIN-P0-001 are excluded.

## Admin Center status

- Inventory remains exactly `main`, `feat/media-library-admin`, `feat/cutinapp-admin-email-composer`.
- `main`: **KEEP / PROTECTION_GAP**; owner/ruleset remediation remains pending.
- PR #2: **MERGED / DELETE_READY_SOURCE**.
- PR #1: **KEEP / BLOCKED**. It is open and mergeable, but API #534 remains open and API CI run 36343439430 failed.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 29
- HIGH_RISK_SECOND_REVIEWS: 31
- UNIQUE_USEFUL_THIS_RUN: 11
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0

## Evidence correction

The prior audit treated `feat/generic-portfolio-analytics` and `feat/generic-resource-operations` as delete-ready because PRs #107 and #109 were merged. Fresh review shows both PRs were merged into `feat/leasing-lifecycle-intelligence-v2`, not `main`. Main currently lacks:

- `app/Domain/Analytics/Http/Controllers/PortfolioAnalyticsController.php`
- `app/Domain/Operations/Http/Controllers/ResourceOperationsController.php`
- `database/migrations/2026_09_04_020500_create_generic_resource_operations_tables.php`

Both refs are therefore corrected to **UNIQUE_USEFUL / KEEP_SELECTIVE**.

## Decision matrix

| Branch | Fresh comparison | Decision | Evidence |
|---|---:|---|---|
| feat/generic-lease-contract-templates | +3 / -1364 | DELETE_READY / PR_MERGED_MAIN | PR #119 merged to main |
| feat/generic-leasing-domain | +5 / -1437 | DELETE_READY / PR_MERGED_MAIN | PR #95 merged to main |
| feat/generic-onboarding-data-quality-v2-final | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2-impl | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2-mainwork | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2-pr | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2-pr2 | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2-work | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-data-quality-v2 | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-hardening-20260903 | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-hardening-final2-20260903 | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-onboarding-hardening-final-20260903 | +0 / -1523 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/generic-pix-beneficiary-payouts | +31 / -1568 | DELETE_READY / PR_MERGED_MAIN | PR #45 merged; finance second review only |
| feat/generic-portfolio-analytics | +5 / -1407 | UNIQUE_USEFUL / KEEP_SELECTIVE | PR #107 merged only into intermediate branch; controller absent from main |
| feat/generic-resource-operations | +8 / -1407 | UNIQUE_USEFUL / KEEP_SELECTIVE | PR #109 merged only into intermediate branch; controller/migration absent from main |
| feat/generic-service-scheduling | +107 / -1571 | DELETE_READY / SUPERSEDED_HISTORICAL | 90-file obsolete integration |
| feat/generic-subscription-foundation | +3 / -349 | DELETE_READY / PR_MERGED_MAIN | PR #461 merged |
| feat/generic-subscription-intents | +11 / -727 | DELETE_READY / PR_MERGED_MAIN | PR #332 merged |
| feat/google-place-picker | +7 / -1240 | DELETE_READY / SUPERSEDED_FAMILY | PR #147 closed; v2 retained |
| feat/identity-platform-20260903 | +0 / -1488 | DELETE_READY / MAIN_ANCESTOR | PR #77 merged |
| feat/issue-645-flyer-description-api | +6 / -9 | DELETE_READY / PR_MERGED_MAIN | PR #527 merged |
| feat/item-discovery-view | +3 / -3 | DELETE_READY / PR_MERGED_MAIN | PR #529 merged |
| feat/kryvion-airdrops | +5 / -881 | DELETE_READY / PR_MERGED_MAIN | PR #255 merged |
| feat/leasing-lifecycle-intelligence | +10 / -1409 | DELETE_READY / SUPERSEDED_FAMILY | PR #104 closed; production successor retained on main |
| feat/leasing-lifecycle-intelligence-v2 | +9 / -1407 | DELETE_READY / SUPERSEDED_FAMILY | PR #106 closed; exclusive subfeatures preserved in #107/#109 refs |
| feat/leasing-lifecycle-production | +2 / -1389 | DELETE_READY / PR_MERGED_MAIN | PR #110 merged |
| feat/lifecycle-write-breaker | +0 / -1419 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/mission-control-observability-v2 | +12 / -1479 | DELETE_READY / PR_MERGED_MAIN | PR #83 merged |
| feat/nexus-discovery-v2 | +5 / -2004 | DELETE_READY / PR_MERGED_MAIN | PR #5 merged |
| feat/nexus-profitability-50 | +0 / -277 | DELETE_READY / MAIN_ANCESTOR | no unique commits |
| feat/payflow-domain | +6 / -1890 | DELETE_READY / SUPERSEDED_FAMILY | PR #15 closed; v2 PR #16 merged |
| feat/generic-organization-taxonomy-20260905 | +12 / -1160 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #169 open/non-mergeable; CI 33979634772 failed |
| feat/generic-scheduling-domain | +8 / -1542 | UNIQUE_USEFUL / KEEP_SELECTIVE | 17-file scheduling/auth delta; no PR |
| feat/global-public-discovery-search | +1 / -1188 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #161 now mergeable but CI 33973174405 failed |
| feat/google-place-picker-v2 | +1 / -1232 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #148 open/non-mergeable; CI 33928282085 failed |
| feat/important-events-center | +9 / -994 | UNIQUE_USEFUL / KEEP_SELECTIVE | event/mail/migration delta; no PR |
| feat/kryvion-email-notifications | +6 / -1147 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #182 open/non-mergeable; CI 33985053951 failed |
| feat/leasing-production-governance | +9 / -1388 | UNIQUE_USEFUL / KEEP_REBASE_REQUIRED | PR #111 CI passed historically but is non-mergeable and 1,388 behind |
| feat/location-aware-event-discovery | +9 / -1163 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #167 open/non-mergeable; CI 33978834968 failed |
| feat/media-library-platform | +20 / -1 | UNIQUE_USEFUL / KEEP_CI_BLOCKED | PR #534 open/mergeable; CI 36343439430 failed |

## Classification summary

- MAIN_ANCESTOR: 13
- PR_MERGED_MAIN: 11
- SUPERSEDED_FAMILY / SUPERSEDED_HISTORICAL: 5
- UNIQUE_USEFUL: 11

## High-risk second review

Thirty-one refs touched finance/payouts/subscriptions, auth/identity, leasing migrations and governance, scheduling authorization, event email delivery, Media Library storage/migrations, or broad historical integrations.

- No payout, subscription, auth, leasing, PayFlow, webhook or migration delta was integrated.
- `generic-pix-beneficiary-payouts` remains delete-ready only because PR #45 is merged to main; FIN-P0-001 was not touched.
- PR #111 has historical green CI but remains unsafe to merge directly because it is non-mergeable and 1,388 commits behind.
- PR #161 becoming mergeable does not override its failed CI or 1,188-commit age.
- API #534 remains unmerged because its current PR workflow failed.
- No ref was deleted because delete-ref is unavailable.

## Owner actions

1. Review `generic-portfolio-analytics` and `generic-resource-operations` for selective recovery; do not delete them with the old allowlist.
2. Rebase and obtain green current-main CI for viable open PRs before integration.
3. Recheck every branch head immediately before executing the 29-ref delete allowlist.
