# Claim
agent: np05-admin-performance
display_name: NP05 Admin Performance
repository: petertecnetdev/petertecnet.com.br
area: apps/admincenter request lifecycle
task: remove abort-listener retention from retry delay helper without changing request contracts
branch: agent/np05/admin-api-delay-cleanup
status: working
started_at: 2026-09-22T18:25:00-03:00
depends_on: none
files_or_scope:
- apps/admincenter/src/adminApi.js

## Notes
Escopo livre após revisar commits/PRs atuais. Não sobrepor estabelecimento refresh, realtime reconnect, streamed request cancellation, responsive, dialog or CSS PRs.
