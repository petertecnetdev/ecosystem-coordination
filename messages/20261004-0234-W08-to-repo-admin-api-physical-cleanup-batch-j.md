# W08 API physical cleanup — batch J

- Date: 2026-10-04
- Worker: W08
- Repository: `petertecnetdev/api.petertecnet.com.br`
- Result: VERIFIED
- API_BRANCH_COUNT_BEFORE: 320
- DELETED_VERIFIED_THIS_RUN: 40
- API_BRANCH_COUNT_AFTER: 280
- NET_REDUCTION: 40
- HIGH_RISK_SECOND_REVIEWS: 40
- DELETE_READY_REMAINING: 52
- UNIQUE_USEFUL: 0
- NEW_BRANCHES_CREATED: 0

## Safety and classification

Every source ref was the exact live head of a PR already merged into `main`; 15 were also direct `MAIN_ANCESTOR` refs and 25 were `PR_MERGED` refs with later-diverged history. All 40 were second-reviewed as high-risk because the set includes finance, payments, payouts, billing, subscriptions, checkout, routes or workflow history. Immediately before execution, every live SHA matched the claimed SHA and none was an open PR head. The workflow refused deletion on any SHA change.

## Admin Center

- ADMINCENTER_COUNT: 2 (`main`, `feat/media-library-admin`)
- PR #2: merged; source branch remains absent.
- PR #1: KEEP; source branch present while API #534 remains open and non-mergeable.
- `main` currently reports `protected=false`; this remains a governance risk and no protection setting was mutated.

## Evidence

- Workflow run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37180203644
- Commit: https://github.com/petertecnetdev/api.petertecnet.com.br/commit/7592d386a66a1823a73f6a0c68a6e7ed2b2a1140
- Job: delete-verified-w08-batch-j
- Log summary: `deleted=40 already_absent=0 changed=0 failures=0`
- Independent enumeration: 320 branches before, 280 after; all 40 selected refs absent.

## Deleted refs

- PR #484 — `architecture/rebase-fail-closed-payout-release` — `d82c229e42984aca9a25eb6e9e5d0badd6401b06`
- PR #482 — `feat/asaas-payouts-complete` — `df5f2e6c1a3a34b74f4baa47857c456d3798844d`
- PR #468 — `automation/billing-unify-plan-catalog` — `43f1a6c2020a94026f617c735e511aa8fafb8858`
- PR #467 — `fix/allow-sales-before-payout-setup` — `87cddac96870500c81d241b26931df205b6ce641`
- PR #466 — `fix/billing-active-window` — `8077fae86b72fb93c8b28d83582e0868be5bab2c`
- PR #464 — `fix/billing-transport-boundary` — `dba1fc5a1a529c7219fc1f852580e9ca99299ff3`
- PR #463 — `feat/billing-context-api` — `00e8eb7b63c49cbcd4c7dae58090e4a04ce3edfb`
- PR #462 — `feat/billing-entitlement-resolution` — `b9367e364b898eb5f41d744335fd5f0c6d7cd09e`
- PR #458 — `fix/commerce-retry-terminal-status` — `ca76dfe914fbfdbc386b1dd879bd7c11acc6cb13`
- PR #459 — `automation/fix-mercadopago-retry-tests` — `d794e8545a2c0aa07d00c2df0379a20f9354f895`
- PR #455 — `automation/entitlement-expiry-revenue` — `cc098b3e240c30a5e1383450da6e5e1c3c4b60f4`
- PR #457 — `automation/pix-postcopy-funnel-r11` — `3af4e5119778e631c25e92f564deba924dab807d`
- PR #456 — `automation/fix-subscription-checkout-route-r11` — `a91e9815950b2341d205c566e1ecde69789d048b`
- PR #453 — `fix/subscription-pix-retry` — `4a3ee413877694bebda6c4698d767884dd1fd6e3`
- PR #451 — `automation/event-to-payment-funnel-r11` — `494bac2adeaf82edf10d245fd8a64c7c97aa408f`
- PR #446 — `automation/mercadopago-408-425-retry-r12` — `3f895558dbabae102997f81565f0c3e05d534a38`
- PR #442 — `automation/commerce-checkout-idempotency-r12` — `f55926fd8414431d5b06a2ca45cbab1b66c047d6`
- PR #440 — `automation/commerce-pix-failure-release-stock-r10` — `1e346dd748b244b1d8a9f3d1c6175601ddf2416f`
- PR #439 — `automation/plat-guest-pix-api-r9` — `fa5662094454aae668db396c013c34b12be83789`
- PR #435 — `automation/pix-init-recovery-economics-r11` — `a8b927317db89fd9e7bcdacf9ba49e8d40d0f613`
- PR #434 — `automation/commerce-payment-resume-r11` — `f052271c7c426ebeb5e2e220744508148e98d7ec`
- PR #433 — `automation/payment-retry-after-r11` — `482138fe2494e05a6fd83d263f34f10bd2f85c4b`
- PR #432 — `automation/plat-payment-retry-r12` — `f3295aa5cb4b3ee79d427f20bfe2ef27361ffd53`
- PR #424 — `automation/plat-guest-checkout-r6` — `606fb93c7cf53cce9fd03c5cc51a33d6a10d3e7f`
- PR #423 — `automation/rasoio-renewal-final-reminder-r7` — `a7e9bb70d4a17d3fee61ac43fe22217f8c2abf2e`
- PR #422 — `automation/paid-publish-readiness-r12` — `dcda57731ea7b7e960f45be418e2f40d716f8f8f`
- PR #421 — `automation/event-payment-readiness-r11` — `927ed85bcbfbc0df75ce9bd5ce2a480538e5ad50`
- PR #418 — `automation/subscription-preexpiry-reminder-r12` — `9609d6307d89503c8cd30a18be9ec8f20fd3509a`
- PR #416 — `fix/revenue-preserve-paid-renewal-days` — `2c9a5c64feee2c9e1b366009bff9e779581e4d1f`
- PR #415 — `automation/subscription-renewal-grace-r11` — `cb398b77de230b0fd5e330d332e8083b8b9e9970`
- PR #414 — `fix/revenue-subscription-renewal-recovery-20260913` — `0c2323ed17ae18ff568e2cfacab7ec888e7e2085`
- PR #413 — `fix/revenue-subscription-recovery-claim` — `b60bc1c691b4a54e09c04005159d915929e2f3de`
- PR #412 — `automation/checkout-recovery-channel-attribution-r11` — `d22c2c42855bac5592d560c91a6bf78609452f6b`
- PR #411 — `automation/subscription-recovery-cta-r6` — `0bb7aae789dda44d39cb1dc86b406e87780478c6`
- PR #410 — `automation/atomic-checkout-recovery-claim-r11` — `44fcfa9ba9bbfe653fc7c1417b989ca889c6db4c`
- PR #408 — `fix/revenue-external-pix-recovery` — `79066a85908941044e263bf16512a6cfaf7b376c`
- PR #405 — `automation/payout-identity-safety-r11` — `fe15cd0cac0bf2ce06983e7e37b1c82ed37daa78`
- PR #404 — `automation/recovery-cohort-confidence-r12` — `c1baec1d64d13735acad89c583456ef4ba9e6876`
- PR #403 — `automation/checkout-recovery-cohort-r11` — `17903284883f25154011adfbd7744b56f9983118`
- PR #402 — `automation/recovery-journey-economics-r11` — `bbe1f64e3bd6ada10794d7449e546ff2b250c8a7`


## Requests

1. Repository admin should enforce protection/ruleset on Admin Center `main`.
2. W08 can continue with the remaining 52 exact merged refs in a non-overlapping shard.
