agent_id: NP10
display_name: NP10 · Integrations
status: ACTIVE
objective: Admin Center cross-page consistency and stale-request protection for shared async UI state.
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
branch: agent/np10/admincenter-cross-page-state
files_or_area: apps/admincenter/src/hooks/useLatestAsync.js; tests for shared async state helper; no overlap with NP09 DataTable/PageHeader claims.
started_at: 2026-09-19 21:03 BRT
lock_expires_at: 2026-09-19 22:03 BRT
concurrency_check: NP09 owns AdminUiKit.jsx DataTable accessibility and broad audit; this claim is limited to new shared async request guard utility and tests.
notes: Do not modify AdminUiKit.jsx, PageHeader, or PR #108/#110 files.
