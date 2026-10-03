# W08 — DELETE_READY revalidation manifest B

Date: 2026-10-03  
Repository: `petertecnetdev/api.petertecnet.com.br`  
Scope: historical `automation/*` positions 55–94  
Current main: `5fea1752fb674dd463b65bb2069f2c13117e2749`

## Metrics

- REVIEWED_THIS_RUN: **40**
- DELETE_READY_THIS_RUN: **40**
- HIGH_RISK_SECOND_REVIEWS: **36**
- UNIQUE_USEFUL_THIS_RUN: **0**
- NEW_BRANCHES_CREATED: **0**
- REMAINING_API_SHARD: **0**
- References deleted: **0** — delete-ref unavailable.

## Admin Center

- Exactly three branches remain.
- `main`: **KEEP**, protection gap remains.
- PR #1: **KEEP_BLOCKED** by API #534 without green validation.
- PR #2: **MERGED**; source remains **DELETE_READY**.

## Exclusive classification

### MAIN_ANCESTOR — 23

- `automation/payment-health-diagnosis-r15` — fresh compare reports `ahead=0`.
- `automation/payment-health-incidents-r14` — fresh compare reports `ahead=0`.
- `automation/payment-health-recovery-attribution-r16` — fresh compare reports `ahead=0`.
- `automation/payment-health-recovery-r13` — fresh compare reports `ahead=0`.
- `automation/payment-health-risk-r11` — fresh compare reports `ahead=0`.
- `automation/payment-reconciliation-persistence-r11` — fresh compare reports `ahead=0`.
- `automation/payment-reconciliation-telemetry-r12` — fresh compare reports `ahead=0`.
- `automation/payment-retry-after-r11` — fresh compare reports `ahead=0`.
- `automation/payout-identity-safety-r11` — fresh compare reports `ahead=0`.
- `automation/pix-init-recovery-economics-r11` — fresh compare reports `ahead=0`.
- `automation/pix-postcopy-funnel-r11` — fresh compare reports `ahead=0`.
- `automation/preserve-profile-photo-ordering-r17` — fresh compare reports `ahead=0`.
- `automation/profitability-financial-dashboard` — fresh compare reports `ahead=0`.
- `automation/profitability-recovery-segment-probability` — fresh compare reports `ahead=0`.
- `automation/profitability-risk-queue-v2` — fresh compare reports `ahead=0`.
- `automation/profitability-top-recovery-opportunities` — fresh compare reports `ahead=0`.
- `automation/provider-failure-r11` — fresh compare reports `ahead=0`.
- `automation/provider-init-failure-r12` — fresh compare reports `ahead=0`.
- `automation/public-event-ticket-availability` — fresh compare reports `ahead=0`.
- `automation/r11-commerce-webhook-compat-latest` — fresh compare reports `ahead=0`.
- `automation/r11-treatment-attribution` — fresh compare reports `ahead=0`.
- `automation/r13-reconciliation-alerts` — fresh compare reports `ahead=0`.
- `automation/r14-reconciliation-app-breakdown` — fresh compare reports `ahead=0`.

### PR_MERGED — 13 divergent historical heads

- `automation/plat-guest-checkout-r6` — PR #424 freshly confirmed `merged=true`.
- `automation/plat-guest-pix-api-r9` — PR #439 freshly confirmed `merged=true`.
- `automation/plat-payment-retry-r12` — PR #432 freshly confirmed `merged=true`.
- `automation/plat-pix-recovery-deeplink-r21` — PR #395 freshly confirmed `merged=true`.
- `automation/profitability-confidence-adjusted-value` — PR #272 freshly confirmed `merged=true`.
- `automation/profitability-dashboard-alert-20260907` — PR #238 freshly confirmed `merged=true`.
- `automation/profitability-recovery-action-cost` — PR #263 freshly confirmed `merged=true`.
- `automation/profitability-recovery-break-even-margin` — PR #269 freshly confirmed `merged=true`.
- `automation/profitability-recovery-guardrails` — PR #268 freshly confirmed `merged=true`.
- `automation/profitability-recovery-roi` — PR #267 freshly confirmed `merged=true`.
- `automation/profitable-pix-recovery-cta` — PR #306 freshly confirmed `merged=true`.
- `automation/public-scheduling-availability-r5` — PR #427 freshly confirmed `merged=true`.
- `automation/public-sellable-inventory-run11` — PR #325 freshly confirmed `merged=true`.

### SUPERSEDED_FAMILY — 2

- `automation/plat-pix-recovery-deeplink-r19`
- `automation/plat-pix-recovery-deeplink-r20`

Both older refs share the same recovery service blob as r21, and all three share the same `config/checkout_recovery.php` blob as current main. r21 was merged through PR #395; current main further evolves the service.

### PATCH_EQUIVALENT / SUPERSEDED — 2

- `automation/precheckout-funnel-r11`: current main contains the event-view and ticket-intent stages, conversion ratios, intent-surface aggregation and newer normalized recommendation codes. `RevenueRecoveryEconomicsService.php` is byte-identical to main. Historical PR #450 was already closed without merge.
- `automation/rasoio-renewal-final-reminder-r6`: renewal service and focused test are byte-identical to current main.

## High-risk second review

Thirty-six refs touch payments, payout identity, reconciliation, PIX, guest checkout, webhook compatibility, recovery economics or profitability. None was merged or modified in this review.

Fresh evidence:

- All 36 referenced historical PRs remain closed with `merged=true`.
- Twenty-three refs are direct ancestors of current main.
- The r19/r20/r21 configuration blob is identical to main: `eb21d87cdf4e293edf676cd525dbdc2f2317b491`.
- The r19/r20/r21 recovery service blob is identical across the family; main contains a later version.
- Rasoio renewal service and test match main exactly.
- Precheckout economics service matches main exactly; remaining funnel behavior is present under later normalized stage/action names.

## Evidence correction

The earlier audit linked `automation/provider-init-failure-r12` to PR #425. Fresh PR inspection shows #425 belongs to `automation/checkout-readiness-atomic-r11`. The provider-init branch remains DELETE_READY solely because the fresh compare reports `ahead=0`; the incorrect PR association is removed.

## Deletion gate

This file is an exact allowlist. Recheck branch heads immediately before deletion. Never delete `main`, `staging`, W07 `agent/*`/`w07/*`, FIN-P0-001 owner refs, or any branch not listed here.
