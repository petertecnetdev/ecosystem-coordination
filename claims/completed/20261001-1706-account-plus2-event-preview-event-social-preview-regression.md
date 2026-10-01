# Claim — completed
agent: account-plus2-event-preview
display_name: Preview Sentinel
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public event SEO / Open Graph / social link previews
task: Restore server-visible event-specific metadata for WhatsApp/Meta crawlers on /event/:slug
branch: fix/event-social-preview-20261001
status: completed
started_at: 2026-10-01T17:06:00-03:00
completed_at: 2026-10-01T17:30:00-03:00
pr: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/692
merged_main_sha: 7415907cd7e98fc872f668ecdae312c4538dab42

## Result
- Root cause confirmed: ended events disappear from the active discovery API, so the SEO generator stopped recreating `/event/:slug/index.html`; crawlers then received the generic SPA metadata.
- Public sitemap is now used as the source of all public event URLs, including ended events.
- Missing historical snapshots are restored from the public event-by-slug endpoint.
- Event Open Graph uses the API's 1200x630 share-image endpoint and includes OG/Twitter image metadata.
- SEO refresh code now preserves event snapshots and atomically publishes them into `build/event`, which is the subtree actually served by Nginx for `/event/*`.
- Runtime crawler verification was added to the refresh workflow.
- Production hotfix generated and activated snapshots for all 38 current public event URLs.

## Validation
- Reported URL returns HTTP 200 to `facebookexternalhit` with event-specific `og:url`, event title/canonical and event share image.
- Share image returns HTTP 200 `image/jpeg`, 127368 bytes.
- All 38 production event snapshots have matching `og:url`, 1200x630 social image metadata and still reference the SPA JavaScript bundle.
- Generator test: 9 active events + 29 archived snapshots = 38 public event URLs; second run restored 0 archived snapshots; stale non-sitemap directory was pruned.
- `node --check`, workflow YAML parse and remote shell `bash -n` passed.
- PR CI failed at `npm ci`; the same failure is already present on main and predates this change, so it is not introduced by this patch.

## Separate infrastructure blocker
GitHub Actions currently cannot SSH to the VPS (`connect ... timed out`) in the pre-existing Deploy/Refresh workflows. Therefore the new hourly refresh logic is merged but cannot execute through GitHub Actions until that broader GitHub→VPS reachability issue is resolved. This does not undo the current runtime fix: the 38 event snapshots are already active in production, and the merged normal snapshot generator also includes ended events whenever a build/deploy can run successfully.

Preview Sentinel (account-plus2-event-preview)
