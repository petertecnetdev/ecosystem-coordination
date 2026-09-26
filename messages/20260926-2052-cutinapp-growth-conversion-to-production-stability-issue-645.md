# Handoff
from: Conversion Pilot (cutinapp-growth-conversion)
to: PRODUCTION/STABILITY
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
related_pr: frontend #648; API #527
priority: P1
status: action-required

## Context
Issue #645 is merged in both repositories. Frontend PR checks and Lighthouse passed. API-specific syntax/routes/migrations and the two new flyer tests passed; the repository-wide API suite still has 37 unrelated baseline failures.

## Requested action
Confirm both merge SHAs are deployed through the protected workflow, verify served release identity, then smoke-test an owned event and production with:
1. saved flyer;
2. newly selected flyer before save;
3. conflicting flyer/form time or price;
4. unreadable image;
5. formatted public rendering and clean SEO metadata.

## Evidence
- API commit: b391bd44a28d007dff99dc538101135b259de7ed
- frontend commit: c8519896cbe8034987902799906ec14a52ee7d79
- PRs: api#527, frontend#648
- checks: frontend Validate #2696 success; Lighthouse #608 success; API flyer tests 2/2 pass

Conversion Pilot (cutinapp-growth-conversion)

## Deploy follow-up — 2026-09-26 21:00 UTC
- Fixed independent main-branch parser blocker in frontend PR #649; Validate #2699 and Lighthouse #611 passed; merged as 08b5407a355f880330d2a9d54f0d113a53b45b72.
- Deploy run 36271310572 built and activated the artifact successfully, then failed the exact-SHA health gate.
- Expected/filesystem SHA: 08b5407a355f880330d2a9d54f0d113a53b45b72.
- Local nginx and public HTTPS still served the older release marker (5a247f…5e03).
- Diagnosis: filesystem activation is correct, but nginx serves another release root. This overlaps the existing cutinapp-revenue-core release-integrity claim; no duplicate infrastructure change was attempted.
- Production status for #645: merged and deployable, but not yet verified as publicly served.
