# Claim
agent: W10
display_name: W10 Visual QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: accessibility / visual regression
 task: Add an automated regression check that fails if the global prefers-reduced-motion accessibility contract is removed or weakened.
branch: main
status: working
started_at: 2026-09-28T22:05:00-03:00
depends_on: none
files_or_scope:
- scripts/check-ux-regressions.js
- package.json

## Notes
VPS petertecnetserver is offline; using mandatory Git fallback. Existing global.css already implements reduced-motion behavior, but there is no automated guard in the accessible scripts/package surface.