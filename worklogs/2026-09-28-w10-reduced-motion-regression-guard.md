# W10 Worklog — reduced-motion regression guard

worker: W10 Visual QA
when: 2026-09-28T22:10:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br
flow: Git fallback because petertecnetserver is offline

## Problems found
- `src/styles/global.css` already has a strong global `prefers-reduced-motion: reduce` contract.
- `npm run lint:ux-regressions` only checked newly added JS/React anti-patterns and did not protect that accessibility contract from future removal/weakening.

## Implementation
- Extended `scripts/check-ux-regressions.js` to fail when the global reduced-motion media query is absent.
- The guard also requires smooth scrolling to be disabled, animation duration effectively disabled, animation loops capped to one, and transitions effectively disabled.
- Existing architecture checks remain intact.

## Files
- scripts/check-ux-regressions.js
- agents/cutinapp-visual/workstreams/W10.json (coordination only)

## Evidence
- code commit on main: `2e0db0c3cba8b5276c0897c3a7aab46fa6b75c02`
- VPS status: offline; last observed agent status unavailable for runtime execution in this cycle.
- No performance thresholds were relaxed.

## Tests
- Static source inspection confirms current `src/styles/global.css` contains all contracts checked by the new guard.
- Command execution/build/runtime smoke could not be performed through the GitHub contents fallback because it has no command runner.

## Deployment
pending_deploy_vps: true
restart: not performed
build: pending VPS/runner

## Pending
- Sync/reconcile main on VPS when it reconnects.
- Run `npm run lint:ux-regressions`, applicable build/performance/smoke checks, and browser accessibility verification.
- Reopen W10-008 if the executable guard or runtime behavior fails.

## Requests
- W05: continue deployment/release recovery so pending Git-fallback commits can be validated in production.
