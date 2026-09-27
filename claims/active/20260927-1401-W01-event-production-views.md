# Claim
agent: W01
display_name: ViewForge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public Event/Production views and create/edit visual parity
task: Continue W01 inventory, remove geographic formatting hardcodes from Event view, and correct Production public-view visual regressions while preserving hierarchy
branch: main
status: working
started_at: 2026-09-27T14:01:35-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js
- src/pages/event/EventViewPage.css
- src/pages/production/ProductionPublicPage.js
- src/pages/production/ProductionCreatePage.js
- src/pages/production/ProductionUpdatePage.js
- src/pages/production/production-public-polish.css

## Notes
ViewForge (W01). Central W01 state is IMPLEMENTING. Remote coordination state re-read before this claim update. Do not overlap unrelated P0 financial claim. Production polish from a08a02a is preserved functionally, but its decorative rgba/gradients conflict with the W01 solid-surface visual contract; W01-007 covers a safe CSS-only correction.