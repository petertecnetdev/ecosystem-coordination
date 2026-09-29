# Claim
agent: W09
display_name: Public Conversion SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public production SEO / structured data
task: Harden public Production ProfilePage/Organization identity URLs and global location metadata
branch: main
status: working
started_at: 2026-09-29T19:43:45-03:00
depends_on: none
files_or_scope:
- src/components/SeoManager.js

## Notes
VPS petertecnetserver is offline, so Git fallback is active. Current Production SEO emits website_url directly into Organization.url and location fallback only considers city/uf. Scope is limited to metadata/structured data and does not touch route-specific visual layout.
