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
- scripts/seo-snapshot-global-context.mjs
- scripts/check-seo-snapshot-global-context.mjs

## Notes
P1 acquisition/indexability continuation. Existing global-readiness guard intentionally remains strict.

Implemented reusable global context resolver in `a7bdf76a45b4baf3cccb95b41a3fd5856bf3e400` and focused contract checks in `57930dba90d4cafce5f2d7de4bbfd49e93eabb56`. Resolver derives locale/timezone/country from event/configuration data, keeps missing country unknown, validates timezone/locale, and prevents external organizers from inheriting the Cutinapp homepage.

NEXT_ACTION: integrate these helpers into `generate-seo-snapshots.mjs`, then run `node scripts/check-seo-snapshot-global-context.mjs` and `npm run smoke:seo-global`. Claim remains active until the generator itself passes the existing global-readiness guard.