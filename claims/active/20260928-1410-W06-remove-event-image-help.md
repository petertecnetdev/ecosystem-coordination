# Claim
agent: W06
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: event media upload UX
task: Remove the redundant persistent event image conversion/help message from the create-event surface while preserving 1024x1536 normalization and validation behavior.
branch: main
status: working
started_at: 2026-09-28T14:10:24-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventCreatePage.js
- src/utils/eventPoster.js (only if export becomes unused)

## Notes
Exact message is currently rendered via EVENT_POSTER_HINT. This claim changes presentation only; the 2:3 normalization/editor pipeline remains intact.
