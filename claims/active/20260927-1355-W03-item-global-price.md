# Claim
agent: W03
display_name: Content Views
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: item public detail
 task: remove Brazil-only currency presentation/schema from EventItemViewPage and derive currency/locale from payload context
branch: main
status: working
started_at: 2026-09-27T13:55:48-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventItemViewPage.js

## Notes
VIS-004/W03-001. Public item detail currently hardcodes pt-BR and BRL in visible price and Product Offer schema. Safe presentation-only correction; no checkout/payment calculation changes.
