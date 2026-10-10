# AUX-01 W1 — Public item promotion price parity
Date: 2026-10-10
Priority: P1
Repository main: 337c9ba22a4b97f9bd8d48f09b695105a954f43f
Branch: aux-01/w1-item-catalog-promotion-price-parity
Status: BLOCKED pending PR/CI

## Finding
Static review found that `EventItemViewPage.js` honors `promotion_enabled` and `promotion_price`, but `EventItemCatalogPage.js` rendered `item.price` and computed the selected total from that regular price. For items with an active promotion, catalog display, estimated total and `event_item_catalog_checkout_started` amount could disagree with the item detail page.

## Work completed
- Added shared helper `src/utils/eventItemPricing.js`.
- Updated the public item catalog to display an effective promotional price, show the regular price struck through when discounted, and compute its client-side total from the displayed price.
- Updated the public item detail page to use the shared pricing rules.
- Added `src/utils/eventItemPricing.test.js` covering active promotion, disabled promotion, zero-price promotion and negative promotion-price fallback.
- Kept final checkout price authoritative in the API; no payment or inventory logic changed.

## Evidence
- Base main SHA: `337c9ba22a4b97f9bd8d48f09b695105a954f43f`.
- Branch compare: 8 commits ahead, 0 behind; 4 files changed.
- Last test-file commit: `360cc76caca8fa76c4ef64ba86b074fe43c97a0f`.
- Files: `src/pages/event/EventItemCatalogPage.js`, `src/pages/event/EventItemViewPage.js`, `src/utils/eventItemPricing.js`, `src/utils/eventItemPricing.test.js`.
- No matching active claim for the item catalog pricing scope was found.
- Pull request creation was blocked by the GitHub connector safety layer; no PR exists.
- GitHub Actions query for this branch returned zero workflow runs. Tests/build were not executed in this session.
- No deploy, VPS operation, git pull, merge, force push, or destructive product change.

## Next action
W00 or an authorized GitHub write path should open a draft PR from the branch, run `CI`, `npm test -- --watchAll=false --runInBand src/utils/eventItemPricing.test.js` and `npm run build`, then review the pricing display in the mobile catalog and detail page. Do not merge until checks pass.
