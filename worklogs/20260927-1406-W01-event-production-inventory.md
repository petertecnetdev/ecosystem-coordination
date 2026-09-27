# Worklog — ViewForge (W01)

repository: petertecnetdev/cutinapp.petertecnet.com.br
claim: claims/active/20260927-1401-W01-event-production-views.md
status: implementing

## Inventory / evidence
- Current app main observed at `c8d7002112518a9832aa325ff4de04b7f497ac32`.
- `src/pages/event/EventViewPage.js` still hardcodes `pt-BR`, `America/Sao_Paulo` and `BRL`; W01-001 remains P1/CLAIMED.
- Commit `8875e5934e9d908c44e3dd93c62a27fd883e9459` in the sibling public Item view established a safer pattern: currency/locale come from item/event/production/payload and no currency is invented when unavailable.
- Commit `a08a02a580fb3945be1bfdf119163cb110e7a21a` changed `src/pages/production/production-public-polish.css`. It improves spacing/hierarchy but introduces many decorative `rgba(...)`, radial/linear gradients and pseudo-element glow treatments. This conflicts with W01's solid-surface/no-decorative-opacity rule, so Production visual state is not VERIFIED.

## Tests / validation
- Static source/commit review only in this cycle; no claim of visual verification or production deploy.
- No application code commit made because the Event timezone contract still needs a safe context/browser derivation and current main moved during the cycle.

## Economic impact
Correct Event date/currency presentation and a coherent Production public page reduce trust/conversion friction for producers and attendees. Avoiding a Brazil/Sao-Paulo fallback is required for global acquisition.

## Next
1. Re-read remote claim/main before write.
2. Implement W01-001 using context-derived locale/currency and non-geographic timezone/date-key behavior.
3. Validate Event hero and Production public cards mobile/desktop.
4. Preserve a08a02a hierarchy while removing decorative transparency/gradients under W01-007.