# Handoff — Independence frontend/SEO partial publication
from: Cutinapp Content Views (W03)
to: W04 independent QA; W00 orchestration; W01/W02 API owners; W05 SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required
branch: Independence
issue: petertecnetdev/ecosystem-coordination#10

## Published evidence — 2026-10-13 05:30 BRT
- Existing frontend HEAD before this run: f7805eeefe945b0230e7d52b4bbf0670168999f1.
- New commits: b61c7cd2d793a99e911f6dd08b34d7f3e46455fb (listing safety Jest tests); d4372179d0e88b800fce0c107dfb7e4616087ebe (mobile-first CSS); 6ba367ef2a1d8bc3032a8d5d1b5bd0500c2a0acd (SEO helpers).
- Latest W03 SHA: 6ba367ef2a1d8bc3032a8d5d1b5bd0500c2a0acd; 5 ahead/0 behind main when checked.
- Files present: src/utils/independenceListing.js, src/utils/independenceListing.test.js, src/components/independence/unverified-listing.css, src/utils/independenceSeo.js.
- No edits to main, event/production pages, SEO generator, sitemap, backend, VPS or deploy.

## Validation
- Local Node built-in test runner (logic smoke): 36/36 PASS; exit 0. Not Jest.
- Local node --input-type=module --check on listing, SEO and claim service drafts: exit 0 each.
- Chromium CSS with representative HTML (NOT integrated React): widths 320/360/390/430 PASS; no horizontal overflow, 46px submit target, visible focus.
- Jest React, lint, full build, API integration, production runtime and GitHub Actions CI: NOT VERIFIED.

## Blocked publication
- Attempts to publish src/utils/independenceSeo.test.js, src/services/IndependenceClaimService.js and src/components/independence/UnverifiedListingPanel.js were blocked by OPENAI_SAFETY_CHECKS. Do not bypass the restriction.
- Therefore the public panel, claim service and React tests are NOT in the branch. Previously prepared W03 v6 package is a local artifact only.
- The published SEO builder is a utility only; not wired to crawler-facing SSR/OG/sitemap.
- Published listing commerce helper is presentation-only. W01 ListingCommercePolicy must block checkout server-side before release.

## Requested actions
1. W00: coordinate authorized publication of remaining five claimed files and explicit ownership handoff before wiring existing event/production pages. Do not overwrite others' claims.
2. W01/W02: confirm authenticated claim API contract, deduplication and server-side commerce gate. Never invent endpoint URLs.
3. W04: run actual Jest, lint/build and browser integration tests on new SHA, including 320/360/390/430 and authenticated/error states.
4. W05: validate canonical/OG/Schema.org Event with original/licensed content, source evidence, sitemap/indexability and crawler-visible rendering.
5. W03: keep claim active until authorized publication and integration checks complete.

## Status
PARTIALLY_PUSHED; CLAIM_WORKING; CI_UNVERIFIED; FIVE_FILES_PENDING; NO_MERGE; NO_DEPLOY.
