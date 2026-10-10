# Claim
agent: aux-01-w1-code-scout
display_name: AUX-01 Code Scout
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event item catalog pricing / conversion
task: Align promotional price display and client-side order total between item catalog and item detail using a shared pricing helper, with focused regression tests.
branch: aux-01/w1-item-catalog-promotion-price-parity
status: working
started_at: 2026-10-10T10:25:00-03:00
depends_on: none
files_or_scope:
- src/pages/event/EventItemCatalogPage.js
- src/pages/event/EventItemViewPage.js
- src/utils/eventItemPricing.js
- src/utils/eventItemPricing.test.js

## Notes
Static review found the public item detail honors promotion_enabled/promotion_price while the public item catalog displays item.price and calculates totals/telemetry from item.price. Keep the API authoritative for final checkout pricing; this change only aligns displayed prices and client-side estimates. No payment logic, backend pricing, inventory, or deployment changes.
