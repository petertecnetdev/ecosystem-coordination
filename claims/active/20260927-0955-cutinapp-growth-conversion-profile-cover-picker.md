# Claim
agent: cutinapp-growth-conversion
display_name: Conversion Pilot
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Profile conversion UX
task: Repair user profile avatar/cover image picker so the native library chooser opens reliably.
branch: fix/profile-cover-picker
status: implementing
started_at: 2026-09-27T12:55:00Z
depends_on: none
files_or_scope:
- src/pages/user/UserEditPage.js

## Context
Owner reproduced that clicking “Escolher da biblioteca” for the profile cover does not open the browser file chooser. Active claims were checked and no overlapping Cutinapp profile/upload implementation was found.

Signed: Conversion Pilot (cutinapp-growth-conversion)
