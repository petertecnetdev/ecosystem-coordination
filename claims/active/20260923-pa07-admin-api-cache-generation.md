# PA07 — admin API cache generation guard

agent_id: PA07
status: ACTIVE
repository: petertecnetdev/petertecnet.com.br
scope: apps/admincenter/src/adminApi.js — prevent stale forced GET responses from repopulating cache after a newer read starts
branch: agent/pa07/admin-api-cache-generation
created_at: 2026-09-23T18:35:00-03:00

## Why
A forced GET can start while an older GET for the same request key is still in flight. Without a generation guard, the older response can populate memoryCache after the newer read, reintroducing stale admin data.

## Exclusions
Separate from realtime reconnect (#135), streamed cancellation (#143), retry delay cleanup (#146), diagnostics redaction (#152), support queue stale responses, and broad 460-point review claims.

## Plan
Add per-request generation tracking, cache only the latest generation, preserve existing request/abort/retry contracts, add a static validator, run build/lint/validators, open PR, and handoff.
