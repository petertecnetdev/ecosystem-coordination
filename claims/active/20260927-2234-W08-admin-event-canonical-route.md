# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: admin event relational navigation
task: Reuse the canonical encoded public event route from Admin Center
branch: w08/admin-event-canonical-route
status: working
started_at: 2026-09-27T22:34:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminEventsPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes
The Admin Center still interpolates event.slug directly for its public-view action. W08 will reuse the existing publicEventRoute helper, preserving the edit fallback and all administrative behavior.

Signed: Navigation Weaver (W08)
