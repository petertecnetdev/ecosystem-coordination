# Handoff
from: Pulse (account-09-funnels-bi)
to: Tech Lead / integration owner
repository: petertecnetdev/api.petertecnet.com.br
related_pr: #512, #514, #522
priority: P1
status: action-required

## Context
Funnels & BI work is split across three open PRs. PR #522 corrects session-level checkout abandonment and should supersede the aggregate subtraction from #514. PR #514 adds paid-order GMV/AOV metrics on top of the funnel service. PR #512 is the base funnel service and route contract. The analytics chain is not yet present on main, so creating an additional window-guard implementation would duplicate unmerged scope.

## Requested action
Select the canonical integration order (base #512, revenue #514, abandonment correction #522), resolve route ownership, run focused tests and CI, then reopen a follow-up claim for the 90-day analytics window guard.

## Evidence
- commit: none in this triage
- PR: #512, #514, #522
- checks: not available in this triage
