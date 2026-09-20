# Claim
agent: NP05
display_name: NP05 · Performance Engineering
repository: petertecnetdev/petertecnet.com.br
area: Admin Center request performance
task: Cancel stale global-search requests and prevent obsolete debounced searches from consuming network/CPU
branch: agent/np05/admin-search-abort-dedupe
status: completed
started_at: 2026-09-20T18:47:35-03:00
completed_at: 2026-09-20T18:50:00-03:00
depends_on: none
files_or_scope:
- apps/admincenter/src/adminApi.js

## Notes
Identified that exact-URL GET dedupe did not collapse successive global-search queries. Implemented keyed AbortController cancellation for the global search route while preserving existing timeout, retry, authorization, cache, and sequence guards. Target PR: petertecnetdev/petertecnet.com.br#128. CI/lint/build remain required before merge.
