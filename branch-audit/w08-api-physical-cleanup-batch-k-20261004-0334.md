# W08 API physical cleanup — batch K

- Date: 2026-10-04
- Worker: W08
- Repository: `petertecnetdev/api.petertecnet.com.br`
- Result: VERIFIED
- ADMINCENTER_COUNT: 2
- API_BRANCH_COUNT_BEFORE: 280
- DELETED_VERIFIED_THIS_RUN: 40
- API_BRANCH_COUNT_AFTER: 240
- NET_REDUCTION: 40
- HIGH_RISK_SECOND_REVIEWS: 40
- DELETE_READY_REMAINING: 12
- UNIQUE_USEFUL: 0
- NEW_BRANCHES_CREATED: 0

## Safety classification

All 40 refs were exact live heads of PRs already merged into `main`. Twenty-six were also direct `MAIN_ANCESTOR` refs; fourteen were `PR_MERGED` refs whose histories later diverged. Every PR diff and merge metadata was reviewed again because the batch includes payment, checkout, webhook, authentication, finance, idempotency and ticket history. Immediately before deletion, all SHA values matched and no ref was an open PR head or in the W07 shard.

## Admin Center

- Live branches: `main`, `feat/media-library-admin`.
- PR #2 is merged and its source remains absent.
- PR #1 remains KEEP while API #534 is open and non-mergeable.
- GitHub still reports `protected=false` for `main`; no administrative setting was changed.

## Evidence

- Workflow: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37182925745
- Commit: https://github.com/petertecnetdev/api.petertecnet.com.br/commit/8ca310b4748d34a6534ea2a9ca1d2013f965f648
- Job: `delete-verified-w08-batch-k`
- Summary: `deleted=40 already_absent=0 changed=0 failures=0`
- Independent enumeration: 280 branches before, 240 after; all 40 selected refs absent.

## Deleted refs

- PR #400 — `automation/checkout-production-scope-r16` — `108191e9cc9e12003df62d91ff3c996d29ad94c4`
- PR #398 — `automation/checkout-combined-segments-r14` — `c6a7920f852ca4e59a27e000474e7f3b267ea420`
- PR #397 — `automation/checkout-device-r13` — `ee45c88756c640b12fc2906515e849e6d39cf33d`
- PR #396 — `automation/checkout-unattributed-r12` — `5198b8eb66f82fc9a91016d2c19b631cd9b966cd`
- PR #395 — `automation/plat-pix-recovery-deeplink-r21` — `ce98439c19ca8182894a68cdc9b8c400813a5942`
- PR #394 — `fix/commerce-pix-retry-service-r6` — `eee3f61152806229a1b316a66ce443b453b63742`
- PR #393 — `automation/checkout-abandonment-breakdown-r11` — `e50ac2d1350f657881653a72977c73043362ad16`
- PR #390 — `automation/checkout-abandonment-alias-r19` — `43b74047722febcf7b685e34e219547814327ee0`
- PR #388 — `automation/remove-duplicate-payment-reconcile-r18` — `c855b0cb94aa2a9a2610a9dcb8800c56aca0af71`
- PR #386 — `automation/payment-health-recovery-attribution-r16` — `a34fb140b5326b5644e4350f470b30e05ed7ad9c`
- PR #385 — `automation/payment-health-diagnosis-r15` — `a9f901d47bc45e1240a314c9d30e192a3b47b6fe`
- PR #384 — `automation/payment-health-incidents-r14` — `34c67742b5308a355eb86fba502ebc7ea886be74`
- PR #383 — `automation/payment-health-recovery-r13` — `864d0aa0097d90d5466113a9436193598373be1f`
- PR #382 — `automation/payment-health-alert-r12` — `fa8f4ca1f4058968dbb2ec49f672a1b6578d3abb`
- PR #381 — `automation/payment-health-baseline-r11` — `5816f27f6479e2d2e2b7ec3d8708db12e93845d0`
- PR #380 — `automation/payment-health-risk-r11` — `341700918f3bc1940e5b81cd3bd3027d0ca82711`
- PR #379 — `automation/payment-reconciliation-persistence-r11` — `e73c7793472a41468eab4b15cadf40dbecdb20f3`
- PR #377 — `automation/r13-reconciliation-alerts` — `9f191c1c9fe4959aeee86e6b4b9eb45698e3d0f3`
- PR #376 — `automation/payment-reconciliation-telemetry-r12` — `d66553eff02faabbe59dae99fded1ae0b183d47d`
- PR #375 — `automation/reconcile-payments-schedule` — `0a1f5097439894cf490c714cc9ea2f45c784cc3e`
- PR #374 — `automation/r11-commerce-webhook-compat-latest` — `fe808fb6d64204729e6589a453ae732eed641f07`
- PR #373 — `automation/r11-treatment-attribution` — `25f4990376f665ecc9c78a1e5ab3668fe9d493b7`
- PR #365 — `automation/checkout-action-effectiveness-r11` — `9f77a0ec062a387c2ee539a871a3c2a4419699ac`
- PR #364 — `automation/checkout-period-comparison-r11` — `f7cc41a0ea8ae886c55abd65233ac51cf44dcf97`
- PR #363 — `automation/subscription-intent-recovery-r6` — `25c52e4968a4c4f208f06c57fabd7b6400ce7150`
- PR #362 — `automation/checkout-remediation-r12` — `e814bb2ccb1e1d8be9347f1b905794c2174c7e88`
- PR #355 — `automation/checkout-stage-gmv-r10` — `82a741cf377a1213306591b943c6eeb860e9c3ea`
- PR #353 — `automation/checkout-journey-funnel-r10` — `c2a27fd5b9cd26f47fea7253db902274ffc65d04`
- PR #315 — `automation/recovery-prominence-economics-v2` — `b1f8dbb66b333c47d91b6a299d56cbbdbc0ef012`
- PR #309 — `feat/admin-password-reset` — `02f110d816a6e2c1739379b6b25173aa20270f7a`
- PR #306 — `automation/profitable-pix-recovery-cta` — `b4ed7ac7191a699f83d501c42327bda1042cc6aa`
- PR #302 — `automation/recovery-incrementality-control` — `450b4080c3a26d4e913f00549575b5d659fed13b`
- PR #295 — `automation/cutinapp-delivery-effects-20260909` — `eba56cfa090f0390de8b30fa38e515880a474909`
- PR #292 — `feat/automated-in-app-checkout-recovery` — `1d0b2acde5fb83455369b400c555a7a44e438bbd`
- PR #289 — `feat/cutinapp-owner-hardening-20260907` — `6de79250e39c74ddb2de9c234dfab2ce7806a988`
- PR #259 — `automation/recovery-performance-by-payment` — `7ad857381e2192c85dc2f2ab27ac5e43c815480d`
- PR #256 — `automation/profitability-top-recovery-opportunities` — `5fd8446d6faab0e20929ddd56765e28e4645019f`
- PR #253 — `automation/recovery-opportunity-analytics` — `e4bb02eaa43f4a1565709c6f44cd56d42bf9f0e4`
- PR #243 — `automation/profitability-financial-dashboard` — `a6a311df003a04fc5a0d5ac590776f30300e0aad`
- PR #239 — `fix/idempotency-upload-fingerprint` — `ad502ceb272647c9dfad15836f2e7980a3bf4f2e`

## Exact merged refs remaining

- PR #232 — `automation/financial-dashboard-indexes-20260907` — `eab7fd48d17024d24784f8b0f99d706cefb1ec37`
- PR #229 — `feat/admin-user-360-20260907` — `a6ba982bf413ec3f2c7169101b024294ccf73b01`
- PR #224 — `feat/analytics-settlement-profitability` — `680386b982642e266bde530d297426c669822bb4`
- PR #221 — `feat/cutinapp-admin-root-only` — `ea1314ae9dc2957285974518dd6b05940be3de0b`
- PR #215 — `fix/backup-restore-readiness-20260906` — `96d25b1438522b84174793b4d5bb1cca4ff2afc2`
- PR #208 — `feat/checkout-recovery-intent-v5-20260906` — `934af111c75925720751b0a3f887aeedd1a7bd2c`
- PR #206 — `fix/commerce-checkout-idempotency` — `a7093081984553756e8cfc53de4a8ccc7d4a495f`
- PR #160 — `feat/checkout-recovery-intent` — `6ad78250f25aa8c07171007731d73c2f6baff3f3`
- PR #159 — `feat/commerce-recovery-revenue-attribution` — `b529cf6bc4014e497cafeb2ef176b1b058ae88f3`
- PR #158 — `feat/checkout-recovery` — `13b157b19456cbc09c111d9c62642fc9ce2fa346`
- PR #142 — `feat/admin-establishment-owner-transfer-preserved-20260904` — `2fb41f9061dbd96059bbd276a47938a9edfa2f24`
- PR #139 — `feat/cutinapp-ticket-transfer-20260904` — `85d5772aa4836f1695230a391bfa57f41f34cb78`
