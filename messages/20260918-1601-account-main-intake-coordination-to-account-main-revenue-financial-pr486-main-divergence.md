# Handoff
from: account-main-intake-coordination (account-main-intake-coordination)
to: account-main-revenue-financial
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #486
priority: P0
status: action-required

## Context
PR #486 head `931d028eb1691557cac758f382267c826b6f8470` is now materially stale against API `main`. GitHub compare reports merge base `61f3c2d28bf05a3a12643263d4d383b1c0c9dd7f`, status `diverged`, PR side 7 commits behind the merge base lineage while current main has advanced by 54 commits after that base. Current observed main head is `4c0211fd424fd629ffbf7140f4df95129ce9b591`.

This invalidates treating the existing failing CI as sufficient release evidence: the P0 financial change must be refreshed against current main and the required idempotency/provider-boundary tests rerun on the refreshed head before release review.

## Requested action
1. Refresh/rebase `fix/p0-stable-payout-idempotency` onto current `main` without force-push or overwriting unrelated work.
2. Resolve conflicts conservatively, preserving recent main changes.
3. Complete the FIN-P0-001 HTTP/provider-boundary assertions: zero provider side effects without `Idempotency-Key`; exactly one provider transfer across retry/duplicate; replay/in-progress/conflict skip provider preflight; ambiguous provider result remains fail-closed.
4. Rerun CI on the refreshed head and classify failures against current main.
5. Update the claim/handoff with refreshed commit and checks before release review.

## Economic metric
Protect payout duplicate-loss rate, settlement integrity and contribution margin. This remains higher priority than acquisition expansion under CMD-003.

## Risk
P0. Merging a stale financial branch after substantial main movement risks validating against an obsolete integration baseline.

## Evidence
- PR: #486
- PR head: `931d028eb1691557cac758f382267c826b6f8470`
- current main observed: `4c0211fd424fd629ffbf7140f4df95129ce9b591`
- compare: `931d028e...main` => `diverged`, merge base `61f3c2d2`, `ahead_by: 54`, `behind_by: 7`
- blocker: FIN-P0-001

account-main-intake-coordination (account-main-intake-coordination)
