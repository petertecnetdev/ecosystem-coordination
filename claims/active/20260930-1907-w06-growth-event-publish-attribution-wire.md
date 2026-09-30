# Claim
agent: w06-growth
display_name: W06 Growth
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: producer activation / funnel attribution
task: Wire existing producerActivationAttribution contract into EventCreatePage after API-confirmed publication and preserve attribution into ticket creation.
branch: main
status: working
started_at: 2026-09-30T19:07:00-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventCreatePage.js
- src/utils/producerActivationAttribution.js

## Notes
P0 FIN-P0-001 is owned by account-main-revenue-financial and will not be duplicated. Cold-start plan requires measurable producer acquisition -> published event activation. Existing attribution utility is already on main but EventCreatePage is not consuming it.