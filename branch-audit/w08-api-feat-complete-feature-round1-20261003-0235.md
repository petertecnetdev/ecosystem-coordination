# W08 API feat completion + feature round 1 — 2026-10-03 02:35 BRT

## Scope

Completed the final 15 `feat/*` branches (positions 190–204) and reviewed `feature/*` positions 1–25. Active claims and W07 were re-read; W07 did not own either lexical shard.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 31
- HIGH_RISK_SECOND_REVIEWS: 26
- UNIQUE_USEFUL_THIS_RUN: 9
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 45 (`feature/*`)
- REMAINING_FEAT_SHARD: 0

## DELETE_READY

| Branch | Objective reason |
|---|---|
| feat/sellable-free-ticket-signals | PR #327 merged |
| feat/social-feed-facebook-main | superseded by later social feed/timeline families |
| feat/stop-branch-loop | MAIN_ANCESTOR / PR #100 merged |
| feat/subscription-intents-profitability | PR #322 merged |
| feat/subscription-pix-lifecycle | PR #334 merged |
| feat/subscription-plan-entitlements | PR #336 merged |
| feat/ticket-multi-event-20260908 | PR #283 merged |
| feat/ticket-sales-cutoff-rule-20260908 | PR #285 merged |
| feat/user-profile-background-20260905 | MAIN_ANCESTOR / PR #175 merged |
| feat/weekly-agenda-event-picker | PR #517 merged |
| feat/weekly-event-agenda-20260905 | PR #185 merged |
| feature/acquisition-agent | PR #128 merged |
| feature/admin-command-center-v2 | PR #38 merged |
| feature/admin-copilot-v2 | MAIN_ANCESTOR |
| feature/admin-financial-control-center | PR #32 merged |
| feature/admin-user-communications-20260906 | MAIN_ANCESTOR / PR #214 merged |
| feature/admin-user-communications-mainready-20260906 | MAIN_ANCESTOR / PR #212 merged |
| feature/application-branding-manager-20260903 | PR #81 merged |
| feature/application-runtime-controls-20260911 | PR #359 merged |
| feature/commerce-coupons | MAIN_ANCESTOR / PR #275 merged |
| feature/creative-director-v2 | MAIN_ANCESTOR / PR #247 merged |
| feature/cutinapp-admin-impersonation | PR #350 merged |
| feature/cutinapp-artist-groups | PR #28 merged |
| feature/cutinapp-domain-2026 | PR #9 closed this run: stale monolithic domain, non-mergeable, 1995 behind |
| feature/cutinapp-mercadopago-auto-split-20260918 | superseded by v2 PR #502 |
| feature/cutinapp-participant-social | PR #178 closed this run as superseded by merged #179 |
| feature/cutinapp-participant-social-v2 | MAIN_ANCESTOR / PR #179 merged |
| feature/cutinapp-payments | MAIN_ANCESTOR / PR #30 merged |
| feature/direct-instagram-level-20260911 | MAIN_ANCESTOR / PR #368 merged |
| feature/ecosystem-impersonation | superseded by v2 PR #341 |
| feature/ecosystem-impersonation-v2 | PR #341 merged |

## UNIQUE_USEFUL — preserve for owner review

| Branch | Status |
|---|---|
| feat/ride-events | PR #266 open, non-mergeable; migration and authorization review required |
| feat/social-feed-v2 | PR #222 open, non-mergeable; selective social/media recovery |
| feat/social-timeline-v2 | PR #227 open, non-mergeable; migrations/automation review |
| feat/universal-whatsapp-notifications | PR #526 open, mergeable and only 9 behind; active WhatsApp ownership preserved |
| feature/admin-copilot | PR #125 open, non-mergeable; selective action-safety review |
| feature/ambient-media | PR #130 open, non-mergeable; migration/media review |
| feature/blog-performance-instagram | PR #153 open, non-mergeable; analytics owner review |
| feature/cutinapp-event-opening-media | PR #186 open, non-mergeable; event/media owner review |
| feature/cutinapp-mercadopago-auto-split-20260918-v2 | PR #502 open, non-mergeable; financial owner and independent review required |

## High-risk second review

26 branches touching payments, subscriptions, PIX, auth/impersonation, webhooks, migrations, WhatsApp, financial administration, runtime controls or social automation were reviewed twice. No high-risk branch was merged. Active finance/payment/WhatsApp claims remain authoritative.

## Admin Center

- `main`: KEEP at `9c649f5`; GitHub still reports `protected=false`.
- `feat/cutinapp-admin-email-composer`: STALE/DELETE_READY because PR #2 is merged.
- `feat/media-library-admin`: KEEP/BLOCKED; PR #1 is mergeable but API #534 validation remains red.
