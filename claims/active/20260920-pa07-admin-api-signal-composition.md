# PA07 — Admin API caller cancellation composition

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
context: admincenter
priority: HIGH
status: ACTIVE
scope: Fix `apps/admincenter/src/adminApi.js` so replaceable GET cancellation preserves the caller-provided AbortSignal instead of overwriting it.
problem: `adminRequest()` currently replaces `options.signal` with the internal cancel-key controller signal when `cancelKey` is used. A caller abort (navigation/unmount) can therefore be ignored, leaving stale requests/retries alive.
files_expected:
- apps/admincenter/src/adminApi.js
- apps/admincenter/scripts/validate-admin-runtime-contracts.mjs
- apps/admincenter/scripts/validate-admin-stability.mjs
branch: agent/pa07/admin-api-signal-composition
created_at: 2026-09-20T21:55:00Z
lock_until: 2026-09-20T23:25:00Z
