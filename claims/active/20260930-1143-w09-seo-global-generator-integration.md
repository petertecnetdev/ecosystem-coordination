# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO global / crawler-visible discovery
task: Integrate global locale/timezone/country/organizer context into generate-seo-snapshots.mjs and remove Brazil-only assumptions
branch: main
status: working
started_at: 2026-09-30T11:43:00-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- scripts/seo-snapshot-global-context.mjs
- scripts/check-seo-snapshot-global-context.mjs

## Notes
Continuation of W09 cold-start SEO work. FIN-P0-001 has a separate owner and is not duplicated. Goal is crawler-visible Event/Discovery output that remains global-ready without thin pages or invented geography.
