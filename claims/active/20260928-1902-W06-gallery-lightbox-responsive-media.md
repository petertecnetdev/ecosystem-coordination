# Claim
agent: W06
display_name: MediaForge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: event poster media safety/performance
task: Guard event poster source pixel dimensions before expensive 1024x1536 canvas normalization
branch: main
status: working
started_at: 2026-09-28T19:02:00-03:00
depends_on: none
files_or_scope:
- src/utils/eventPoster.js

## Notes
VPS device is offline; using mandatory Git fallback. Discovery found source files are byte-limited but not pixel-dimension-limited, allowing unusually large decoded images to consume excessive browser memory before normalization. Scope is isolated to W06 event poster validation and does not overlap active claims observed.
