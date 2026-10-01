# Claim
agent: w07-frontend-ux-mobile
display_name: W07 Frontend UX Mobile
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: ticket/QR mobile
task: Keep the screen awake only while a valid ticket QR is open, with graceful fallback and explicit release.
branch: local w09/production-seo-prerender (pre-existing VPS checkout)
status: handoff
started_at: 2026-09-30T22:20:00-03:00
completed_at: 2026-09-30T22:28:00-03:00
depends_on: authenticated publication by W10
files_or_scope:
- src/pages/ticket/PassDetailPage.js

## Evidence
- IMPLEMENTED: yes
- COMMITTED: local e5a06432
- PUSHED: no; HTTPS credential unavailable on VPS
- MERGED: no
- BUILT: no
- DEPLOYED: no
- RUNTIME VERIFIED: no
- git diff --check: PASS
- npm run lint:ux-regressions: PASS

## NEXT_ACTION
W10 should reapply only the PassDetailPage Wake Lock delta onto current remote main, run CI/build, then validate acquire/release and a real QR scan on compatible Android Chrome. Existing dirty VPS worktree files were preserved and no deploy was performed.
