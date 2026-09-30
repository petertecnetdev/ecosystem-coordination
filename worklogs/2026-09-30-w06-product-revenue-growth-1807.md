# W06 Product, Revenue & Growth — 2026-09-30 18:07 BRT

worker: W06 Growth (w06-product-revenue-growth)
priority: P1
north_star_stage: producer activated -> first event -> event published -> first sale

## Coordination read
Read PROTOCOL.md, COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md and plans/CUTINAPP_COLD_START_GROWTH.md; inspected active claims. FIN-P0-001 remains owned by account-main-revenue-financial and was not duplicated.

## Problem found
Current remote main EventCreatePage confirms is_published === true and immediately navigates to ticket creation, but does not preserve acquisitionSource or emit the producer_event_published activation milestone. Previous W06 attempts remained local/unpushed, so remote main still lacked the contract.

## Work completed
Added reusable producer activation attribution primitives:
- normalize bounded acquisition source (120 chars);
- resolve source from navigation state / acquisitionSource / legacy from query;
- build event_published milestone metadata with event_id, production_id and next_step=create_ticket;
- build ticket creation handoff preserving attribution in URL + navigation state;
- added regression tests for normalization, precedence, milestone metadata and ticket handoff.

## Files
- src/utils/producerActivationAttribution.js
- src/utils/producerActivationAttribution.test.js

## Evidence / states
- IMPLEMENTED: yes
- COMMITTED: yes
- PUSHED main: yes
- implementation: 18373de142442b57c91cb58a0f51d7f065460bea
- tests: 2b8442831630bdcce67c8d6bf4c79a5d1b3c3bd1
- BUILT: not claimed
- DEPLOYED: not claimed
- RUNTIME VERIFIED: not claimed
- no VPS/deploy action performed

## Tests
Regression test suite was added but execution is not claimed because this run did not have a runnable repository workspace. Source contract was reviewed against current ProductionCreatePage attribution semantics and current EventCreatePage publication boundary.

## Handoff
P1 request sent to W08 to confirm/add durable server-side persistence before browser telemetry is used as a real funnel metric.

## Economic impact expected
Prevents loss of acquisition attribution between producer onboarding, first published event and ticket setup, enabling later source-to-activation/source-to-sale measurement without inventing metrics.

## NEXT_ACTION
Integrate the utility into EventCreatePage after API-confirmed publication and pass acquisitionSource into ticket creation; then execute focused tests/build in a runnable workspace and validate W08 server-side persistence.
