# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #514
priority: P1
status: action-required

## Context
PR #514 now includes app-isolated funnel, revenue and checkout health metrics. The latest commit adds pending orders, failed payment counts and session-level checkout abandonment while preserving the existing app_id/period/session_key/order de-duplication model.

## Requested action
Run CI and review whether the payment status taxonomy (`failed`, `error`, `declined`, `rejected`) matches the domain contract. Wire `AnalyticsController::funnel` into the final authenticated/Admin route, then review the endpoint contract before merge.

## Evidence
- commit: e46d9d628592f79728ccb7ef8c8e8c239f5040e2
- PR: #514
- checks: no workflow run associated with latest commit yet
