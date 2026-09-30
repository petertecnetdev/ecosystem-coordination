# W07 Worklog — Public Event price above fold

agent: W07
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
state: IMPLEMENTED_LOCAL / COMMITTED_LOCAL / NOT_PUSHED

## Outcome
Implemented the cold-start requirement that a visitor can understand ticket price in the public Event summary before scrolling into the cart. Reused `data.tickets` from the existing public event payload; no extra request and no independent pricing endpoint were introduced.

Behavior:
- ignore tickets explicitly unavailable, expired or with zero remaining stock;
- if any sellable ticket is free, show `Entrada gratuita disponível`;
- otherwise show the minimum valid positive price as `Ingressos a partir de ...`;
- do not show price summary for past events.

## Evidence
- local commit: `eba49be`
- changed: `src/pages/event/EventViewPage.js` (+14/-1)
- `git diff --check`: PASS
- `node scripts/check-ux-regressions.js`: PASS
- `node scripts/check-react-stability.js`: baseline-blocked by unrelated improved debt in `ProductionCreatePage.js`; no EventViewPage finding
- push: FAILED because the clean VPS clone has no GitHub credentials

## Economic impact expected
Reduces a major information gap for WhatsApp/Instagram/Google visitors by exposing real ticket pricing beside title/date/location/organizer and the ticket CTA, reducing exploratory scrolling before purchase intent.

## NEXT_ACTION
Publish `eba49be` through an authenticated GitHub path without overwriting newer main work; then CI/build and functional validation at 320/360/390/430 and tablet/desktop. After publication, close the active claim with remote SHA evidence.
