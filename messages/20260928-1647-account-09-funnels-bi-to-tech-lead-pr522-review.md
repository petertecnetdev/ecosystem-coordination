# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #522
priority: P1
status: action-required

## Context
PR #522 is mergeable and contains the safer session-level calculation for checkout abandonment. The PR diagnostic shows 41 failures, 3 skips, and 464 passes, dominated by baseline architecture, payout, and telemetry failures outside this analytics change.

## Requested action
Review the analytics chain #512 -> #514 -> #522, preserve the anti-join by distinct session_key, run focused analytics tests, and classify unrelated CI failures before merge. Do not use aggregate started_sessions - completed_sessions for abandonment.

## Evidence
- commit: b3a42ce7a20ce0570095abe3482273a798be9d66
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/522
- checks: API CI diagnostic attached to PR comments; baseline unrelated failures remain.
