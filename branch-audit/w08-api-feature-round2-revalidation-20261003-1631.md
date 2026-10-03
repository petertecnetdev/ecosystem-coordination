# W08 API feature/* round 2 revalidation — 2026-10-03

## Scope and guardrails

- Repository: `petertecnetdev/api.petertecnet.com.br`
- Shard: historical `feature/*` positions 26–65 (40 branches)
- Current API main: `5fea1752fb674dd463b65bb2069f2c13117e2749`
- W07 overlap: none; `agent/*` and `w07/*` remain excluded
- FIN-P0-001: excluded and left with its existing owner
- Branches created: 0
- Refs deleted: 0; delete-ref capability remains unavailable

## Admin Center status

- `main`: **KEEP**, with known protection gap.
- `feat/cutinapp-admin-email-composer`: **DELETE_READY**; PR #2 is merged.
- `feat/media-library-admin`: **KEEP / BLOCKED**; PR #1 is open and mergeable, while required API PR #534 remains open with failed API CI run 36343439430.
- Repository inventory remains exactly three branches.

## API classification

| # | Branch | Current disposition | Fresh evidence |
|---:|---|---|---|
| 26 | feature/event-items-bulk-selection | DELETE_READY · MAIN_ANCESTOR | 0 ahead / 818 behind |
| 27 | feature/event-list-weekly-agenda-strategy-20260910 | DELETE_READY · PR_MERGED | PR #349 merged |
| 28 | feature/event-producer-notifications | UNIQUE_USEFUL · REVIEW | Still diverged; not an ancestor of merged v2 |
| 29 | feature/event-producer-notifications-v2 | DELETE_READY · PR_MERGED | PR #189 merged |
| 30 | feature/event-production-prefill | UNIQUE_USEFUL · KEEP | PR #145 open/non-mergeable; migration delta |
| 31 | feature/financial-ledger-reconciliation-20260903 | DELETE_READY · PR_MERGED | PR #64 merged; historical finance family |
| 32 | feature/generic-catalog-production-20260902 | DELETE_READY · PR_MERGED | PR #52 merged |
| 33 | feature/generic-commerce-checkout | UNIQUE_USEFUL · REVIEW | No canonical merged PR; checkout/migration delta |
| 34 | feature/generic-fulfillment-qr-privacy-20260902 | DELETE_READY · PR_MERGED | PR #57 merged |
| 35 | feature/generic-social-messaging | DELETE_READY · MAIN_ANCESTOR | 0 ahead |
| 36 | feature/generic-social-messaging-copy | DELETE_READY · MAIN_ANCESTOR / PR_MERGED | 0 ahead; PR #248 merged |
| 37 | feature/global-ecosystem-sso | UNIQUE_USEFUL · KEEP | PR #70 open/non-mergeable; auth/migration |
| 38 | feature/global-social-feed | UNIQUE_USEFUL · KEEP | PR #184 open/non-mergeable; migration |
| 39 | feature/identity-production-hardening-v3 | UNIQUE_USEFUL · REVIEW | Diverged from identity-sso-hardening; auth/security/migrations |
| 40 | feature/identity-sso-hardening | UNIQUE_USEFUL · KEEP | PR #80 open/non-mergeable |
| 41 | feature/laora-production | DELETE_READY · MAIN_ANCESTOR | 0 ahead |
| 42 | feature/laora-production-hardening | DELETE_READY · PR_MERGED | PR #39 merged |
| 43 | feature/leasing-contextual-roles | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #114 merged |
| 44 | feature/media-library-multi-media | UNIQUE_USEFUL · KEEP | PR #296 open/mergeable; API CI 34303975115 failed |
| 45 | feature/nexus-item-social-share-20260902 | UNIQUE_USEFUL · KEEP | PR #49 open/non-mergeable; base staging |
| 46 | feature/peter-account-ecosystem | UNIQUE_USEFUL · REVIEW | Diverged from merged v2; auth/account delta |
| 47 | feature/peter-account-ecosystem-v2 | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #29 merged |
| 48 | feature/peter-identity-core-v2 | UNIQUE_USEFUL · KEEP | PR #78 open/non-mergeable; auth/migration |
| 49 | feature/producer-assisted-onboarding | UNIQUE_USEFUL · KEEP | PR #494 open/non-mergeable; agreements/payment readiness |
| 50 | feature/producer-engagement-email | UNIQUE_USEFUL · KEEP | PR #279 open/non-mergeable |
| 51 | feature/producer-media-library | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 52 | feature/producer-media-library-clean | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 53 | feature/producer-media-library-final | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 54 | feature/producer-media-library-final2 | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 55 | feature/producer-media-library-pr | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 56 | feature/producer-media-library-ready | DELETE_READY · PR_MERGED | PR #278 merged |
| 57 | feature/producer-media-library-release | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 58 | feature/producer-media-library-v2 | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 59 | feature/producer-media-library-v3 | DELETE_READY · SAME_HEAD FAMILY | Duplicate historical media-library head |
| 60 | feature/property-intelligence-20 | UNIQUE_USEFUL · KEEP | PR #121 open/non-mergeable; schema delta |
| 61 | feature/property-management | UNIQUE_USEFUL · KEEP | PR #90 open/non-mergeable; schema delta |
| 62 | feature/provider-settlement-statements-20260903 | UNIQUE_USEFUL · KEEP | PR #66 open/mergeable with API CI 33763991738 green, but base is staging and finance review is required |
| 63 | feature/public-nexus-services-by-cnpj | DELETE_READY · PR_MERGED | PR #18 merged |
| 64 | feature/rasoio-operations-dashboard | DELETE_READY · MAIN_ANCESTOR | 0 ahead |
| 65 | feature/recovery-channel-attribution-20260908 | DELETE_READY · PR_MERGED | PR #276 merged |

## High-risk second review

Sixteen branches touching finance, checkout, auth/security, privacy, webhooks or migrations were reclassified a second time. No high-risk branch was merged, closed, or deleted in this run.

Notable outcomes:

- PR #66 has green historical branch CI, but targets `staging`, not `main`; its provider-settlement schema and Mercado Pago reporting integration remain owner-review work.
- PRs #70, #78 and #80 remain non-mergeable identity/auth changes.
- PR #494 still mixes onboarding, agreements and payment readiness.
- PRs #90 and #121 remain non-mergeable schema-heavy property families.
- PR #296 is mergeable but its branch CI is red.
- The old producer-notification and Peter Account branches are genuinely divergent from their v2 relatives, so they were not falsely promoted to DELETE_READY.

## Totals

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 24
- HIGH_RISK_SECOND_REVIEWS: 16
- UNIQUE_USEFUL_THIS_RUN: 16
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 0
