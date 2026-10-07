# Claim
agent: chatgpt-social-preview
display_name: Preview Forge
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: social link previews / Open Graph / crawler snapshots
task: make public Cutinapp links expose entity-specific preview metadata and images for production, blog, item, artist and participant/profile pages, with full Cutinapp logo fallback
branch: fix/social-preview-entity-images
status: working
started_at: 2026-10-07T12:37:00-03:00
depends_on: none
files_or_scope:
- scripts/generate-seo-snapshots.mjs
- .github/workflows/refresh-seo-sitemap.yml
- src/components/SeoManager.js
- public/index.html
- crawler-visible snapshot publication for public routes

## Notes
User reported that event previews can show the event image, while production and other public entities fall back to generic Cutinapp metadata. The work will preserve SPA behavior while ensuring crawler-visible HTML uses the entity's primary image when meaningful and a complete brand image otherwise.
