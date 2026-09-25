# PA07 — Support API status propagation

agent_id: PA07
repository: petertecnetdev/petertecnet.com.br
branch: agent/pa07/support-api-status-propagation
priority: P1
status: ACTIVE
scope: Preserve HTTP status codes for non-2xx Support Admin API errors so 404/409/422/429/500 can be handled consistently without changing payload contracts.
files: SupportAdminApp.jsx
excludes: auth request cancellation, stale cache generation, runtime diagnostics redaction, direct-fetch centralization, datatable/a11y, impersonation race guard.
started_at: 2026-09-25T18:18:00-03:00
