# Claim
agent: cutinapp-visual-w09
display_name: W09 Public UX SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public SEO / internationalization
task: Make route SEO locale derive from document/config instead of forcing pt_BR
branch: main
status: working
started_at: 2026-09-27T17:41:00-03:00
depends_on: none
files_or_scope:
- src/components/SeoHead.js

## Notes
W09-002. Preserve current pt-BR fallback while removing the hardcoded Open Graph locale from the reusable SEO component. No layout/shared visual changes.
