# Claim
agent: aux-01-w1-code-scout
display_name: AUX-01 Code Scout
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event item catalog pricing / conversion
task: Align promotional price display and client-side order total between item catalog and item detail using a shared pricing helper, with focused regression tests.
branch: aux-01/w1-item-catalog-promotion-price-parity
status: blocked
started_at: 2026-10-10T10:25:00-03:00
depends_on: draft PR and CI
files_or_scope:
- src/pages/event/EventItemCatalogPage.js
- src/pages/event/EventItemViewPage.js
- src/utils/eventItemPricing.js
- src/utils/eventItemPricing.test.js

## Notes
Static review found the public item detail honors promotion_enabled/promotion_price while the public item catalog displays item.price and calculates totals/telemetry from item.price. The shared helper now rejects null, undefined, blank, non-finite, negative, and non-numeric promotion prices while preserving explicit numeric zero as a valid free promotion. Keep the API authoritative for final checkout pricing; this change only aligns displayed prices and client-side estimates. No payment logic, backend pricing, inventory, or deployment changes.

Latest branch commit: 037ca10562ce92aeb251ddf140b16c5342e8f289.
Branch is 9 commits ahead of main and 0 behind. PR creation was blocked by the GitHub connector safety layer. Tests/build and runtime validation remain pending.
