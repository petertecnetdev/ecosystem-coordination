# W08 — API physical cleanup batch I

Date: 2026-10-04 01:31 America/Sao_Paulo
Worker: W08
Repository: `petertecnetdev/api.petertecnet.com.br`

## Published metrics

- ADMINCENTER_COUNT: 2
- API_BRANCH_COUNT_BEFORE: 360
- DELETED_VERIFIED_THIS_RUN: 40
- API_BRANCH_COUNT_AFTER: 320
- NET_REDUCTION: 40
- HIGH_RISK_SECOND_REVIEWS: 27
- DELETE_READY_REMAINING: 0 (executed shard)
- UNIQUE_USEFUL: 0
- NEW_BRANCHES_CREATED: 0

## Classification and safeguards

- MAIN_ANCESTOR: 15
- PR_MERGED_MAIN: 25
- All refs exactly matched the merged PR head and had no open PR.
- W07, `agent/*`, `preserve/*`, `quality/*`, API #534 and unmerged unique deltas were excluded.
- Twenty-seven PR file sets touching routes, migrations, finance-adjacent, infrastructure or identity surfaces received second review.
- The workflow checked the expected SHA immediately before each deletion.
- No force push, `update_ref`, deploy, VPS access or new branch was used.

## Execution

- Workflow commit: `131a99081fd4175d1930c13587ffb706dcfd661f`
- Run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37177120769
- Job: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37177120769/job/111361957636
- Summary: `deleted=40 already_absent=0 changed=0 failures=0`
- Post-run enumeration: 320 branches; all selected refs absent.

## Admin Center

- Live branches: `main`, `feat/media-library-admin`.
- `main` reports `protected=false`.
- PR #1 remains KEEP while API #534 is open/non-mergeable.
- PR #2 is merged and its source remains absent.

## Deleted refs

- `fix/guest-order-tracking-transport-boundary-v2` — PR #469; `0006ef8fb42c6d960d6293484cd110cae6b5c3b5`
- `automation/fulfillment-recovery-economics-r11` — PR #449; `b35d11c15adedb2504be6fe51e016bee10b23dd6`
- `automation/fulfillment-recovery-attribution-r11` — PR #448; `e49b5b90f0369169b48860c992141806549319fc`
- `automation/fulfillment-auto-escalation-r11` — PR #447; `daae77f2d8d0b6f392630d2f243436668f6f4a71`
- `automation/fulfillment-sla-r11` — PR #445; `51f176a46542403f3e25ff7388aa2686ab27fe99`
- `automation/admin-fulfillment-reprocess-r11` — PR #443; `fac9f91951166df0d21fcd77e4f296113894c4ac`
- `automation/paid-fulfillment-health-r11` — PR #441; `fbd1f0420ec634c4b24e1c79a5656f7190a7beee`
- `automation/commerce-fulfillment-alert-r11` — PR #438; `530ee6a614a0fd11317bdb6901a791b3640ff982`
- `fix/reconcile-underfulfilled-paid-orders` — PR #436; `1860311814ff77dd9c79af6dd9b4d5aba5c08af5`
- `fix/order-context-integrity-current-main` — PR #431; `80a6637edf87b468a421345bf3ef3fa1d76ada46`
- `automation/guest-order-tracking-r1` — PR #426; `2b4bef82f380e10586ac32fa2483825a4c43711f`
- `fix/plat-recognized-revenue-dashboard` — PR #406; `4b27c108bce3ba657cdb7f89129960a84d9fc4b1`
- `automation/r14-reconciliation-app-breakdown` — PR #378; `93b54305902535efd06d556862f4c02f063ebc6e`
- `automation/recovery-rollout-economics-r11` — PR #366; `9fefebd2bf45d8ecc540fdef3112f1fe92be7f4d`
- `automation/recovery-surface-revenue-r11` — PR #335; `4d9b8192b68c524dc1e2c10c25cea8d46ae2faa7`
- `fix/app-code-invite-activation-url` — PR #320; `832e86dbe2d285296c5584b178a6c4791a69828f`
- `fix/order-modifier-context-integrity` — PR #316; `6eb3d31dc18a98f05065d02938d3a42a110c326b`
- `fix/order-removal-pricing` — PR #313; `e7e67db1b31380b3062887921485791c872a3505`
- `fix/commerce-compatibility-boundary-round13` — PR #303; `ab01ccee76e51ac9a74c824f452630e8c02dfdcc`
- `automation/recovery-realized-profit-20260909` — PR #297; `d462d864ac77a29664fbaca66a1d52c511b847e0`
- `feature/recovery-channel-min-sample` — PR #282; `1e34ff67203039a49a8b84c61351e6d5f69c4ff1`
- `automation/revenue-analytics-index-20260907` — PR #230; `edeb460e2593ab081b78f348459a8c4fb201ae27`
- `feat-acquisition-commission-margin-guard-20260906` — PR #219; `90b5fb7615ea26020ed26c224be65e0529ff36fb`
- `feat/application-admin-access-20260906` — PR #212; `20148701f01a075ba1caf6ac679d4a7e61b24e06`
- `fix/nonroot-verified-backup-deploy-20260906` — PR #213; `c7617abab1480fb0facb7f12f1fe104c273d7b79`
- `infra/database-backups-20260906` — PR #209; `56e6c02d5940c2c70d8c4329b7d03135577ca25d`
- `fix/deploy-preflight-resilience` — PR #207; `31aac45f73855e1dd728d9cd8f08ac6847e1fc3d`
- `fix/api-architecture-gate-sep05` — PR #201; `3df8a26d6b388bf27abfa696234329ebf5d37e84`
- `fix/architecture-gate-all-products-20260904` — PR #144; `b015a75cbfa7dc1da04035bbe939647e49deb9e3`
- `fix/automated-database-backups-20260904` — PR #134; `bdc17b3c1ae54c37861727284d55d1cb0e518729`
- `ops/reconcile-observability-schema-20260904-v2` — PR #133; `4ec6573dab02ad94386e70eaef4ebfa5c0cd60f0`
- `feat/cognitive-consciousness-research-core` — PR #126; `17b86fcf18964ae90895a8865f7b00eb422e70e0`
- `fix/enforce-generic-architecture-20260904` — PR #123; `8f979520f7b2e90acd79fbc52bfb86800f30abbb`
- `fix/organization-soft-delete-20260904` — PR #115; `9faa96ce43330967c401f1952a104b1fb9cde0ba`
- `feat/account-profile-documents-production` — PR #113; `32cab78c0c6b6a0400c904df4d3a713502d90d01`
- `fix/generic-commerce-orders-contract-20260903` — PR #99; `d5314d56a2949464e2373fa60b2ac6b32240344d`
- `refactor/contract-generic-database-storage-20260903` — PR #94; `5f9d3521a433e145503be9877ec1a584fcfad882`
- `refactor/finalize-generic-platform-20260903` — PR #87; `1534c0be7712bfd238ec066213a962b9ce09a67b`
- `refactor/generic-cutinapp-api-20260903` — PR #60; `6572da04d1977c26e872932421af511351ba7b05`
- `feat/commerce-availability-controls` — PR #69; `6a4f946cba6268534458dd23acdff4d964ba47ea`
