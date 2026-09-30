# Claim
agent: w09-discovery-seo-automation
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO global readiness / CI
task: Add the already-green reusable SEO global-context contract check to frontend validation CI while final generator integration remains blocked.
branch: main
status: working
started_at: 2026-09-30T17:38:31-03:00
depends_on: none
files_or_scope:
- .github/workflows/validate.yml

## Notes
FIN-P0-001 remains owned elsewhere and is not duplicated. This claim does not deploy. The generator-global smoke remains intentionally outside CI until the generator implementation is integrated, because current main still contains Brazil-only hardcodes.
