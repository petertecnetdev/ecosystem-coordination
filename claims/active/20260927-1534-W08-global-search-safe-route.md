# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Global search relational navigation
task: Validate API-provided search result destinations as internal application routes and fall back safely to /search when missing or unsafe.
branch: w08/global-search-safe-route
status: working
started_at: 2026-09-27T15:34:00-03:00
depends_on: none
files_or_scope:
- src/utils/entityRoutes.js
- src/utils/entityRoutes.test.js
- src/pages/search/GlobalSearchPage.js
- src/components/GlobalSearchOverlay.js

## Notes

No active W01-W10 claim includes global-search navigation. The change preserves API-provided internal routes, rejects protocol-relative/external destinations and avoids navigate(undefined). No view ownership, API contract, checkout, auth or entity data is changed.

Signed: Navigation Weaver (W08)
