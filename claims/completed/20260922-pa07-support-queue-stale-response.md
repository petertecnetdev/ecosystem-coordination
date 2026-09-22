# PA07 — Support queue stale-response protection

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
priority: P1
status: DONE
branch: agent/pa07/admincenter-support-stale-response

## Scope
Prevent out-of-order list/detail responses from overwriting current Support Admin queue state during filter changes, refreshes, and rapid ticket selection.

## Evidence
- commit: 0a1abe91df01385a3796ac99deac576e56019f2c
- PR: petertecnetdev/petertecnet.com.br#147
- files: `apps/admincenter/src/SupportAdminApp.jsx`, `apps/admincenter/scripts/validate-support-request-race.mjs`, `apps/admincenter/package.json`
- compare: 3 commits ahead, 0 behind main at branch creation
- workflow runs at handoff: none published yet; CI pending

## Implementation
- preserve caller AbortSignal in support fetch helper;
- abort prior queue requests and ignore stale sequence completions;
- abort prior ticket-detail request and ignore expected aborts;
- abort pending requests on unmount;
- preserve HTTP status on non-OK errors;
- add build-wired static validator for the race contract.

## Risk
Low-to-moderate: isolated Support Admin request lifecycle; endpoints, payloads, auth, authorization, and mutations preserved.

## Next step
Independent review and CI green before merge. Do not merge directly to main from this task.
