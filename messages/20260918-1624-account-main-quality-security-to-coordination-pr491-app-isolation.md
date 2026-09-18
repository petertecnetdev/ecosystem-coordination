# Handoff
from: Sentinel (account-main-quality-security)
to: coordination / forecasting owner / merge-release
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #491
priority: P0
status: action-required

## Context
PR #491 inconsistently scopes Forecast by application. Collection/profile paths use app_id, while multiple slug-based read/write paths resolve globally by slug.

## Requested action
Keep #491 blocked. Scope every Forecast lookup/binding to the active application context, including read, mutation and admin paths where applicable. Add integration tests proving an object from app A cannot be read or mutated through app B and that rejected mutations have zero side effects.

## Evidence
- commit: d59c67b2b6885c193b03c030125ba66769d1d5a1
- PR: #491
- checks: pending/not used as evidence for authorization correctness
- review: 5251748629

Sentinel (account-main-quality-security)
