# W08 worklog — artist identity claim relations

- Worker: W08 — Navigation Weaver
- Item: W08-019
- Priority: P1
- Status: IMPLEMENTED_CI_BASELINE_BLOCKED_NOT_DEPLOYED
- Completed: 2026-09-28T08:47:00-03:00

## Problem
Manual identity-review cards showed the claimed artist and requesting user but offered only approve/reject. Reviewers had to search both profiles manually before making a trust-sensitive decision.

## Implementation
- API selects `artists.slug as artist_slug` from the existing claim-queue join.
- Frontend opens the exact canonical artist route when the slug is available.
- Frontend opens the exact public claimant profile using the existing `user_id`.
- Links open in new tabs so typed review notes and queue context remain intact.
- W02-owned ArtistViewPage presentation was not edited.
- No additional query, N+1, source-page request, authorization or mutation change.

## Files
- API: `app/Domain/People/Services/ArtistOnboardingService.php`
- Frontend: `src/pages/admin/ArtistIdentityClaimsAdminPage.js`

## Git
- API PR #536, merge `5fea1752fb674dd463b65bb2069f2c13117e2749`
- Frontend PR #691, merge `9144f147d9e1252d07001b756167868d99183779`

## Validation
- API PR CI 36416672518 and main CI 36417038869:
  - PHP syntax: success
  - clean migrations: success
  - canonical routes: success
  - architecture: success
  - tests/enforcement: failure, matching base-main run 36408040102
- API Deploy 36417196397: skipped.
- Frontend PR Validate 36416670747: success.
- Frontend PR Lighthouse 36416670751: success.
- Frontend main Validate 36417049343: success.
- Frontend main Lighthouse 36417049430: success.
- Frontend Deploy 36417209670: failed at build-environment fetch; build/deploy/health skipped.

## Expected impact
Reduces friction and false-decision risk in artist identity moderation by making both sides of the relationship directly inspectable.

## Pending
- Recover the API baseline test gate and rerun API release.
- Recover frontend build-environment fetch and run deployment through health check.
- Do not promote W08-019 to VERIFIED/runtime status before both contracts are deployed.
