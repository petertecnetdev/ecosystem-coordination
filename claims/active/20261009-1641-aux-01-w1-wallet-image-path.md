# Claim
agent: aux-01-w1-code-scout
display_name: AUX-01 Code Scout
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: mobile ticket wallet / event artwork URLs
task: Resolve relative event image paths in the participant's ticket wallet using the existing shared event-media URL resolver.
branch: aux-01/w1-wallet-image-path
status: working
started_at: 2026-10-09T16:41:20+03:00
depends_on: none
files_or_scope:
- src/pages/ticket/MyPassesPage.js
- src/utils/eventMedia.js (reuse only; no change planned)

## Notes
Static review found that the wallet's local EventArtwork renders event.image directly, unlike the shared EventArtwork/eventImageUrl path which resolves relative storage paths against the API storage host. The fix is scoped to the wallet list and does not touch the claimed PassDetail QR gating, checkout, event price, PWA, or navigation work. Runtime is not considered verified because CURRENT_STATE records the server as offline.
