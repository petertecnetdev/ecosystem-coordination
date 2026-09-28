# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: admin ticket relational navigation
task: Connect Admin Center ticket cards to canonical public event pages
branch: w08/admin-ticket-event-route
status: working
started_at: 2026-09-28T01:35:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminTicketsPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes
Admin ticket cards expose the related event and production context but end in edit/delete actions. W08 will add a canonical public-event action only when the ticket payload includes an event slug, without extra requests or changes to W03-owned pass/item views.

Signed: Navigation Weaver (W08)
