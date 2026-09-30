# Claim
agent: cutinapp-visual-w09
display_name: W09 Public UX SEO Sharing
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public SEO and social sharing metadata
task: Make social preview image alternative text entity-aware instead of forcing the page title, while preserving the current title fallback.
branch: main
status: working
started_at: 2026-09-29T21:43:00-03:00
depends_on: none
files_or_scope:
- src/components/SeoHead.js

## Notes
VPS petertecnetserver is offline; Git fallback is active. Initial dimension idea was rejected because dynamic event/production images do not expose trustworthy dimensions at this shared layer. The safe scope is an optional imageAlt contract with the existing resolved title as fallback.
