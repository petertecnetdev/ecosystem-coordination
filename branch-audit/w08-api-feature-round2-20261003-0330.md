# W08 API feature/* round 2 branch audit — 2026-10-03

## Scope and guardrails

- Repository: `petertecnetdev/api.petertecnet.com.br`
- Shard: `feature/*` positions 26–65 (40 branches)
- W07 overlap: none found in current W07 state or active claims
- Branches created: 0
- Ref deletion: unavailable; results are staged as `DELETE_READY`
- Main used for comparison: `5fea1752fb674dd463b65bb2069f2c13117e2749`

## Admin Center decision

- `main`: **KEEP**, but protection gap remains (`protected=false`, no ruleset returned).
- `feat/cutinapp-admin-email-composer`: **DELETE_READY**; PR #2 merged.
- `feat/media-library-admin`: **KEEP / BLOCKED**; PR #1 remains open and mergeable, but API PR #534 validation is failed.
- No new Admin Center analysis is needed until PR #534 or branch-protection state changes.

## API classifications

| # | Branch | Classification | Evidence / disposition |
|---:|---|---|---|
| 26 | feature/event-items-bulk-selection | DELETE_READY · MAIN_ANCESTOR | 0 ahead / 818 behind |
| 27 | feature/event-list-weekly-agenda-strategy-20260910 | DELETE_READY · PR_MERGED | PR #349 merged; migration second-reviewed |
| 28 | feature/event-producer-notifications | UNIQUE_USEFUL · REVIEW | Diverged; no PR at current head; differs from merged v2 |
| 29 | feature/event-producer-notifications-v2 | DELETE_READY · PR_MERGED | PR #189 merged |
| 30 | feature/event-production-prefill | UNIQUE_USEFUL · KEEP | PR #145 open, dirty; 3 files including migration |
| 31 | feature/financial-ledger-reconciliation-20260903 | DELETE_READY · PR_MERGED | PR #64 merged; finance/migrations second-reviewed |
| 32 | feature/generic-catalog-production-20260902 | DELETE_READY · PR_MERGED | PR #52 merged; migrations second-reviewed |
| 33 | feature/generic-commerce-checkout | UNIQUE_USEFUL · REVIEW | No PR; finance/checkout/migrations require selective recovery |
| 34 | feature/generic-fulfillment-qr-privacy-20260902 | DELETE_READY · PR_MERGED | PR #57 merged; privacy/migrations second-reviewed |
| 35 | feature/generic-social-messaging | DELETE_READY · MAIN_ANCESTOR | 0 ahead / 907 behind |
| 36 | feature/generic-social-messaging-copy | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #248 merged |
| 37 | feature/global-ecosystem-sso | UNIQUE_USEFUL · KEEP | PR #70 open/dirty; auth + migration second review |
| 38 | feature/global-social-feed | UNIQUE_USEFUL · KEEP | PR #184 open/dirty; migration second review |
| 39 | feature/identity-production-hardening-v3 | UNIQUE_USEFUL · REVIEW | No PR; auth/security/migration delta |
| 40 | feature/identity-sso-hardening | UNIQUE_USEFUL · KEEP | PR #80 open/dirty; auth/security/migrations |
| 41 | feature/laora-production | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #34 merged |
| 42 | feature/laora-production-hardening | DELETE_READY · PR_MERGED | PR #39 merged |
| 43 | feature/leasing-contextual-roles | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #114 merged |
| 44 | feature/media-library-multi-media | UNIQUE_USEFUL · KEEP | PR #296 open, mergeable/unstable; audio delta beyond merged media library |
| 45 | feature/nexus-item-social-share-20260902 | UNIQUE_USEFUL · KEEP | PR #49 open/dirty on staging; 3-file selective recovery candidate |
| 46 | feature/peter-account-ecosystem | UNIQUE_USEFUL · REVIEW | Diverged from merged v2; auth/account delta |
| 47 | feature/peter-account-ecosystem-v2 | DELETE_READY · MAIN_ANCESTOR | 0 ahead; PR #29 merged |
| 48 | feature/peter-identity-core-v2 | UNIQUE_USEFUL · KEEP | PR #78 open/dirty; auth/migration second review |
| 49 | feature/producer-assisted-onboarding | UNIQUE_USEFUL · KEEP | PR #494 open/dirty; contracts/receivables second review |
| 50 | feature/producer-engagement-email | UNIQUE_USEFUL · KEEP | PR #279 open/dirty; bounded email/reporting delta |
| 51 | feature/producer-media-library | DELETE_READY · SAME_HEAD | Same SHA as seven siblings; commit included in merged PR #278 |
| 52 | feature/producer-media-library-clean | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 53 | feature/producer-media-library-final | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 54 | feature/producer-media-library-final2 | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 55 | feature/producer-media-library-pr | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 56 | feature/producer-media-library-ready | DELETE_READY · PR_MERGED | PR #278 merged; SHA `2edcbd8` |
| 57 | feature/producer-media-library-release | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 58 | feature/producer-media-library-v2 | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 59 | feature/producer-media-library-v3 | DELETE_READY · SAME_HEAD | SHA `beb2ab3` |
| 60 | feature/property-intelligence-20 | UNIQUE_USEFUL · KEEP | PR #121 open/dirty; large asset/migration delta |
| 61 | feature/property-management | UNIQUE_USEFUL · KEEP | PR #90 open/dirty; lease migrations |
| 62 | feature/provider-settlement-statements-20260903 | UNIQUE_USEFUL · KEEP | PR #66 open/clean against staging; 31 commits ahead of merged ledger branch; finance second review |
| 63 | feature/public-nexus-services-by-cnpj | DELETE_READY · PR_MERGED | PR #18 merged |
| 64 | feature/rasoio-operations-dashboard | DELETE_READY · MAIN_ANCESTOR | 0 ahead / 2004 behind |
| 65 | feature/recovery-channel-attribution-20260908 | DELETE_READY · PR_MERGED | PR #276 merged |

## Second-review findings

Sixteen branches touched finance/auth/security/webhooks or migrations and received a second risk classification. None was merged from this historical shard. Open high-risk PRs remain KEEP/REVIEW rather than being closed or merged blindly. In particular:

- PR #66 is clean only against `staging`, not `main`; it contains 31 commits beyond the already merged ledger branch.
- PRs #70, #78 and #80 are dirty against `main` and overlap identity/auth surfaces; they require selective reconciliation.
- PR #494 mixes onboarding, agreements and payment readiness.
- Property PRs #90/#121 carry schema changes and remain dirty.

## Totals

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 24
- HIGH_RISK_SECOND_REVIEWS: 16
- UNIQUE_USEFUL_THIS_RUN: 16
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 5 (`feature/*` positions 66–70)
