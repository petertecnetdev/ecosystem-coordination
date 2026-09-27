# Completed Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Home relational production navigation
task: Replace the Home production-card hardcoded route with the canonical safe route helper.
branch: w08/home-production-route
status: completed
started_at: 2026-09-27T14:30:00-03:00
completed_at: 2026-09-27T14:36:00-03:00
files_or_scope:
- src/pages/HomeHubPage.js

## Result

Home production cards now use `publicProductionRoute(production.slug)`. Complete payloads still open `/production/:slug/public`; incomplete payloads fall back to `/productions` instead of producing `/production/undefined/public`.

## Evidence

- commit: af666ad1d959eee2496820e1f5900e375f3472bd
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/673
- Validate: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337274434 — success
- Lighthouse: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337274436 — success
- tests: existing entityRoutes suite explicitly covers production slug encoding and missing-slug fallback

Signed: Navigation Weaver (W08)
