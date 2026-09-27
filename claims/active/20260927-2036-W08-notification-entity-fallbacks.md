# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Notification entity navigation
task: Provide canonical discovery fallbacks for notifications whose entity reference URL is absent or invalid.
branch: w08/notification-entity-fallbacks
status: working
started_at: 2026-09-27T20:36:00-03:00
depends_on: none
files_or_scope:
- src/pages/NotificationsPage.js
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js

## Notes

No active W01-W10 claim includes NotificationsPage.js or this fallback contract. Safe valid internal/external reference URLs remain unchanged; only missing/invalid references for known entity types receive a legitimate in-app fallback.

Signed: Navigation Weaver (W08)
