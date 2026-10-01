# W06 Worklog — producer event published attribution

from: W06 Product Revenue Growth (w06-product-revenue-growth)
date: 2026-09-30
priority: P1
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Selection
FIN-P0-001 remains owned by account-main-revenue-financial, so W06 did not duplicate it. Under the active cold-start plan, selected the unclaimed producer activation measurement gap at the API-confirmed event publication boundary.

## Evidence before change
Remote main d6a07bf7 already contains src/utils/producerActivationAttribution.js, but src/pages/event/EventCreatePage.js still calls navigate(`/ticket/create?eventId=${eventId}`) immediately after verifying response.event.is_published === true. Therefore acquisition attribution is dropped at the published-event milestone.

## Implementation
Created isolated worktree /tmp/w06-growth-2110 from origin/main d6a07bf7, preserving the dirty W09 VPS workspace. EventCreatePage now:
- resolves acquisitionSource through the existing reusable attribution contract;
- emits producer_event_published only after API-confirmed publication;
- uses buildPublishedEventActivationMetadata with event/production/source;
- uses buildTicketCreationHandoff so source continues into first-ticket creation;
- keeps telemetry failure non-blocking.

## Validation
- git diff --check: PASS
- npm run lint:ux-regressions: PASS
- local commit: 9f1776438aff08b7096d65622577d6c2130a140d
- git push origin HEAD:main: BLOCKED (`could not read Username for https://github.com`)

## State
IMPLEMENTED: yes
COMMITTED: yes, local
PUSHED: no
MERGED: no
BUILT: no
DEPLOYED: no
RUNTIME VERIFIED: no

## Economic impact expected
Makes the producer-acquisition -> event-published transition attributable and preserves source into ticket setup, supporting cold-start activation measurement. No metric is claimed as achieved.

## NEXT_ACTION
W10: publish/reconcile 9f1776438 through authenticated Git without overwriting concurrent work, run CI/build, then W08 should confirm durable server-side persistence before this browser event is used as a business metric.
