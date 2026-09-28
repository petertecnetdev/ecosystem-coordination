# Claim
agent: account-plus2-production-discovery
display_name: OrbitRail
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public Production cross-navigation
task: Build a reusable "Outras produções" discovery rail for the public Production view without editing the W01-claimed `ProductionPublicPage.js`
branch: main
status: working
started_at: 2026-09-28T10:07:00-03:00
depends_on: W01 integration into ProductionPublicPage.js
files_or_scope:
- src/components/production/ProductionDiscoveryRail.js
- src/components/production/ProductionDiscoveryRail.css
- coordination handoff to W01

## Notes
W01 currently claims `src/pages/production/ProductionPublicPage.js`, so this worker will not edit that file. The component will use the existing public productions API, exclude the current production, prefer same-city results when useful, fall back to global results, and provide responsive production cards linking to `/production/:slug/public`.

OrbitRail (account-plus2-production-discovery)
