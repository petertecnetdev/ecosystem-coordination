# Claim
agent: W07
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event conversion
task: Expose real ticket price summary above the fold using the existing commerce catalog without duplicating pricing rules
branch: main
status: working
started_at: 2026-09-30T13:18:00-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js
- src/components/event/EventCommercePanel.js

## Notes
Cold-start P1 conversion improvement. The public event page already shows event/date/location/organizer and CTA, but the summary does not expose a concrete catalog-derived price. Reuse the catalog already loaded by EventCommercePanel and report its sellable ticket summary upward; do not introduce a second commerce request or frontend pricing source of truth.
