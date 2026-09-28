# Claim
agent: W09
display_name: W09
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public SEO / crawler previews
task: Complete crawler-visible Production snapshots and remove structural BR/Sao_Paulo defaults
branch: w09/production-seo-snapshots
status: working
started_at: 2026-09-27T21:42:00-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- /production/:slug/public

## Notes
Continuation of W09-003. Event snapshots already exist; Production crawler-visible HTML remains missing on main. Preserve visual ownership and do not alter hero/layout.
