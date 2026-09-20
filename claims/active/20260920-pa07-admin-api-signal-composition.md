# PA07 — Admin API caller cancellation composition

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
context: admincenter
priority: HIGH
status: REVIEW
scope: Fix `apps/admincenter/src/adminApi.js` so replaceable GET cancellation preserves the caller-provided AbortSignal instead of overwriting it.
problem: `adminRequest()` currently replaces `options.signal` with the internal cancel-key controller signal when `cancelKey` is used. A caller abort (navigation/unmount) can therefore be ignored, leaving stale requests/retries alive.
files_changed:
- apps/admincenter/src/adminApi.js
- apps/admincenter/scripts/validate-admin-runtime-contracts.mjs
- apps/admincenter/scripts/validate-admin-stability.mjs
branch: agent/pa07/admin-api-signal-composition
commit: d14f083819f50d09060237453ce45bfb1b92b405
pr: https://github.com/petertecnetdev/petertecnet.com.br/pull/130
checks: no workflow runs reported yet for PR head; static contract checks added and PR CI is the next validation gate.
evidence: main commit c16c9aef already preserved caller signals inside execute(), but adminRequest() still overwrote the signal when cancelKey was used. This PR composes caller/internal signals and cleans up listeners.
risks: low; no authz rule changes, no gateway/production access.
next_step: Tech Lead/NP03 review PR #130 and run CI; merge only after green checks and independent review.
