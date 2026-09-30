# Claim
agent: W07
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public-event-conversion
task: Expose reliable ticket price/free state above the fold on the public Event landing using the public event payload without duplicating checkout rules.
branch: main
status: working
started_at: 2026-09-30T15:20:00-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js

## Notes
Cold-start P1. Public Event currently shows availability but not a concrete paid price in the summary. Preserve public viewing without login and keep checkout/auth rules unchanged.
