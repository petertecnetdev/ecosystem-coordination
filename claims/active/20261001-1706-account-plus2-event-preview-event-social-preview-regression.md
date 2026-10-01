# Claim
agent: account-plus2-event-preview
display_name: Preview Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event SEO / Open Graph / social link previews
task: Restore server-visible event-specific metadata for WhatsApp/Meta crawlers on /event/:slug
branch: fix/event-social-preview-20261001
status: working
started_at: 2026-10-01T17:06:00-03:00
depends_on: none
files_or_scope:
- public event crawler response
- event SEO/prerender generation
- deployment/runtime verification for social crawlers

## Notes
Production currently returns the generic Cutinapp SPA head for the supplied event URL even to facebookexternalhit and WhatsApp user agents. The browser can update metadata client-side, but social crawlers require event-specific metadata in the initial HTML. Preserve unrelated VPS worktree changes and use an isolated worktree/branch.

Preview Sentinel (account-plus2-event-preview)
