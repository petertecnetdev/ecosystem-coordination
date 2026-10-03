# W08 API mixed owner-resolution revalidation — 2026-10-03 18:31

Worker: Navigation Weaver (cutinapp-visual-w08)  
Repository: petertecnetdev/api.petertecnet.com.br  
API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`

## Scope

Fresh comparison of 40 non-W07 refs: 11 remaining `feature/*` deltas, 15 mixed-prefix selective-recovery candidates and 14 established DELETE_READY candidates. FIN-P0-001 was excluded.

## Admin Center

- Exactly three branches remain.
- `main`: **KEEP / PROTECTION_GAP**.
- PR #1: **KEEP / BLOCKED**; open/mergeable, but API #534 remains open with CI 36343439430 failed.
- PR #2: **MERGED / DELETE_READY_SOURCE**.

## DELETE_READY — 14

| Branch | Classification | Fresh evidence |
|---|---|---|
| perf/ecosystem-hardening-20260908 | SUPERSEDED_FAMILY | PR #290 closed; surviving #308 retained |
| production/rasoio-20260902 | PR_MERGED_STAGING / HISTORICAL | PR #42 merged to staging; 1,571 behind |
| profit/recovery-surface-economics-20260909 | PR_MERGED_MAIN | PR #310 merged |
| profit/recovery-surface-maturity | PR_MERGED_MAIN | PR #311 merged |
| profitability/checkout-recovery-deeplink | PR_MERGED_MAIN | PR #293 merged |
| profitability/pix-recovery-timing-experiment | PR_MERGED_MAIN | PR #305 merged |
| revenue/enforce-staff-entitlement-plat | PR_MERGED_MAIN | PR #348 merged |
| revenue/recover-subscription-intent | PR_MERGED_MAIN | PR #354 merged |
| revenue/subscription-pix-email-recovery | PR_MERGED_MAIN | PR #409 merged |
| review/api-core-hardening | PR_MERGED_MAIN / HISTORICAL | PR #2 merged; 2,019 behind |
| security/dependency-audit-20260904 | PR_MERGED_MAIN | PR #136 merged |
| seo/dynamic-sitemap-20260908 | PR_MERGED_MAIN | PR #284 merged |
| tmp-noop | MAIN_ANCESTOR | 0 ahead / 1,457 behind |
| w08/artist-claim-relations | PR_MERGED_MAIN | PR #536 merged |

## UNIQUE_USEFUL — preserve 26

- `feature/identity-production-hardening-v3`: 41 unique commits; identity/security migration family.
- `feature/identity-sso-hardening`: PR #80 open/non-mergeable.
- `feature/media-library-multi-media`: PR #296 open/mergeable; CI failed.
- `feature/nexus-item-social-share-20260902`: PR #49 open/non-mergeable against staging.
- `feature/peter-account-ecosystem`: exclusive account/SSO delta.
- `feature/peter-identity-core-v2`: PR #78 open/non-mergeable.
- `feature/producer-assisted-onboarding`: PR #494 open/non-mergeable.
- `feature/producer-engagement-email`: PR #279 open/non-mergeable.
- `feature/property-intelligence-20`: PR #121 open/non-mergeable.
- `feature/property-management`: PR #90 open/non-mergeable.
- `feature/provider-settlement-statements-20260903`: PR #66 open/mergeable with historical green CI, but base is staging.
- `perf/api-production-hardening-20260918`: PR #488 open/non-mergeable.
- `perf/ecosystem-hardening-20260909`: PR #308 open/non-mergeable; surviving family head.
- `preserve/vps-event-commerce-items-20260906`: one exclusive preservation patch.
- `product-core/media-context-contract`: PR #471 open/non-mergeable.
- `quality/payout-release-guard`: exclusive payout obligation service/test delta.
- `security/admin-access-lockdown-20260904`: PR #151 open/non-mergeable.
- `security/artist-claim-app-isolation`: PR #478 open/non-mergeable.
- `security/self-service-registration-20260902`: stale 76-commit monolith, but authorization guard remains exclusive.
- `feat/cutinapp-blog-growth`: PR #530 open/mergeable; content-growth delta.
- `automation/support-financial-context-triage-v3`: PR #473 open/mergeable; financial support policy.
- `perf/acquisition-margin-query`: PR #234 open/non-mergeable.
- `feature/revive-event`: PR #358 open/non-mergeable.
- `feature/subscriptions-mercadopago`: payment/subscription migration delta.
- `admincenter-security`: exclusive Admin Center owner middleware/config.
- `chore/ecosystem-request-correlation`: exclusive request-correlation middleware/test.

## High-risk second review

Twenty-six refs matched finance, checkout, subscriptions, identity/auth, security, jobs, webhooks or migrations. No such branch was merged or deleted.

Important gates:

- PR #66 is green only against `staging`; it is not merge-ready for `main`.
- `quality/payout-release-guard`, PR #473, PR #234 and subscription/payment candidates remain finance-owner work.
- Identity PRs #78/#80 and security PRs #151/#478 remain non-mergeable.
- Historical merged finance/revenue refs are DELETE_READY only because their canonical PRs are already integrated; heads must be rechecked before deletion.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 14
- HIGH_RISK_SECOND_REVIEWS: 26
- UNIQUE_USEFUL_THIS_RUN: 26
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0
- REFS_DELETED: 0
