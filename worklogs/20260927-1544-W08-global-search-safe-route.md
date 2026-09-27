# W08 Worklog — Safe global-search destinations

worker: Navigation Weaver (W08)
date: 2026-09-27
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: VERIFIED

## Problems found

- Full global search called `navigate(item.url)` directly.
- The global search overlay called `navigate(url)` directly.
- Missing URLs could create dead clicks/errors; external or protocol-relative values could leave the Cutinapp.
- Prefetch parsed the unvalidated URL and could request an unrelated entity slug.

## Point

- W08-006 — keep global-search relation navigation inside valid application routes.

## Files

- `src/utils/entityRoutes.js`
- `src/utils/entityRoutes.test.js`
- `src/pages/search/GlobalSearchPage.js`
- `src/components/GlobalSearchOverlay.js`

## Implementation

- Added reusable `safeInternalRoute`.
- Preserved internal path/query destinations.
- Rejected missing, absolute external, protocol-relative, backslash and control-character destinations.
- Applied normalized destinations to navigation, recent storage, telemetry and prefetch.
- Fallback is `/search`; an invalid caller-provided fallback degrades to `/`.
- No API, entity data, auth, checkout or claimed W01-W04 view was changed.

## Tests and review

- Added three tests for valid route, invalid destinations and invalid fallback.
- First CI attempt: all 850 tests passed, but build exposed ESLint `no-control-regex`.
- Replaced the regex with character-code inspection; behavior remained covered.
- Validate 36341305128 passed: 138 suites, 850 tests, build and performance budget.
- Lighthouse 36341305134 passed.

## Commit / PR / push

- final branch commit: `d70a81af6f2f6a12cc67dcf927e90509e86e7945`
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/674
- merged commit: `8feb34b8056cc839b042b34396d5cc431f3a1098`
- push/merge: completed through PR

## Deploy

- Not declared published. Exact production release identity has not been verified for this commit.

## Evidence

- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36341305128
- https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36341305134
- `claims/completed/20260927-1534-W08-global-search-safe-route.md`

## Pending / requests

- W03/W04 still own the requested `ItemDiscoveryRail` dead-fallback fix.
- W03/API still own blog relational fan-out reduction.
- W05 has recognized W08 ownership in MASTER and should continue conflict arbitration.

## Expected commercial impact

Prevents discovery clicks from becoming dead ends or leaving the product because of incomplete/malformed API route data. This protects navigation depth toward events, productions, artists, profiles and items. No conversion metric is asserted without measured data.

Signed: Navigation Weaver (W08)
