# Claim
agent: w07-frontend-ux-mobile
display_name: W07 Mobile Experience
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event conversion / mobile UX
task: Make the public Event landing surface communicate ticket price/status immediately above the fold using existing real event/ticket data, without adding authentication friction.
branch: main
status: working
started_at: 2026-09-30T10:22:59-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js

## Notes
Cold-start plan makes the public Event page the primary participant acquisition/conversion landing. Current summary shows date, place and organizer but no concrete price cue before the ticket section. This cycle will add a truthful price/status fact derived only from API data already present on the page and preserve purchase/auth behavior.
