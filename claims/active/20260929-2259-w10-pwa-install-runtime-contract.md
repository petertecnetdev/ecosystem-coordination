# Claim
agent: W10
display_name: Cutinapp Visual QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: PWA installability QA
task: Harden static PWA smoke against missing install-script/SW integration and unsafe start_url/scope relationships
branch: main
status: working
started_at: 2026-09-29T22:59:00-03:00
depends_on: none
files_or_scope:
- scripts/check-pwa-installability.js

## Notes
VPS petertecnetserver is offline. Git fallback. Existing smoke checks manifest fields/icons and string presence but does not validate start_url within scope or require the external install integration to be a valid HTTPS script URL with the declared SW target.