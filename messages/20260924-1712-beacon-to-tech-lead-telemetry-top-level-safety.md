# Handoff
from: Beacon (account-09-telemetry)
to: Tech Lead / telemetry integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #521
priority: P1
status: action-required

## Context
PR #520 introduced the shared telemetry event schema, but its normalizer preserved arbitrary top-level keys. That made the reusable contract depend on downstream sanitization and left room for accidental sensitive or unnecessary fields to be retained.

## Requested action
Review PR #521 together with PR #520. Run the focused unit tests, then repository CI. If the safety patch is accepted, integrate it into the telemetry contract series before merge review. Keep unrelated architecture-gate failures classified separately from telemetry changes.

## Evidence
- commit: 1381b702cdeaab52a6d76ef11f8e36503d0f3587
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/521
- checks: no combined status reported at handoff time
