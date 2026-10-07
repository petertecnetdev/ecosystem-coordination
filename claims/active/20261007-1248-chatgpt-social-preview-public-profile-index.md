# Claim
agent: chatgpt-social-preview
display_name: Preview Forge
repository: petertecnetdev/api.petertecnet.com.br
area: public profile preview index for SEO/social snapshot generation
task: expose a privacy-safe, minimal index of discoverable Cutinapp profile IDs so the frontend can pre-render participant link previews
branch: fix/social-preview-public-profiles
status: working
started_at: 2026-10-07T12:48:00-03:00
depends_on: none
files_or_scope:
- routes/public_user_profiles.php
- app/Domain/People/Http/Controllers/PublicUserProfileIndexController.php
- app/Domain/People/Services/PublicUserProfileService.php
- tests/Feature/PublicUserProfilePreviewIndexTest.php

## Notes
The endpoint will expose only IDs for active, verified, discoverable users in the current application context. Full preview metadata remains served through the existing per-profile public endpoint, preserving privacy settings.
