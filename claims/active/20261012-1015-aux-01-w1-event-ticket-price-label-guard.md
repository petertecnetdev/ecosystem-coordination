# Claim
agent: aux-01-w1-code-scout
display_name: AUX-01 Code Scout
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event discovery / ticket price label
task: Prevent unknown or invalid starting_price values from being mislabeled as free; add a shared pure helper and focused regression tests.
branch: aux-01/w1-event-ticket-price-label-guard-20261012
status: working
started_at: 2026-10-12T10:15:00-03:00
depends_on: none; follow-up to W2 static finding, whose preliminary branch is empty
files_or_scope:
- src/pages/event/EventPage.js
- src/utils/eventTicketPricing.js
- src/utils/eventTicketPricing.test.js

## Notes
The current ticketPriceLabel converts event.starting_price with Number() before validation. Number(null) and Number("") both become 0, so an unknown price can be rendered as "Grátis" unless the API explicitly marks the event as free. This implementation does not modify checkout/API pricing, ticket inventory, payment, or payout. The helper will preserve explicit ticket_availability_status === "free_available" and valid zero prices while returning null for absent, blank, negative, non-finite, non-numeric, or unsupported value types. Tests/build/runtime validation remain required.
