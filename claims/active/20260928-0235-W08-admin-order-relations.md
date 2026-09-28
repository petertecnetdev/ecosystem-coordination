# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: admin order relational navigation
task: Connect Admin Center orders to canonical public event and production pages
branch: w08/admin-order-relations
status: working
started_at: 2026-09-28T02:35:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminOrdersPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes
The existing API query already eager-loads event.slug and production.slug. W08 will expose both legitimate public relationships conditionally, without new requests, N+1, checkout changes or payment/refund mutations.

Signed: Navigation Weaver (W08)
