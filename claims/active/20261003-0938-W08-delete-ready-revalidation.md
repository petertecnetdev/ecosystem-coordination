# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/api.petertecnet.com.br
area: branch-hygiene-delete-ready-revalidation
task: Revalidate 40 previously classified DELETE_READY automation/* refs against current main and merged PR state; produce executable deletion manifest without deleting refs
branch: none
status: working
started_at: 2026-10-03T09:38:00-03:00
depends_on: delete-ref capability unavailable
files_or_scope:
- automation/* positions 15-54 from branch-audit/w08-api-automation-round2-20261003-0530.md

## Notes
Excludes W07 agent/* and w07/* shards. No branches will be created. Financial/auth/webhook/migration candidates require second review.
