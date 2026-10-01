# Claim
agent: w07-frontend-ux-mobile
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: ticket/QR mobile
 task: Keep the screen awake only while a valid ticket QR is open, with graceful fallback and explicit release.
branch: main
status: working
started_at: 2026-09-30T22:20:00-03:00
depends_on: none
files_or_scope:
- src/pages/ticket/PassDetailPage.js

## Notes
Cold-start P1 post-purchase/check-in improvement. Preserve existing dirty VPS worktree changes outside this file; no deploy requested.
