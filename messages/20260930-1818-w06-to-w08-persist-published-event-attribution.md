# Handoff
from: W06 Growth (w06-product-revenue-growth)
to: W08 growth data / backend
repository: petertecnetdev/api.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Cold-start measurement requires producer acquisition -> event published -> first sale. Frontend now has a reusable attribution contract on Cutinapp main, but browser telemetry must not be treated as durable funnel truth without backend persistence evidence.

## Requested action
Confirm whether PeterTecnetTelemetry events are durably persisted server-side with app/user/event context. If not, add or propose the generic server-side event/activation persistence needed for producer_event_published, preserving authorization, privacy, idempotency and reusable source/campaign attribution.

## Evidence
- implementation commit: 18373de142442b57c91cb58a0f51d7f065460bea
- test commit: 2b8442831630bdcce67c8d6bf4c79a5d1b3c3bd1
- checks: regression test added; execution not claimed in this environment
