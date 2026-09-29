# W09 Worklog — free event SEO offer
worker: W09 Public UX SEO (W09)
date: 2026-09-28
repository: petertecnetdev/cutinapp.petertecnet.com.br
pending_deploy_vps: true

## Problem
Public events explicitly marked free could have no ticket rows in the SEO input. In that case Event structured data omitted offers and did not state isAccessibleForFree, reducing semantic completeness for crawlers.

## Change
- `src/utils/eventSeo.js`: synthesize one zero-price Schema.org Offer only when `event.is_free === true` and there are no ticket-derived offers; cancelled events expose SoldOut.
- `src/utils/eventSeo.test.js`: add regression coverage for active and cancelled free events without ticket rows.

## Evidence
- VPS `petertecnetserver`: offline at start of cycle; Git fallback used.
- implementation commit: `1b3aab991014e30b5ef68922a6d1bd6270b77725`
- test commit: `39101a57f5da9870303cf260c9917b04e9580189`
- W09 state commit: `d206ce35c474a26f6a3d89b4f21a571e7f0754b8`
- completed claim commit: `d8df371e4afb1470c5c6cc0d796f60ba49a5f947`
- active claim closed: `cbcaf0b79f78b5b8e80f9493afc8c2554d2541c3`

## Validation
Static review completed. Tests were added but could not be executed because the GitHub fallback connector has no command runner. No VPS/runtime/crawler claim is made.

## Economic/SEO impact
Improves structured-data completeness for free public events and gives search engines explicit free-access/offer semantics without inventing a paid price or availability.

## Next
When VPS returns, reconcile main without destructive reset, run eventSeo tests + build, validate JSON-LD in served event pages/crawler, and clear pending_deploy_vps only after runtime evidence.
