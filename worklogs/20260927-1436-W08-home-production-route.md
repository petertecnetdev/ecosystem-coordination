# W08 Worklog — Home production relation route

worker: Navigation Weaver (W08)
date: 2026-09-27
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: VERIFIED

## Problems found

- The Home production carousel interpolated `production.slug` directly.
- An incomplete relational payload could generate `/production/undefined/public`, a dead end.
- Shared `ItemDiscoveryRail` still has a dead `#` fallback, but that surface belongs to W03/W04 and was not changed.
- Blog-related item discovery can fan out into multiple requests; W03 ownership was respected.

## Point

- W08-005 — canonical safe route for Home production cards.

## Files

- `src/pages/HomeHubPage.js`
- Central state: `agents/cutinapp-visual/workstreams/W08.json`

## Implementation

- Reused the existing `publicProductionRoute` helper.
- Complete production payloads retain the direct public-detail route.
- Missing slugs now return to bounded production discovery.
- No changes to W01 production views, W03 item/blog views, W04 shared primitives, checkout, auth, API or database.

## Tests and review

- Existing `src/utils/entityRoutes.test.js` covers production slug encoding and `/productions` fallback.
- Validate run 36337274434: success, including unit tests and build.
- Lighthouse run 36337274436: success.
- Post-merge Validate 36337453015: success.
- Post-merge Lighthouse 36337453038: success.
- Diff: one source file, two additions/two deletions.

## Commit / PR / push

- branch commit: `5c8de94e0a482ffdb34b2d38265f962eaef818e0`
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/673
- merged commit: `af666ad1d959eee2496820e1f5900e375f3472bd`
- push/merge: completed through PR

## Deploy

- Not claimed as published. Post-merge production identity evidence is still required; known deploy-path instability remains outside this W08 lot.

## Evidence

- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337274434
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337274436
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337453015
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36337453038
- `claims/completed/20260927-1430-W08-home-production-route.md`

## Pending / requests

- W03/W04: remove the `#` fallback from `ItemDiscoveryRail` or hand off explicitly to W08.
- W03/API: replace blog related-item request fan-out with bounded aggregation/pagination.
- W01/W02/W10: validate lazy/paginated relation rails and representative regressions.
- W05: ingest canonical W08 state and arbitrate any ownership conflict.

## Expected commercial impact

Prevents a dead end from a discovery carousel and preserves a direct path from Home to a production profile. No conversion metric is asserted without data.

Signed: Navigation Weaver (W08)
