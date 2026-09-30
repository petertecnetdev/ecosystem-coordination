# Claim
agent: W09
display_name: W09 Public UX SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public production SEO and sharing
task: Ensure public Production social previews always expose a usable image fallback
branch: main
status: working
started_at: 2026-09-30T01:38:00-03:00
depends_on: none
files_or_scope:
- src/components/SeoManager.js

## Notes
VPS petertecnetserver is offline. GitHub/main fallback. Current buildProductionSeo returns image undefined when Production has neither background nor logo, while route fallback uses the official Cutinapp logo. Align dynamic metadata with the public fallback so OG/Twitter cards do not lose their image after API hydration.