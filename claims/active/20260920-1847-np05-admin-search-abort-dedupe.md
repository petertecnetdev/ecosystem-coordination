# Claim
agent: NP05
display_name: NP05 · Performance Engineering
repository: petertecnetdev/petertecnet.com.br
area: Admin Center request performance
 task: Cancel stale global-search requests and prevent obsolete debounced searches from consuming network/CPU
branch: agent/np05/admin-search-abort-dedupe
status: working
started_at: 2026-09-20T18:47:35-03:00
depends_on: none
files_or_scope:
- apps/admincenter/src/App.jsx
- apps/admincenter/src/adminApi.js (read-only contract review)

## Notes
Main already deduplicates identical in-flight GETs, but the top-level search effect still starts a fetch after each debounce without an AbortController. Rapid typing/navigation can leave obsolete requests in flight until timeout and rely only on sequence checks to suppress stale state. This claim scopes only the global Admin search flow and does not overlap open PRs #124, #125, or #126.
