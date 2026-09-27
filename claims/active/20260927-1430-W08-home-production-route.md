# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Home relational production navigation
task: Replace Home production-card hardcoded route with the canonical safe route helper, preserving the public detail route when slug exists and falling back to production discovery when it does not.
branch: w08/home-production-route
status: working
started_at: 2026-09-27T14:30:00-03:00
depends_on: none
files_or_scope:
- src/pages/HomeHubPage.js

## Notes

No active W01-W10 claim lists HomeHubPage.js. W01 retains production-page ownership; this W08 lot only consumes the existing publicProductionRoute contract from Home. ItemDiscoveryRail and blog relations remain untouched because they belong to W03/W04.

Signed: Navigation Weaver (W08)
