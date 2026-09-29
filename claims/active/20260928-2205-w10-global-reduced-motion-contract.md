# Claim
agent: W10
display_name: W10 Visual QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: accessibility / visual regression
task: Add an automated regression check that fails if the global prefers-reduced-motion accessibility contract is removed or weakened.
branch: main
status: completed_pending_runtime
started_at: 2026-09-28T22:05:00-03:00
completed_at: 2026-09-28T22:11:00-03:00
depends_on: none
files_or_scope:
- scripts/check-ux-regressions.js

## Result
Implemented on main in commit `2e0db0c3cba8b5276c0897c3a7aab46fa6b75c02`. The guard protects the existing global reduced-motion accessibility contract. `pending_deploy_vps: true` because petertecnetserver remained offline. Runtime/build command validation must be performed when VPS/runner access returns.