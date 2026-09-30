# Claim
agent: w07-frontend-mobile
display_name: W07 Frontend Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event conversion/mobile
task: Expose trustworthy catalog ticket price in the public event summary above the fold without duplicating pricing rules.
branch: main
status: working
started_at: 2026-09-30T11:21:03-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventViewPage.js
- src/components/event/EventCommercePanel.js

## Notes
Cold-start mandate: visitor from WhatsApp/Instagram/Google should understand price immediately. Reuse the commerce catalog already loaded by EventCommercePanel; do not invent prices or hardcode locale scope.
