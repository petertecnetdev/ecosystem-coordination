# W08 API physical branch cleanup — batch D

Date: 2026-10-03 20:36 America/Sao_Paulo  
Worker: Navigation Weaver (W08)  
Repository: petertecnetdev/api.petertecnet.com.br  
Workflow commit: `b8efde74d46582fe306dfea9ffe4a5d8ba2c56e0`  
Workflow run: https://github.com/petertecnetdev/api.petertecnet.com.br/actions/runs/37162284321

## Live results

- ADMINCENTER_COUNT: 2
- API_BRANCH_COUNT_BEFORE: 540
- DELETED_VERIFIED_THIS_RUN: 40
- API_BRANCH_COUNT_AFTER: 500
- NET_REDUCTION: 40
- HIGH_RISK_SECOND_REVIEWS: 22
- DELETE_READY_REMAINING: 0 in this executed shard
- UNIQUE_USEFUL: 0 in this executed shard
- NEW_BRANCHES_CREATED: 0

## Admin Center status

- Live refs: `main`, `feat/media-library-admin`.
- PR #2 source remains absent.
- PR #1 remains KEEP/BLOCKED; both Admin PR #1 and API #534 are open and non-mergeable.
- GitHub branch inventory currently reports `protected: false` for Admin Center `main`; protection remediation remains required.

## Safety controls

- Excluded `agent/*`, `w07/*`, every UNIQUE_USEFUL ref and unrelated active implementation claims.
- Every branch was freshly compared with current main.
- The workflow pinned the exact observed head SHA and refused deletion on any change.
- Run result: `deleted=40 already_absent=0 changed=0 failures=0`.
- No force-push, reset, update_ref deletion, deploy, VPS action or new branch.

## Classification

- MAIN_ANCESTOR: 13
- PR_MERGED_MAIN: 22
- SUPERSEDED_FAMILY/HISTORICAL: 5
- UNIQUE_USEFUL: 0

## Deleted refs

| Branch | Verified pre-delete head | Basis | High-risk second review | Post-run |
|---|---|---|---:|---|
| `feat/generic-pix-beneficiary-payouts` | `c86b2eb8c9ea0f9a22fb1ad150324378e84c9ce6` | PR_MERGED_MAIN | yes | absent |
| `feat/generic-service-scheduling` | `ebfea609cc94d86d9e13ec507c26a5de8368acf1` | SUPERSEDED_FAMILY/HISTORICAL | yes | absent |
| `feat/generic-subscription-foundation` | `28b5d97ceb69f3ab9c599d07abfdf86fc914105e` | PR_MERGED_MAIN | yes | absent |
| `feat/generic-subscription-intents` | `19873ea8f012fd3061333a3703e823d9c3ee190a` | PR_MERGED_MAIN | yes | absent |
| `feat/google-place-picker` | `0341315af6982600a81ec6778f7704e9c6ab4a96` | SUPERSEDED_FAMILY/HISTORICAL | yes | absent |
| `feat/identity-platform-20260903` | `a0bcf72be3a8aa52664d5c2b3fd572ca21167ef4` | MAIN_ANCESTOR | no | absent |
| `feat/issue-645-flyer-description-api` | `8607423828e11625d55979c4c71924ecb0ee0d1d` | PR_MERGED_MAIN | no | absent |
| `feat/item-discovery-view` | `a62a750bde3b98c81310d21cd4d75c9ee46482b1` | PR_MERGED_MAIN | yes | absent |
| `feat/kryvion-airdrops` | `a060d6c44e83b36bd5be95de88e2725d6cc6ec18` | PR_MERGED_MAIN | no | absent |
| `feat/leasing-lifecycle-intelligence` | `78ab3bbd0fa125fb4c50916f0f6e332308f981d9` | SUPERSEDED_FAMILY/HISTORICAL | yes | absent |
| `feat/leasing-lifecycle-intelligence-v2` | `4cd858bee9daa7dd88692554cc396070ad29b54a` | SUPERSEDED_FAMILY/HISTORICAL | yes | absent |
| `feat/leasing-lifecycle-production` | `dab49c89c877ffd5d2bac195f1cf1d437d501a03` | PR_MERGED_MAIN | yes | absent |
| `feat/lifecycle-write-breaker` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/mission-control-observability-v2` | `ffa31248c53d90c738edc39e0cc0835032ba5193` | PR_MERGED_MAIN | yes | absent |
| `feat/nexus-discovery-v2` | `2d0d69270bd4885ff703f37f7b410683b6a6e11a` | PR_MERGED_MAIN | no | absent |
| `feat/nexus-profitability-50` | `076f339f494605108ba11f4c78d2b7cfb29be9c0` | MAIN_ANCESTOR | no | absent |
| `feat/payflow-domain` | `23f60ff369015d3a46d7523a36316933470da1a9` | SUPERSEDED_FAMILY/HISTORICAL | yes | absent |
| `feat/stop-branch-loop` | `bc47336e16e5a2fff581e0a5df5ccf6d8fd44abc` | MAIN_ANCESTOR | no | absent |
| `feat/user-profile-background-20260905` | `fcd489319e19636dd72abd2f37d451b4d7731e2f` | MAIN_ANCESTOR | no | absent |
| `feature/admin-copilot-v2` | `f53b6b4244df0811c280e60de6ad66eeb8f16c30` | MAIN_ANCESTOR | no | absent |
| `feature/admin-user-communications-20260906` | `721217ecf8b62c5115df10f5feba1cfd18d71154` | MAIN_ANCESTOR | no | absent |
| `feature/admin-user-communications-mainready-20260906` | `6036c311741d42a8486821f9ec10db938808176d` | MAIN_ANCESTOR | no | absent |
| `feature/commerce-coupons` | `d005bb65074532e77f46d4f6c28ab2a1dec9edbe` | MAIN_ANCESTOR | no | absent |
| `feature/creative-director-v2` | `be6c85bf6d0666d3966de09970b4d593307f86df` | MAIN_ANCESTOR | no | absent |
| `feature/cutinapp-participant-social-v2` | `42ac94bc6892fced657673932ebabe5a7ee9678f` | MAIN_ANCESTOR | no | absent |
| `feature/cutinapp-payments` | `9cf16089fbafb85c613dd3e4f319417650981c4b` | MAIN_ANCESTOR | no | absent |
| `feature/direct-instagram-level-20260911` | `94613c2574c083b41d3f96daf21912527cfe8a6e` | MAIN_ANCESTOR | no | absent |
| `feat/sellable-free-ticket-signals` | `d77d364b4a5c033bf145e6c45c3d495f56caedfb` | PR_MERGED_MAIN | no | absent |
| `feat/subscription-intents-profitability` | `6e150f66062d7b98cb89021ff0dca7c74d166f7d` | PR_MERGED_MAIN | yes | absent |
| `feat/subscription-pix-lifecycle` | `83780b2c14416e628ac69e009e7a589b0a171639` | PR_MERGED_MAIN | yes | absent |
| `feat/subscription-plan-entitlements` | `f285475eecafd4adb15a66f5b51599fcdb793b8e` | PR_MERGED_MAIN | yes | absent |
| `feat/ticket-multi-event-20260908` | `61f144e7202efee12f69a376a20accf67549dfc1` | PR_MERGED_MAIN | no | absent |
| `feat/ticket-sales-cutoff-rule-20260908` | `457a5e8e770442f447d8e32a5400dc1534749742` | PR_MERGED_MAIN | yes | absent |
| `feat/weekly-agenda-event-picker` | `74933a15ff55add7294ac3693bda43d887b6bf22` | PR_MERGED_MAIN | yes | absent |
| `feat/weekly-event-agenda-20260905` | `05b13ef54f850d191fa8a15c70d51a095d7998d7` | PR_MERGED_MAIN | yes | absent |
| `feature/acquisition-agent` | `3a7bd320681743972784b701147a0c6ec7249787` | PR_MERGED_MAIN | yes | absent |
| `feature/admin-financial-control-center` | `5ce6969c79fe588602e6992609647d5804ef3e7d` | PR_MERGED_MAIN | yes | absent |
| `feature/application-branding-manager-20260903` | `2572f0acea85f41a3ce28da6ae52079eef452f8c` | PR_MERGED_MAIN | yes | absent |
| `feature/application-runtime-controls-20260911` | `90c5fb544f438dc543419c585b26941c165877da` | PR_MERGED_MAIN | yes | absent |
| `feature/cutinapp-admin-impersonation` | `6302deb293515039bd69faca04882922b9fdca64` | PR_MERGED_MAIN | yes | absent |
