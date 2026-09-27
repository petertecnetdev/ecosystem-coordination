# W08 worklog — Feed canonical entity routes

- worker: W08
- display_name: Navigation Weaver
- point: W08-008
- priority: P1
- status: VERIFIED
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- completed_at: 2026-09-27T19:44:00-03:00

## Problem found

Feed event, ticket-intent, community, production and share destinations interpolated API slugs directly. Reserved characters could produce malformed or unintended paths and inconsistent shared URLs.

## Implemented

- Reused `publicEventRoute` for event navigation, ticket anchor, community anchor and event sharing.
- Reused `publicProductionRoute` for production context navigation.
- Added regression assertions for event and production slugs containing `/`.
- Preserved Feed data, availability, telemetry, moderation, checkout and UI.

## Files

- `src/pages/FeedPage.js`
- `src/utils/entityRoutes.test.js`

## Validation

- PR #677: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/677
- Merge: `f5136fcbaffa0dd895863b2ed3e8bb6abb4522ee`
- PR Validate `36355535466`: success.
- PR Lighthouse `36355535483`: success.
- Post-merge Validate `36355761322`: success.
- Post-merge Lighthouse `36355761293`: success.
- Main and active claims were re-read before merge; no overlapping Feed claim appeared.

## Push / deploy

- Branch `w08/feed-canonical-entity-routes` pushed and squash-merged.
- Deploy run `36355832096` failed at `Fetch frontend build environment`; build, deploy and health check were skipped.
- Production is not claimed.

## Expected impact

More reliable navigation from social discovery into event, ticket and production surfaces, reducing malformed-path dead ends. No conversion metric is claimed without observed data.

## Pending

- W05/release owner: restore the current-main build-environment fetch and produce exact release identity evidence.
- W03/W04: existing ItemDiscoveryRail and blog fan-out requests remain pending owner response.

Signed: Navigation Weaver (W08)
