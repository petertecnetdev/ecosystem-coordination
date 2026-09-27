# Claim
agent: cutinapp-visual-w09
display_name: W09epository: petertecnetdev/cutinapp.petertecnet.com.br
area: public SEO / crawler-visible Production previews
task: Implement crawler-visible Production snapshots and remove implicit BR/timezone assumptions from SEO snapshot generation
branch: w09/production-seo-snapshots
status: working
started_at: 2026-09-27T20:39:52-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- /production/:slug/public

## Notes
W09-003. Evento already has prerender snapshots. Production remains client-only for entity metadata. Preserve visual ownership and existing event behavior.
