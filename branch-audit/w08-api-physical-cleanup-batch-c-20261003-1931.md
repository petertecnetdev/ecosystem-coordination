# W08 API physical branch cleanup — batch C

Date: 2026-10-03 19:31 America/Sao_Paulo  
Worker: Navigation Weaver (W08)  
Repository: petertecnetdev/api.petertecnet.com.br  
Workflow commit: `5d71c9dab4afa9834b2c3df424e95aa67925cf88`  
Workflow run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37158591328

## Live results

- ADMINCENTER_COUNT: 2
- API_BRANCH_COUNT_BEFORE: 599
- DELETED_VERIFIED_THIS_RUN: 40
- API_BRANCH_COUNT_AFTER: 559
- NET_REDUCTION: 40
- HIGH_RISK_SECOND_REVIEWS: 15
- DELETE_READY_REMAINING: 0 in this executed shard
- UNIQUE_USEFUL: 0 in this executed shard
- NEW_BRANCHES_CREATED: 0

## Safety controls

- Excluded `agent/*`, `w07/*`, FIN-P0-001, open unique-useful PRs, auth/finance branches without prior merged/superseded evidence, and every W07-owned shard.
- Every ref was compared with current `main`, then the workflow verified its exact expected head SHA immediately before deletion.
- The job refused deletion on any changed head.
- Run result: `deleted=40 already_absent=0 changed=0 failures=0`.
- Post-run enumeration confirmed all 40 refs absent and branch count reduced from 599 to 559.
- No force-push, update-ref deletion, deploy, VPS action, or auxiliary branch.

## Classification

- MAIN_ANCESTOR: 23
- PR_MERGED: 8
- SUPERSEDED_FAMILY/HISTORICAL: 9
- UNIQUE_USEFUL: 0

## Deleted refs

| Branch | Verified pre-delete head | Basis | High-risk second review | Post-run |
|---|---|---|---:|---|
| `feat/discovery-learning-loop-20260903` | `0fdaad7daac454ab7522414f32b06f0255385116` | SUPERSEDED_FAMILY | yes | absent |
| `feat/discovery-learning-loop-v2-20260903` | `71ae2e45e5698452e20869d84fc9bdf7c9e17a96` | PR_MERGED | yes | absent |
| `feat/document-signature-production` | `764c48cfc7d3fdecac3767ed79d74678401c10f6` | PR_MERGED | yes | absent |
| `feat/document-signature-workflow` | `dfa379c4d50daf4039a6c4887d530f93388225ad` | SUPERSEDED_FAMILY | yes | absent |
| `feat/ecosystem-support-20260905-v2` | `6b7262d26d6d44b9bdf1e6d506f919a0cb8549ee` | SUPERSEDED_FAMILY | yes | absent |
| `feat/ecosystem-support-20260905` | `84c2cc62d14fe8f0ce32de1c33f53ad31dd31182` | MAIN_ANCESTOR | no | absent |
| `feat/email-verification-deferral` | `bc770234d364df121cb739275064f7eea24b4349` | PR_MERGED | yes | absent |
| `feat/enforce-entitlement-limits` | `cf5dcd1aafdf181453121979e30c17317958d015` | PR_MERGED | yes | absent |
| `feat/event-addons-management-20260906` | `60281b6948cc20d2e15142ee7851747b82f4c1bf` | MAIN_ANCESTOR | no | absent |
| `feat/event-catalog-addons` | `8273b54fe050d60e2be89810f04cc2307375e054` | MAIN_ANCESTOR | no | absent |
| `feat/event-date-item-redemption` | `09069a16614e2ffac8f6c34c8a83882ad1e4bfac` | MAIN_ANCESTOR | no | absent |
| `feat/event-lifecycle-generic-20260903-2` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/event-lifecycle-generic-20260903` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/event-lifecycle-implementation` | `2dda1993873a16110f4bd06143f280d74974487c` | SUPERSEDED_FAMILY | yes | absent |
| `feat/event-lifecycle-implementation-2` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/event-lifecycle-implementation-3` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/event-lifecycle-working` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/event-no-show-metrics-20260905` | `11cde1a1a81effb7317dc637687c92f124e59bdb` | PR_MERGED | no | absent |
| `feat/event-share-preview-20260907` | `9fc72dc01a946770a8343b343352bdab10721da7` | SUPERSEDED_FAMILY | no | absent |
| `feat/explicit-checkout-recovery-intent` | `939486e9c6e810a1b6e40db317e5398e4b978edc` | SUPERSEDED_FAMILY | yes | absent |
| `feat/flyer-date-consistency` | `06afd697a251e26358722f6f825857022adef2cc` | PR_MERGED | yes | absent |
| `feat/generic-app-messaging` | `432b39b347a85f6ff08718bf27920aa85beb6f7b` | SUPERSEDED_FAMILY | yes | absent |
| `feat/generic-establishment-conversion-20260903` | `f93380872dfcf2a5869e97a0d18da54138a0f9b9` | SUPERSEDED_FAMILY | yes | absent |
| `feat/generic-event-lifecycle-protection` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/generic-event-lifecycle-protection-final` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/generic-event-lifecycle-protection-impl` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/generic-event-lifecycle-protection-v2` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/generic-fulfillment-lifecycle` | `b354c698bcfff44edef920d0a1f56836cea85041` | SUPERSEDED_FAMILY | yes | absent |
| `feat/generic-lease-contract-templates` | `21b22329a95e902938e8fad28f0b427f5b620429` | PR_MERGED | yes | absent |
| `feat/generic-leasing-domain` | `1b3cfa28afc6e74067475f75b0dd7590d5f4f3d8` | PR_MERGED | yes | absent |
| `feat/generic-onboarding-data-quality-v2-final` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2-impl` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2-mainwork` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2-pr` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2-pr2` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2-work` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-data-quality-v2` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-hardening-20260903` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-hardening-final2-20260903` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |
| `feat/generic-onboarding-hardening-final-20260903` | `1e09ba566bd7098419d9a8a6267eea588296bf17` | MAIN_ANCESTOR | no | absent |

## Admin Center

- Live branches: `main`, `feat/media-library-admin`.
- Merged PR #2 source remains absent.
- PR #1 remains KEEP/BLOCKED and is currently non-mergeable; API #534 is open and non-mergeable.
