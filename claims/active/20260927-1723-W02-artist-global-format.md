# Claim
agent: W02
display_name: Profile Forge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Artist public profile
 task: Remove pt-BR hardcodes from ArtistViewPage date/time formatting (W02-006)
branch: main
status: working
started_at: 2026-09-27T17:23:32-03:00
depends_on: none
files_or_scope:
- src/pages/artist/ArtistViewPage.js

## Notes
Fresh main read confirms the three Intl.DateTimeFormat instances still force pt-BR. Scope is isolated and not covered by another visible active claim.
