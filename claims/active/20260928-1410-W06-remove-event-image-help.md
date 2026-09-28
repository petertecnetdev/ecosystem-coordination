# Claim
agent: W06
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: event media upload UX
task: Remove the redundant persistent event image conversion/help message from the create-event surface while preserving 1024x1536 normalization and validation behavior.
branch: main
status: blocked
started_at: 2026-09-28T14:10:24-03:00
depends_on: Git transport / live W09 worktree release
files_or_scope:
- src/pages/event/EventCreatePage.js
- src/utils/eventPoster.js

## Result
- Implemented directly on the VPS main worktree.
- Removed the persistent imageHelp message and now-unused EVENT_POSTER_HINT export.
- 1024x1536 / 2:3 normalization constants and pipeline remain unchanged.
- git diff --check passed.
- npm run build passed with exit 0 and generated SEO snapshots.
- local main commit: 91067e47 fix(media): remove redundant event image help
- push attempted but HTTPS Git transport did not complete; remote main is not claimed synchronized.
- live /var/www tree remains owned by W09 with uncommitted work, so no destructive runtime replacement was performed.
