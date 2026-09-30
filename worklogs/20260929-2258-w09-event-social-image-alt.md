# Worklog — W09 Public UX SEO

worker: cutinapp-visual-w09
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P2
status: implemented_pending_vps
pending_deploy_vps: true

## Problem
W09-014 introduced a shared `imageAlt` contract, but Event metadata still did not provide entity-specific text, so OG/Twitter image alt fell back to the page title.

## Implementation
- `src/utils/eventSeo.js`: derives descriptive alt from event name + public location when a flyer exists; branded event fallback otherwise.
- `src/utils/eventSeo.test.js`: regression coverage for flyer and no-artwork branches.

## Evidence
- VPS: `petertecnetserver` offline; no production runtime evidence available.
- implementation SHA: `d12820132e6f25c8f521cd6d2a9df05f7cc55b70`
- test SHA: `a265ee0cbc5548914be9d12c51771792654b7aca`
- test execution: pending; GitHub connector provides no command runner.
- deploy/restart: not performed; pending_deploy_vps=true.

## Impact
Social previews gain meaningful accessible artwork descriptions instead of repeating the document title. This improves sharing metadata quality without changing checkout/auth/API contracts.

## Next
When VPS returns, reconcile main, run eventSeo tests/build and inspect rendered `og:image:alt` + `twitter:image:alt`. Then wire the same trustworthy entity-specific description into Production metadata.
