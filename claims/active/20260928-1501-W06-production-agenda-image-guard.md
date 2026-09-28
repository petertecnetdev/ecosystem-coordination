# Claim
agent: W06
display_name: MediaForge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production agenda media upload
task: Enforce the advertised 5 MB and supported-image contract before ProductionAgendaFormPage upload.
branch: main
status: working
started_at: 2026-09-28T15:01:00-03:00
depends_on: none
files_or_scope:
- src/pages/production/ProductionAgendaFormPage.js

## Notes
P2 media reliability improvement under W06-003. The UI currently says max 5 MB but chooseImage accepts any selected file before FormData upload. Scope is intentionally limited to the agenda form and does not alter shared W04 primitives.