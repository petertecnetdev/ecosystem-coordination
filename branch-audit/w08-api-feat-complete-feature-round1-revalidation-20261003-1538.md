# W08 API branch hygiene — feat completion + feature round 1 revalidation

Date: 2026-10-03 15:38 America/Sao_Paulo  
Worker: Navigation Weaver (cutinapp-visual-w08)  
Repository: petertecnetdev/api.petertecnet.com.br  
API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`  
Scope: final 15 `feat/*` refs plus first 25 `feature/*` refs. W07 prefixes and FIN-P0-001 excluded.

## Admin Center status

- Exactly three branches.
- `main`: **KEEP / PROTECTION_GAP**.
- PR #2: **MERGED / DELETE_READY_SOURCE**.
- PR #1: **KEEP / BLOCKED** by open API #534 and failed CI 36343439430.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 31
- HIGH_RISK_SECOND_REVIEWS: 26
- UNIQUE_USEFUL_THIS_RUN: 9
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0

## MAIN_ANCESTOR — DELETE_READY (10)

`feat/stop-branch-loop`, `feat/user-profile-background-20260905`, `feature/admin-copilot-v2`, `feature/admin-user-communications-20260906`, `feature/admin-user-communications-mainready-20260906`, `feature/commerce-coupons`, `feature/creative-director-v2`, `feature/cutinapp-participant-social-v2`, `feature/cutinapp-payments`, `feature/direct-instagram-level-20260911`.

All have `ahead_by=0` against current main.

## PR_MERGED_MAIN — DELETE_READY (15)

| Branch | PR |
|---|---:|
| feat/sellable-free-ticket-signals | #327 |
| feat/subscription-intents-profitability | #322 |
| feat/subscription-pix-lifecycle | #334 |
| feat/subscription-plan-entitlements | #336 |
| feat/ticket-multi-event-20260908 | #283 |
| feat/ticket-sales-cutoff-rule-20260908 | #285 |
| feat/weekly-agenda-event-picker | #517 |
| feat/weekly-event-agenda-20260905 | #185 |
| feature/acquisition-agent | #128 |
| feature/admin-financial-control-center | #32 |
| feature/application-branding-manager-20260903 | #81 |
| feature/application-runtime-controls-20260911 | #359 |
| feature/cutinapp-admin-impersonation | #350 |
| feature/cutinapp-artist-groups | #28 |
| feature/ecosystem-impersonation-v2 | #341 |

## SUPERSEDED / HISTORICAL — DELETE_READY (6)

- `feat/social-feed-facebook-main`: superseded by later feed/timeline families.
- `feature/admin-command-center-v2`: PR #38 merged into staging, not main; current command-center implementation supersedes the 1,582-behind historical delta.
- `feature/cutinapp-domain-2026`: PR #9 closed; stale monolith, 1,995 behind.
- `feature/cutinapp-mercadopago-auto-split-20260918`: superseded by retained v2 PR #502.
- `feature/cutinapp-participant-social`: PR #178 closed; v2 #179 merged and branch is ancestral.
- `feature/ecosystem-impersonation`: superseded by merged v2 #341.

## UNIQUE_USEFUL — preserve (9)

| Branch | Current evidence | Decision |
|---|---|---|
| feat/ride-events | PR #266 open/non-mergeable; CI 34200117606 failed | KEEP_SELECTIVE |
| feat/social-feed-v2 | PR #222 open/non-mergeable; CI 34097390612 failed | KEEP_SELECTIVE |
| feat/social-timeline-v2 | PR #227 open/non-mergeable; CI 34087848078 failed | KEEP_HIGH_RISK |
| feat/universal-whatsapp-notifications | PR #526 open/mergeable, 9 behind; CI 36152254466 failed | KEEP_CI_BLOCKED |
| feature/admin-copilot | PR #125 open/non-mergeable, 1321 behind; historical CI 33886165060 passed | KEEP_REBASE_REQUIRED |
| feature/ambient-media | PR #130 open/non-mergeable, 1302 behind; historical CI 33894069638 passed | KEEP_REBASE_REQUIRED |
| feature/blog-performance-instagram | PR #153 open/mergeable, 1207 behind; CI 33941715716 failed | KEEP_CI_BLOCKED |
| feature/cutinapp-event-opening-media | PR #186 open/non-mergeable; CI 33990228285 failed | KEEP_SELECTIVE |
| feature/cutinapp-mercadopago-auto-split-20260918-v2 | PR #502 open/non-mergeable; CI 35414867351 failed | KEEP_FINANCE_OWNER |

## Evidence correction

The old association of `feature/admin-user-communications-mainready-20260906` with PR #212 is not the reason for deletion: PR #212 has a different head branch. The ref remains delete-ready because it is a direct ancestor of current main (`ahead_by=0`).

## High-risk second review

Twenty-six refs touched payments, subscriptions, PIX, auth/impersonation, webhooks, migrations, WhatsApp, financial administration, runtime controls or social automation.

- No high-risk code was integrated.
- PRs #526 and #153 are mergeable but CI failed.
- PRs #125 and #130 have historical green CI but require rebase/current-main review due age and conflicts.
- PR #502 remains under finance ownership.
- No ref was deleted because delete-ref is unavailable.

## Next actions

Rebase and obtain current green CI for preserved candidates; recheck all 31 delete-ready heads before deletion.
