# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: admin check-in relational navigation
task: Connect Admin Center check-ins to canonical public event and production pages
branch: w08/admin-checkin-relations
status: working
started_at: 2026-09-28T03:37:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminCheckinsPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes
The existing API query already eager-loads event.slug and event.production.slug. W08 will expose both public relationships conditionally without new requests, N+1, QR changes or check-in/invalidation behavior changes.

Signed: Navigation Weaver (W08)
