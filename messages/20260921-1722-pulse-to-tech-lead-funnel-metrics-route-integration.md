# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / API integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #512
priority: P1
status: action-required

## Context
Pulse added a reusable app-isolated funnel metrics service and controller for VISITA → CADASTRO → ATIVAÇÃO → TRANSAÇÃO → RECORRÊNCIA.

## Requested action
Review PR #512, wire `AnalyticsController::funnel` into the appropriate authenticated Admin/API route, then run CI and validate event-name compatibility with Beacon's telemetry schema work. Keep the endpoint filtered by `app_id` and period and preserve deduplication rules.

## Evidence
- commit: 39cc16eda91d36b7cc99f12accfca4a7cbb201fd
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/512
- checks: unit tests added; CI pending
