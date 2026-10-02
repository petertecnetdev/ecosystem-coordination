# W08 API branch hygiene — fix completion and refactor start

Date: 2026-10-02 20:38 America/Sao_Paulo
Worker: Navigation Weaver (W08)
Repository: petertecnetdev/api.petertecnet.com.br
Scope: remaining fix/* inventory positions 81–112 plus refactor/* positions 1–8. Excludes W07 agent/* shard and does not implement FIN-P0-001.

## Admin Center status

- Branches remain exactly: main, feat/media-library-admin, feat/cutinapp-admin-email-composer.
- main: KEEP at 9c649f5537afe1dbd9bc486a4bf7a2e7df765c4f; GitHub still reports protected=false.
- feat/cutinapp-admin-email-composer: DELETE_READY_SOURCE; PR #2 was merged and deployed in the prior run.
- feat/media-library-admin: KEEP; PR #1 remains open/mergeable but depends on API PR #534, whose CI remains red.

## Metrics

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 32
- HIGH_RISK_SECOND_REVIEWS: 24
- UNIQUE_USEFUL_THIS_RUN: 8
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 11 refactor/* branches
- fix/* shard remaining: 0

## Branch decisions

| Branch | Decision | Evidence |
|---|---|---|
| fix/order-removal-pricing | DELETE_READY / PR_MERGED | PR #313 merged |
| fix/organization-soft-delete-20260904 | DELETE_READY / PR_MERGED | PR #115 merged |
| fix/p0-disable-non-idempotent-payouts | UNIQUE_USEFUL / KEEP_CLAIMED | Draft PR #485; FIN-P0-001 family, owner review required |
| fix/p0-payout-idempotency-boundary | DELETE_READY / PATCH_EQUIVALENT | compare to main reports files=[] |
| fix/p0-payout-idempotency-fresh-main | UNIQUE_USEFUL / KEEP_CLAIMED | Draft PR #500; current-main reconciliation candidate |
| fix/p0-stable-payout-idempotency | UNIQUE_USEFUL / KEEP_CLAIMED | Draft PR #486 is the explicit FIN-P0-001 blocker/claim |
| fix/plat-recognized-revenue-dashboard | DELETE_READY / PR_MERGED | PR #406 merged |
| fix/producer-engagement-release | UNIQUE_USEFUL / KEEP | PR #294 open; engagement/email behavior remains exclusive |
| fix/production-establishment-profile-20260904 | UNIQUE_USEFUL / KEEP_HIGH_RISK | PR #138 open; profile/migration design remains exclusive |
| fix/production-onboarding-hardening-18 | UNIQUE_USEFUL / KEEP_MIXED | No PR; contains readiness, smoke, CORS, monitoring and performance contracts requiring selective recovery |
| fix/production-rating-metrics-20260905 | DELETE_READY / PR_MERGED | PR #180 merged |
| fix/public-application-transport-boundary | DELETE_READY / SUPERSEDED_FAMILY | PR #176 closed; later architecture work exists on main |
| fix/rasoio-disponibilidade-real | DELETE_READY / PR_MERGED | PR #10 merged |
| fix/rasoio-owner-como-colaborador | DELETE_READY / PR_MERGED | PR #11 merged |
| fix/rasoio-owner-manager-legacy-endpoint | DELETE_READY / PR_MERGED | PR #12 merged |
| fix/rasoio-remocao-colaborador-resposta | DELETE_READY / PR_MERGED | PR #13 merged |
| fix/rate-limit-isolation-20260905 | DELETE_READY / PR_MERGED | PR #194 merged |
| fix/reconcile-underfulfilled-paid-orders | DELETE_READY / MAIN_ANCESTOR_PR_MERGED | ahead=0; PR #436 merged |
| fix/resilient-realtime-broadcast | DELETE_READY / PR_MERGED | PR #202 merged |
| fix/revenue-external-pix-recovery | DELETE_READY / PR_MERGED | PR #408 merged |
| fix/revenue-preserve-paid-renewal-days | DELETE_READY / PR_MERGED | PR #416 merged |
| fix/revenue-subscription-recovery-claim | DELETE_READY / PR_MERGED | PR #413 merged |
| fix/revenue-subscription-renewal-recovery-20260913 | DELETE_READY / PR_MERGED | PR #414 merged |
| fix/scheduling-adjacent-appointments | DELETE_READY / PR_MERGED | PR #324 merged |
| fix/scheduling-reassignment-availability | DELETE_READY / PR_MERGED | PR #319 merged |
| fix/scheduling-recurring-block-availability | DELETE_READY / PR_MERGED | PR #321 merged |
| fix/sqlite-production-consolidation-fks | DELETE_READY / PATCH_EQUIVALENT | Migration blob exactly equals main; PR #146 closed this run |
| fix/subscription-pix-retry | DELETE_READY / PR_MERGED | PR #453 merged |
| fix/timeline-standalone-posts | UNIQUE_USEFUL / KEEP | PR #231 open; social_posts migration and standalone posting absent on main |
| fix/unified-auth-google-identifiers | UNIQUE_USEFUL / KEEP_HIGH_RISK | PR #33 open; identifier migration absent on main, requires current-main auth/data review |
| fix/weekly-agenda-delay-max-6-20260910 | DELETE_READY / PR_MERGED | PR #352 merged |
| hotfix/direct-pusher-email | DELETE_READY / MAIN_ANCESTOR | ahead=0, behind=1, files=[] |
| refactor/commerce-domain-maturity | DELETE_READY / PR_MERGED | PR #58 merged |
| refactor/contract-generic-database-storage-20260903 | DELETE_READY / PR_MERGED | PR #94 merged |
| refactor/domain-controller-architecture | DELETE_READY / SUPERSEDED_FAMILY | PR #44 closed this run; 1,571 behind and superseded by merged architecture work |
| refactor/finalize-generic-platform-20260903 | DELETE_READY / PR_MERGED | PR #87 merged |
| refactor/generic-api-main-integration-20260903 | DELETE_READY / SUPERSEDED_FAMILY | PR #61 closed this run; 1,537 behind and superseded by current main |
| refactor/generic-api-staging-integration-20260903 | DELETE_READY / SUPERSEDED_FAMILY | PR #62 closed this run; 1,537 behind and superseded by current main |
| refactor/generic-cutinapp-api-20260903 | DELETE_READY / PR_MERGED | PR #60 merged |
| refactor/generic-platform-hardening-20260904-v2 | DELETE_READY / MAIN_ANCESTOR | ahead=0, files=[] |

## High-risk second reviews

24 branches received second review because they touch finance, auth, webhooks, migrations, production isolation or very large architecture integrations. Key results:

- The four payout branches were kept out of implementation. The no-diff boundary branch is DELETE_READY; #485/#486/#500 remain preserved for the FIN-P0-001 owner to select one current path.
- SQLite consolidation migration is byte-for-byte identical to main; PR #146 was safely closed.
- Unified auth identifiers remain exclusive and risky; PR #33 was preserved.
- Production establishment/profile and onboarding hardening contain exclusive migration/runtime contracts and were preserved.
- Revenue recognition, paid-order reconciliation, Pix recovery/retry and subscription recovery branches were already merged.
- Old refactor integration families are 1,500+ commits behind; merged successors/current main supersede them.

## PR actions

Closed without merge:
- #44 — superseded domain-controller architecture refactor.
- #61 — obsolete generic main integration.
- #62 — obsolete generic staging integration.
- #146 — SQLite migration already identical to main.

No branch was deleted because delete-ref remains unavailable. No branch was created.
