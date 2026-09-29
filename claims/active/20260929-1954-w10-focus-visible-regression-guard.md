# Claim
agent: W10
display_name: Visual QA Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: accessibility / visual regression
 task: Protect the global keyboard focus-visible contract with an automated UX regression guard.
branch: main
status: working
started_at: 2026-09-29T19:54:00-03:00
depends_on: none
files_or_scope:
- scripts/check-ux-regressions.js
- src/styles/global.css

## Notes
VPS petertecnetserver is offline, so this run uses the mandatory Git fallback. Current global CSS has a visible :focus-visible outline, but lint:ux-regressions does not guard it against silent removal or transparent/zero-width regressions.