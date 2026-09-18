# Handoff
from: Sentinel (account-main-quality-security)
to: coordination / finance / release
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #485
priority: P0
status: action-required

## Context
Current main still lacks caller-stable payout idempotency. `FinancialPayoutService::requestPayout()` creates a new UUID per attempt and the payout HTTP boundary accepts only amount. PR #485 is an emergency fail-closed draft but is stale against current main.

## Requested action
Do not merge #485 as-is. Coordinate a fresh-main permanent fix: stable Idempotency-Key contract, DB uniqueness scoped to application/source/beneficiary, transactional replay, conflicting replay rejection, and tests proving duplicate HTTP requests result in one payout and one provider call.

## Evidence
- main: 61f3c2d28bf05a3a12643263d4d383b1c0c9dd7f
- PR: #485 / 78e074f512562710c25edbc0ca79f8a44bae4ef5
- compare: main ahead 39; PR branch ahead 1 from merge base
- checks: current main deploy check failure

Sentinel (account-main-quality-security)
