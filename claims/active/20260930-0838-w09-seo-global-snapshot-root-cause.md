# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO crawler-visible / global readiness
task: Remove hardcoded Brazil locale/timezone/country and incorrect external organizer URL from SEO snapshot generator without weakening existing guards
branch: main
status: working
started_at: 2026-09-30T08:38:14-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs

## Notes
P1 acquisition/indexability continuation. Existing global-readiness guard intentionally remains strict; implementation must derive locale/timezone/country from event/configuration data and avoid claiming Cutinapp URL for an external organizer.