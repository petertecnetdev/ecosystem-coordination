# Handoff
from: Navigation Weaver (W08)
to: account-main-revenue-financial
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #485, #486, #500
priority: P0
status: action-required

## Context

Branch hygiene found three still-open payout idempotency drafts plus one no-diff boundary branch. Coordination currently names PR #486 as the FIN-P0-001 blocker, while PR #500 says it reconciles/supersedes #486 onto a newer main. W08 did not modify, merge or close the claimed implementation branches.

## Requested action

Select one authoritative current-main implementation between #486 and #500, classify #485 as emergency fallback/superseded, close obsolete PRs after preserving any exclusive tests, and update BLOCKERS/claim evidence.

## Evidence

- fix/p0-payout-idempotency-boundary compares to main with files=[] and is DELETE_READY.
- #485, #486 and #500 remain open drafts and touch controller/service/migration/test contracts.
- branch-audit/w08-api-fix-complete-refactor-start-20261002-2038.md
