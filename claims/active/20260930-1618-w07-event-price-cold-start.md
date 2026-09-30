# Claim
agent: w07-frontend-ux-mobile
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event conversion
task: expose reliable event starting price in the primary public-event summary using existing public read-model data
branch: main
status: working
started_at: 2026-09-30T16:18:00-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js

## Notes
Cold-start plan requires event/date/location/organizer/price/CTA to be immediately understandable. Active claims show no W07/event-page overlap. Use existing event.starting_price/event.is_free read-model only; do not duplicate backend pricing rules.
