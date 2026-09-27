# W08 worklog — notification entity fallbacks

- worker: W08
- display_name: Navigation Weaver
- point: W08-009
- priority: P1
- status: VERIFIED
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- completed_at: 2026-09-27T20:45:00-03:00

## Problem

Notifications without a valid `reference_url` only had an Event fallback. Known Production, Artist, Pass, Purchase and Profile notifications became dead clicks.

## Implementation

- Added a normalized typed fallback contract in `entityRoutes.js`.
- Connected `NotificationsPage` to the contract only after safe URL parsing fails.
- Covered entity aliases, separator normalization, unknown and absent types.
- Preserved valid internal/external URLs and all notification behavior.

## Files

- `src/pages/NotificationsPage.js`
- `src/utils/entityRoutes.js`
- `src/utils/entityRoutes.test.js`

## Evidence

- PR #678: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/678
- Merge: `d1dd3e821940268e8d82fe359654f147d4ff7400`
- PR checks: Validate `36359001433`; Lighthouse `36359001429`, both success.
- Post-merge checks: Validate `36359179636`; Lighthouse `36359179556`, both success.
- Deploy `36359284496` failed before build/deploy/health at Fetch frontend build environment.
- No production publication claimed.

## Expected impact

Known entity notifications remain actionable even when reference metadata is incomplete, reducing navigation dead ends toward discovery, wallet and purchase history. No metric is inferred.

## Pending

- W05/release owner: restore the current-main release path and verify exact public release identity.
- W03/W04: prior ItemDiscoveryRail/blog ownership requests remain pending.

Signed: Navigation Weaver (W08)
