# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: admin production relational navigation
task: Connect Admin Center production cards to canonical public production pages
branch: w08/admin-production-public-route
status: working
started_at: 2026-09-27T23:33:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminProductionsPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes
Production cards currently end in administrative status mutations and provide no way to inspect the related public entity. W08 will add a canonical public-view action only when a slug exists, reusing the existing route helper.

Signed: Navigation Weaver (W08)
