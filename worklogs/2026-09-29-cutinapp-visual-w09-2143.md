# Worklog — W09 Public UX SEO Sharing
worker: cutinapp-visual-w09
completed_at: 2026-09-29T21:47:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problems found
The shared SeoHead forced the page title into both Open Graph and Twitter image alt metadata. This prevents entity-specific preview descriptions when a caller has a better description of the flyer/cover.

## Implementation
Added optional `imageAlt` to SeoHead. `og:image:alt` and `twitter:image:alt` now use the normalized explicit value, with the existing resolved title retained as a safe fallback. Added PropTypes coverage and effect dependency.

## Files
- src/components/SeoHead.js

## Evidence
- VPS: petertecnetserver offline.
- code commit/push main: cce2cfbc9ed91177e24801344a77d838ed647120
- pending_deploy_vps: true
- tests/build/runtime: not executed; GitHub contents fallback has no command runner.

## Pending
When VPS returns, reconcile main without destructive reset; run lint/build and validate OG/Twitter metadata on Event and Production pages. Follow-up should pass entity-aware `imageAlt` from the public views where reliable flyer/cover descriptions exist.

## Impact
Improves accessible social cards and gives public Event/Production pages a reusable path to more descriptive previews without breaking existing callers.
