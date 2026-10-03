# W08 — automation tail + mixed-prefix revalidation

Date: 2026-10-03  
Repository: `petertecnetdev/api.petertecnet.com.br`  
Current main: `5fea1752fb674dd463b65bb2069f2c13117e2749`

## Metrics

- REVIEWED_THIS_RUN: **40**
- DELETE_READY_THIS_RUN: **37**
- HIGH_RISK_SECOND_REVIEWS: **35**
- UNIQUE_USEFUL_THIS_RUN: **3**
- NEW_BRANCHES_CREATED: **0**
- REMAINING_API_SHARD: **0**
- References deleted: **0**

## Admin Center

- Exactly three branches remain.
- `main`: **KEEP**, protection gap remains.
- PR #1: **KEEP_BLOCKED**; API #534 remains open.
- PR #2: **MERGED**; source remains **DELETE_READY**.

## DELETE_READY — 37

### MAIN_ANCESTOR — 15

- `automation/reconcile-prod-discovery-r11` — fresh compare reports `ahead=0`.
- `automation/recovery-cohort-confidence-r12` — fresh compare reports `ahead=0`.
- `automation/recovery-confidence-r11` — fresh compare reports `ahead=0`.
- `automation/recovery-journey-economics-r11` — fresh compare reports `ahead=0`.
- `automation/recovery-performance-by-payment` — fresh compare reports `ahead=0`.
- `automation/recovery-rollout-economics-r11` — fresh compare reports `ahead=0`.
- `automation/recovery-surface-revenue-r11` — fresh compare reports `ahead=0`.
- `automation/remove-duplicate-payment-reconcile-r18` — fresh compare reports `ahead=0`.
- `automation/subscription-recovery-cta-r6` — fresh compare reports `ahead=0`.
- `automation/subscription-renewal-grace-r11` — fresh compare reports `ahead=0`.
- `chore/cognition-runtime-config` — fresh compare reports `ahead=0`.
- `develop` — fresh compare reports `ahead=0`.
- `hotfix/direct-pusher-email` — fresh compare reports `ahead=0`.
- `infra/database-backups-20260906` — fresh compare reports `ahead=0`.
- `owner/nexus-catalog-v2` — fresh compare reports `ahead=0`.

### PR_MERGED on main — 16

- `automation/rasoio-renewal-final-reminder-r7` — PR #423 freshly confirmed `merged=true`.
- `automation/reconcile-payments-schedule` — PR #375 freshly confirmed `merged=true`.
- `automation/recovery-decision-policy-r20` — PR #342 freshly confirmed `merged=true`.
- `automation/recovery-incrementality-confidence-20260909` — PR #304 freshly confirmed `merged=true`.
- `automation/recovery-incrementality-control` — PR #302 freshly confirmed `merged=true`.
- `automation/recovery-opportunity-analytics` — PR #253 freshly confirmed `merged=true`.
- `automation/recovery-platform-revenue-priority` — PR #254 freshly confirmed `merged=true`.
- `automation/recovery-prominence-economics-v2` — PR #315 freshly confirmed `merged=true`.
- `automation/recovery-realized-profit-20260909` — PR #297 freshly confirmed `merged=true`.
- `automation/revenue-analytics-index-20260907` — PR #230 freshly confirmed `merged=true`.
- `automation/sellable-inventory-r11` — PR #323 freshly confirmed `merged=true`.
- `automation/subscription-intent-recovery-r6` — PR #363 freshly confirmed `merged=true`.
- `automation/subscription-preexpiry-reminder-r12` — PR #418 freshly confirmed `merged=true`.
- `automation/workforce-invite-r5` — PR #401 freshly confirmed `merged=true`.
- `feat-acquisition-commission-margin-guard-20260906` — PR #219 freshly confirmed `merged=true`.
- `ops/reconcile-observability-schema-20260904-v2` — PR #133 freshly confirmed `merged=true`.

### PR_MERGED to staging + historical supersession — 2

- `hardening/health-deploy-gate-20260902` — PR #53 merged to staging; 75-commit historical monolith, 1,571 commits behind.
- `hardening/public-file-privacy-20260902` — PR #54 merged to staging; 75-commit historical monolith, 1,571 commits behind.

### SUPERSEDED_FAMILY — 3

- `automation/recovery-decision-policy-r19` — superseded by r20 merged through PR #342; historical PR #340 closed.
- `automation/recovery-prominence-economics` — superseded by v2 merged through PR #315; historical PR #312 closed.
- `ops/reconcile-observability-schema-20260904` — superseded by v2 merged through PR #133.

### PATCH_EQUIVALENT — 1

- `finance/fail-closed-payout-release` — `PayoutObligationService.php` remains byte-identical to current main; rebased family merged via PR #484.

## UNIQUE_USEFUL — preserve 3

1. `automation/support-financial-context-triage-v3` / PR #473 remains open and mergeable. Main still lacks `SupportRequestIntakeService`; the branch adds financial-context priority escalation and focused tests. Preserve because its CI/architecture gate is not green.
2. `chore/ecosystem-request-correlation` remains without a PR. Main lacks the focused `RequestCorrelationTest.php`, and the middleware differs materially. Preserve for selective recovery.
3. `perf/acquisition-margin-query` / PR #234 remains open and non-mergeable. It adds bounded `lazyById` processing and database-side settlement filtering. Preserve for owner-led financial review.

## Evidence corrections

Fresh PR inspection invalidated two old associations:

- PR #531 belongs to `feat/flyer-date-consistency`, not `hotfix/direct-pusher-email`. The hotfix branch remains DELETE_READY solely because it is a direct main ancestor.
- PR #129 could not be read as a valid current PR association for `chore/cognition-runtime-config`. That branch remains DELETE_READY solely because it is a direct main ancestor.

These corrections do not weaken deletion eligibility.

## High-risk review

Thirty-five refs touch payments, payout, reconciliation, recovery economics, subscriptions, backups, acquisition margins or operational schemas. None was merged, edited or deleted in this review. The three still-exclusive deltas remain preserved.

## Deletion gate

This file is an exact 37-ref allowlist. Recheck branch heads before deletion. Never delete `main`, `staging`, W07 `agent/*`/`w07/*`, FIN-P0-001 owner refs, or any branch not explicitly listed.
