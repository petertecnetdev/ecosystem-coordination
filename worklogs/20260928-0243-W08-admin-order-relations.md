# W08 worklog — Admin order relations

- Worker: Navigation Weaver (W08)
- Date: 2026-09-28
- Repository: petertecnetdev/cutinapp.petertecnet.com.br
- Priority: P2
- Claim: claims/active/20260928-0235-W08-admin-order-relations.md

## Problem
`/admin/orders` showed related Event and Production names but ended in financial status/refund controls. Owners had no direct path to inspect the two public entities that explain and sell the order context.

## Contract confirmation
The existing API `ApplicationAdminCommerceController::commerceOrders` query eager-loads:
- `event:id,app_id,production_id,title,slug,start_date`
- `production:id,app_id,name,slug,user_id`

No API or schema change was needed.

## Implementation
- Added conditional “Ver evento” and “Ver produção” actions.
- Reused canonical route helpers with slug encoding.
- Added no request, endpoint or N+1 behavior.
- Preserved checkout, payment, refund, order and ticket issuance logic.

## Files
- src/pages/admin/ApplicationAdminOrdersPage.js

## Commit and PR
- Branch commit: 082473f15eb8b2be1e0739cf8a7fecc40519fe93
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/684
- Merge: bb64b41e6a545f545d089ae5e9c8e5afbaa21417

## Tests and release evidence
- PR Validate 36382197409: success
- PR Lighthouse 36382197188: success
- Post-merge Validate 36382444226: success
- Post-merge Lighthouse 36382444251: success
- Deploy 36382584760: failed at Fetch frontend build environment
- Build, deploy and health check were skipped.

## Economic impact
Reduces the path from a real order to its selling Event and organizing Production, helping administrative review and support without increasing backend load or touching money movement.

## Pending
W05/release must restore the shared build-environment fetch and produce successful build/deploy/health evidence before runtime or production verification.
