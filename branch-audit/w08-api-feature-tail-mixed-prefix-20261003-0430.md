# W08 API feature tail + mixed-prefix audit — 2026-10-03

## Scope

- 40 API branches reviewed.
- Five remaining `feature/*` branches plus 35 branches from root, `architecture/*`, `audit/*`, and `automation/*`.
- `agent/*` and `w07/*` were excluded to avoid W07 overlap.
- Main comparison SHA: `5fea1752fb674dd463b65bb2069f2c13117e2749`.
- No branch was created; ref deletion remains unavailable.

## Admin Center status

The repository still has exactly three branches:

- `main`: **KEEP**, SHA `9c649f5`, but GitHub still reports `protected=false`.
- `feat/cutinapp-admin-email-composer`: **STALE / DELETE_READY**, because PR #2 is merged and deployed.
- `feat/media-library-admin`: **KEEP / BLOCKED**. PR #1 is open and clean, but API PR #534 remains `unstable`; its `validate` check failed.

## API DELETE_READY — 37

### PR_MERGED or equivalent

- `feature/recovery-channel-min-sample` — PR #282 merged.
- `feature/weekly-agenda-existing-events-20260910` — PR #344 merged.
- `feature/weekly-agenda-rolling-horizon-20260910` — PR #345 merged.
- `architecture/rebase-fail-closed-payout-release` — PR #484 merged.
- `audit/cutinapp-checkin-scope-2026-09-01` — PR #19 merged.
- `audit/cutinapp-courtesy-mutation-lock-2026-09-01` — PR #25 merged.
- `audit/cutinapp-event-capacity-2026-09-01` — PR #26 merged.
- `audit/cutinapp-private-courtesy-guard-2026-09-01` — PR #24 merged.
- `audit/cutinapp-private-event-visibility-2026-09-01` — PR #23 merged.
- `audit/cutinapp-public-production-visibility-2026-09-01` — PR #20 merged.
- `audit/cutinapp-safe-lineup-notifications-2026-09-01` — PR #22 merged.
- `audit/cutinapp-social-visible-targets-2026-09-01` — PR #21 merged.
- `audit/platform-hardening-2026-08-28` — PR #4 merged.
- `automation/acquisition-net-margin-20260907` — PR #233 merged.
- `automation/admin-fulfillment-reprocess-r11` — PR #443 merged.
- `automation/agenda-ticket-availability-r10` — PR #330 merged.
- `automation/atomic-checkout-recovery-claim-r11` — PR #410 merged.
- `automation/billing-unify-plan-catalog` — PR #468 merged.
- `automation/checkout-abandonment-alias-r19` — PR #390 merged.
- `automation/checkout-abandonment-breakdown-r11` — PR #393 merged.
- `automation/checkout-action-effectiveness-r11` — PR #365 merged.
- `automation/checkout-combined-segments-r14` — PR #398 merged.
- `automation/checkout-device-r13` — PR #397 merged.
- `automation/checkout-journey-funnel-r10` — PR #353 merged.
- `automation/checkout-period-comparison-r11` — PR #364 merged.
- `automation/checkout-production-scope-r16` — PR #400 merged.
- `automation/checkout-recovery-channel-attribution-r11` — PR #412 merged.

### MAIN_ANCESTOR / SAME_HEAD

The nine branches below share exact head `1c1072e`, are 0 commits ahead and 297 behind `main`:

- `artist-upgrade-temp`
- `artist-upgrade-temp2`
- `artist-upgrade-temp3`
- `artist-upgrade-temp4`
- `artist-upgrade-temp5`
- `artist-upgrade-temp6`
- `artist-upgrade-temp7`
- `artist-upgrade-temp8`
- `artist-upgrade-temp9`

Also `audit/nexus-app-isolation` is a direct main ancestor: 0 ahead / 2015 behind.

## UNIQUE_USEFUL — 3

- `feature/revive-event`: PR #358 remains open, dirty, 27 commits and 12 changed files. The event-revival lifecycle is unique, but cannot be merged wholesale.
- `feature/subscriptions-mercadopago`: no PR at the current head; 18 commits touching subscription payments, authentication and schema. Requires current-main selective recovery.
- `admincenter-security`: no PR at the current head; two commits affecting owner middleware/config. Requires security-owner review before recovery.

## High-risk second reviews — 12

Second review was applied to:

1. `feature/revive-event` — lifecycle migration.
2. `feature/subscriptions-mercadopago` — finance/auth/migration.
3. `feature/weekly-agenda-existing-events-20260910` — migration.
4. `feature/weekly-agenda-rolling-horizon-20260910` — migration.
5. `admincenter-security` — authorization boundary.
6. `architecture/rebase-fail-closed-payout-release` — payout release.
7. `audit/platform-hardening-2026-08-28` — auth and integrity migration.
8. `automation/acquisition-net-margin-20260907` — commission economics.
9. `automation/admin-fulfillment-reprocess-r11` — paid fulfillment.
10. `automation/atomic-checkout-recovery-claim-r11` — checkout concurrency.
11. `automation/billing-unify-plan-catalog` — subscription billing.
12. `automation/checkout-recovery-channel-attribution-r11` — revenue attribution.

No high-risk historical branch was merged in this run.

## Inventory progress

A fresh complete search returned 625 remote branches. W08 has now completed all `fix/*` (111), `refactor/*` (19), `feat/*` (204), and `feature/*` (70), plus this mixed-prefix batch. Excluding `main` and 41 W07-reserved `agent/*`/`w07/*` branches leaves **144 unreviewed branches** for W08.

- REVIEWED_THIS_RUN: 40
- DELETE_READY_THIS_RUN: 37
- HIGH_RISK_SECOND_REVIEWS: 12
- UNIQUE_USEFUL_THIS_RUN: 3
- NEW_BRANCHES_CREATED: 0
- REMAINING_API_SHARD: 144
- NEXT_SHARD: `automation/*` positions 15–54
