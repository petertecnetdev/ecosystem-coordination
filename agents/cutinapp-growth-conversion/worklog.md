# Worklog — Cutinapp Conversion & Onboarding

## 2026-09-26 — Issue #645
Implemented and merged one-click flyer-grounded descriptions for events and productions, plus safe structured rich editing and public rendering.

Evidence:
- API PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/527
- API merge: b391bd44a28d007dff99dc538101135b259de7ed
- Frontend PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/648
- Frontend merge: c8519896cbe8034987902799906ec14a52ee7d79
- Issue: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/issues/645
- Frontend checks: Validate Cutinapp #2696 success; Lighthouse #608 success
- API new tests: 2/2 passed; full-suite baseline remains red outside this scope

Next: verify main-to-production deploy identity and run a real producer smoke test using a flyer with conflicting values.

Conversion Pilot (cutinapp-growth-conversion)

### Deploy follow-up
- Frontend PR #649 fixed the independent invalid-template-literal build blocker; both PR checks passed and it merged as `08b5407a355f880330d2a9d54f0d113a53b45b72`.
- Deploy run 36271310572 completed build and artifact activation, but exact-SHA health verification failed: the filesystem contains `08b5407…`, while local nginx and public HTTPS still serve `5a247f…`.
- No duplicate infrastructure implementation was started because deterministic release serving is already claimed by `cutinapp-revenue-core`. Evidence was added to the production/stability handoff.

## 2026-09-26 — Flyer date consistency guard
Implemented and merged the owner-priority protection against incorrect dates printed on event and production flyers.

Delivered:
- recurring production guidance to use weekday only and avoid fixed dates;
- locale/timezone-aware flyer date analysis with safe classifications;
- producer-controlled remove/replace correction with original/proposed preview and explicit confirmation;
- preserved original artwork and no silent production correction;
- idempotent queued audit records, review statuses and minimal telemetry;
- tests for recurrence, ambiguity, no date and timezone boundaries.

Evidence:
- API PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/531
- API merge: `9bf5a48df83b32b331da8773b51f4b34348aac9a`
- Frontend PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/657
- Frontend merge: `8629c9193bee804616d10182552e84d26dd5dd49`
- Frontend tests: 10/10; production build passed
- Frontend PR Validate #2763 and Lighthouse #675: passed
- Frontend main Validate #36280554146 and Lighthouse #36280554162: passed
- API focused tests: 5/5; syntax/migrations/routes/new-controller architecture gates passed
- API full suite: 37 unrelated pre-existing baseline failures remain

Release:
- Deploy run https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36280644821 activated the expected SHA on filesystem and local nginx.
- Public HTTPS still serves `5a247f…`, so production is not claimed.
- Edge/proxy blocker and diagnostic-workflow heredoc defect recorded in `handoffs/20260926-2352-cutinapp-flyer-date-edge-release-blocker.md`.


### Release diagnostic follow-up
- PR https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/658 fixed the malformed diagnostic heredoc and merged as `f14e648cb5501f998b9b9837605ef3abb2021c92`.
- PR frontend and Lighthouse checks passed; main Validate run 36282864463 passed.
- Deploy run 36282954294 activated `f14e648c…` successfully on the filesystem and local nginx.
- The repaired diagnostic proved public HTTPS still serves `5a247f…`, while cloudflared is inactive and its executable is absent on the configured VPS.
- Action-required handoff: `messages/20260927-0039-cutinapp-growth-conversion-to-production-stability-edge-origin.md`.
- Production remains unconfirmed until public `release-sha.txt` equals current main.
