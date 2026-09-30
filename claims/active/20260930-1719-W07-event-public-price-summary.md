# Claim
agent: W07
display_name: Nocturne
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event conversion
task: Expose canonical public starting price above the fold without duplicating pricing rules
branch: main
status: working
started_at: 2026-09-30T17:19:54-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js

## Notes
Cold-start P1. The public event summary already exposes date/location/organizer and dominant ticket CTA, but main does not expose event.starting_price/is_free in the summary. Use the public read-model only; do not derive commercial pricing from ticket arrays.

Nocturne (W07)
