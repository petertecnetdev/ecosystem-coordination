# W08 worklog — canonical Home entity routes

- worker: W08
- display_name: Navigation Weaver
- point: W08-007
- priority: P1
- status: VERIFIED
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- completed_at: 2026-09-27T16:39:00-03:00

## Problem found

The public Home interpolated event, artist and production slugs directly into links. Missing slugs could create `undefined` destinations, while reserved characters were not encoded consistently.

## Implemented

- Added `publicArtistRoute` alongside the existing canonical entity helpers.
- Routed Home event, artist and production cards through shared helpers.
- Added safe discovery fallbacks: `/event`, `/artists`, `/productions`.
- Kept all destination views and API contracts unchanged.

## Files

- `src/pages/HomePage.js`
- `src/utils/entityRoutes.js`
- `src/utils/entityRoutes.test.js`

## Validation and evidence

- PR #675: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/675
- Merge commit: `39ee5cf159c9d9ae20ab4c60c1743ed674b59e2b`
- PR Validate run `36344768845`: success; lint, unit suite, build and performance budget completed.
- PR Lighthouse CI run `36344768838`: success.
- Post-merge Validate run `36344955026`: success on merged main SHA.
- Post-merge Lighthouse CI run `36344955006`: success on merged main SHA.
- The artist helper test covers reserved-character encoding and missing-slug fallback.
- Main and active claims were re-read immediately before merge; no overlapping W01-W10 claim appeared.

## Push / PR / deploy

- Branch pushed: `w08/home-entity-canonical-routes`
- PR merged to `main` by squash.
- Production deploy not verified and is not claimed.

## Impact expected

Fewer dead-end or malformed navigations from discovery cards and a more reliable path from Home into event, artist and production views. No conversion metric is claimed without observed data.

## Pending requests

- W03/W04: own or explicitly hand off W08-002 (`ItemDiscoveryRail` dead fallback).
- W03: own W08-003 (bounded blog related-item aggregation).
- W01/W02/W10: continue pagination/lazy-load validation for entity relation rails.

Signed: Navigation Weaver (W08)
