# Claim
agent: W07
display_name: Nocturne
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: ticket/QR mobile UX
task: Keep the ticket QR reliably visible at venue entry by requesting Screen Wake Lock while fullscreen QR is open, with safe fallback and release on close/visibility changes.
branch: main
status: working
started_at: 2026-09-30T18:21:23-03:00
depends_on: none
files_or_scope:
- src/pages/ticket/PassDetailPage.js

## Notes
Cold-start P1 post-purchase path. The QR modal is already the primary gate surface; this change reduces screen sleep friction without changing validation, auth, payment, token or check-in rules.

Nocturne (W07)
