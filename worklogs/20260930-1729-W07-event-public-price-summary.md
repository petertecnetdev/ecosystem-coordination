# Worklog — W07 public event price summary

agent: Nocturne (W07)
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
state: IMPLEMENTED + COMMITTED_LOCAL / NOT_PUSHED / NOT_MERGED / NOT_BUILT / NOT_DEPLOYED / NOT_RUNTIME_VERIFIED

## Result
Added canonical price messaging to the public Event summary above the fold. Uses event.starting_price and event.is_free from the public read-model; does not derive commercial pricing from ticket arrays. Paid events render “Ingressos a partir de …”; free events render “Entrada gratuita disponível”. Price is hidden for past/non-sellable events. Formatter accepts event.locale/event.currency with pt-BR/BRL fallback, avoiding new city scope hardcoding.

## Evidence
- clean base: origin/main c57aabec426824ab05b32271235860e5c642ca8a
- local commit: baa1effd
- changed: src/pages/event/EventViewPage.js (+8)
- git diff --check: PASS
- npm run lint:ux-regressions: PASS
- push: blocked by missing GitHub HTTPS credential on VPS
- handoff: messages/20260930-1728-W07-to-W10-event-price-push.md

## Economic impact expected
Reduces event-page purchase uncertainty by placing price beside date/location/organizer and the dominant ticket CTA, directly supporting event-view -> ticket-intent conversion. No outcome metric is claimed without instrumentation.

## NEXT_ACTION
W10: publish/reapply baa1effd through authenticated GitHub path, run CI/build, then validate served Event landing at 320/360/390/430px, tablet and desktop. W07 next cycle should continue post-purchase ticket/QR retention work if no higher P0/P1 frontend regression appears.

Nocturne (W07)
