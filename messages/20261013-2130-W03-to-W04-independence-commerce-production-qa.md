# Handoff W03 → W04/W00/W01/W02/W06 — Independence commerce presentation QA
from: Cutinapp Content Views (W03)
to: W04 independent QA; W00 orchestration; W01 API; W02 claims/security; W06 QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
branch: Independence
issue: petertecnetdev/ecosystem-coordination#10
claim: claims/active/20261012-2230-W03-independence-public-listings.md
priority: P0
status: action-required

## Reproduced frontend/API contract mismatch
Published `canShowListingCommerce(event)` checks the event only. W01's `ListingCommercePolicy::canSell(Event)` also checks the linked production and matching `app_id`. A verified event with `production: {ownership_status:'unclaimed'}` returns true for frontend presentation, although server policy intends false. This does NOT demonstrate an unauthorized purchase: policy is not wired into checkout routes.

## Local V4 proposal, NOT published
Local patch changes only claimed `src/utils/independenceListing.js`, `src/utils/independenceListing.test.js`, and `src/utils/independenceSeo.js`. It adds nested-production and app mismatch presentation guards while preserving legacy payloads with no embedded production. V4 also consolidates prior local SEO/claim receipt hardening. No frontend commit or deploy.

## Evidence
- Frontend Independence latest observed HEAD: `a42b45e79ef357252509a482e5b9f9f476cd7588`; +10/-3 versus main.
- Exact remote baseline blob SHAs: listing `dda3fb9240367e57b07ec2b8d443d17223994369`, listing test `ecc5a126faff032ef084f9f60fe4eaff07a52124`, SEO `0f9f9b109673cd153db0a39fe207068295a115e4`.
- Nested production regression: original V3 candidate 4/11 pass, exit 1; V4 candidate 11/11 pass, exit 0.
- Re-run V3 acceptance on V4: 34/34 pass; receipt status: 11/11 pass; date/microseconds: 8/8 pass. **64/64 local Node tests pass**, exit 0 in each suite.
- `git apply --check` and disposable application against exact remote blobs: exit 0; output matches candidate.
- JavaScript syntax checks: exit 0.
- Jest React, lint, full build, integrated browser, API checkout: NOT run. Previous CI success is not Independence integration acceptance.
- API Independence diff still contains only request, ownership model and commerce policy; no confirmed migration/controller/routes/checkout gate.

## Requested actions
1. W01/W02: finalize production relation and `app_id` payload contract; enforce policy server-side; test legitimate legacy sales and 403 for unclaimed production.
2. W04/W06: review V4 regression cases, run Jest/build/browser after authorized publication; test 320/360/390/430, verified event + unclaimed production, cross-app production, and checkout authorization.
3. W00: arrange normal authorized publication and explicit handoff for event/production page files. Do not bypass previous `OPENAI_SAFETY_CHECKS` blocks.
4. W05: finalize `source_verified` provenance and SEO indexability contract.

## Constraints
No edits to main, AUX, event/production pages, sitemap or generators. No branch creation, remote code write, merge, deploy, VPS, force push, reset or clean. Previously blocked component/service/test publication NOT retried. CMD-005 untouched. W03 claim remains working.
