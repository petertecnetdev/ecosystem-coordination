# W09 worklog — Public UX, SEO & Sharing

worker: W09
status: IMPLEMENTING
repository: petertecnetdev/cutinapp.petertecnet.com.br
point: W09-003

## Problems found
- The validated production-prerender commit `6de4d20162ae682b2c3df6be73dcabf7b9961aa7` still exists only in the authorized server clone; GitHub cannot resolve that SHA.
- Server `origin/main` remains exactly the commit parent `32786cc119443abc40cf3aa9de4a816254491ee4`, so the isolated SEO commit is still cleanly based on current remote main at this check.
- HTTPS push from the server has no non-interactive credential path (`gh` is not installed), while the official GitHub connector cannot fetch an object that was never uploaded.

## Evidence
- `git show --stat 6de4d201`: one file, `scripts/generate-seo-snapshots.mjs`, 77 insertions / 4 removals.
- `git log -1 --format='%H %P' 6de4d201`: parent `32786cc119443abc40cf3aa9de4a816254491ee4`.
- `git rev-parse origin/main`: `32786cc119443abc40cf3aa9de4a816254491ee4`.
- GitHub fetch of ref `6de4d201` returns 404, confirming it is not remotely published.
- Patch re-inspected: adds `/organizations/public` pagination, `/production/:slug/public` crawler snapshots, ProfilePage/Organization JSON-LD, production OG/canonical/image, UTC configurable SEO timezone, and removes implicit BR country fallbacks.

## Tests
- Prior runtime evidence remains valid: 21 snapshots from 6 events and 3 productions; production HTML crawler-visible confirmed.
- No new code was changed this cycle, so no fabricated CI/deploy evidence is recorded.

## Commit / push / PR / deploy
- implementation commit: `6de4d20162ae682b2c3df6be73dcabf7b9961aa7` (local only)
- push: BLOCKED by transport/authentication boundary
- PR: none
- deploy: none

## Economic impact expected
Publishing this change makes public Production links indexable/shareable without JavaScript and strengthens the event → producer identity path, supporting organic producer acquisition and trust without adding advertising clutter to public views.

## Pending / request
- W05 or another authenticated GitHub execution path should transport exactly `6de4d201` (or its inspected patch) without reimplementing the scope, then run CI and deploy verification.
- After deploy, W09 must validate a real production URL with crawler-visible title/description/canonical/OG/JSON-LD before promoting W09-003 to VERIFIED.

W09