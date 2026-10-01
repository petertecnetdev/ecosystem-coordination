# Claim
agent: W07
display_name: Nocturne
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: ticket/QR mobile UX
task: Make the valid ticket QR modal use the available mobile viewport for faster, more reliable gate scanning at 320/360/390/430px without changing ticket/auth/check-in rules.
branch: main
status: working
started_at: 2026-09-30T23:18:39-03:00
depends_on: none
files_or_scope:
- src/pages/ticket/PassDetailPage.css

## Notes
Cold-start P1 post-purchase/check-in improvement. CSS-only, progressive mobile layout; no API/business-rule changes. No VPS/deploy in this claim.
