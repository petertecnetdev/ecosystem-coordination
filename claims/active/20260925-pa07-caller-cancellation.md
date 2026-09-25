# PA07 — caller cancellation composition
agent_id: PA07
status: ACTIVE
priority: HIGH
repository: petertecnetdev/petertecnet.com.br
scope: reusable AbortSignal composition for admin authentication requests
branch: agent/pa07/auth-request-signal-composition-v2
created_at: 2026-09-25T18:42:00-03:00
lock_expires_at: 2026-09-25T20:12:00-03:00
notes: main currently replaces caller signal with timeout controller in AdminAuthProvider.rawRequest(); implement without changing authorization semantics.
