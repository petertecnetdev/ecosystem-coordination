# AUX-02 W2 — PWA installability and lifecycle audit

agent: aux-02-w2-frontend-pwa-seo
display_name: PWA Sentinel
date: 2026-10-10
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: AUDIT_COMPLETE / HANDOFF_REQUIRED
main_sha_analyzed: 337c9ba22a4b97f9bd8d48f09b695105a954f43f
assignment_id: W00-20261007-AUX02-W2-PWA-AUDIT
coordination_branch: coord/aux-02-w2-pwa-audit-20261010

## Summary

The manifest now declares the required 192x192, 512x512 and maskable icons, and all three files exist on current main with PNG IHDR dimensions matching their declarations. The release gate is still not verified because the repository's smoke test has not been run and CI does not execute it. The previous duplicate Service Worker registration finding also remains in current main.

## Concrete findings

### P1 — PWA installability guard is not part of required CI

Evidence:
- `.github/workflows/validate.yml` runs npm ci, lint checks, tests, build and perf:budget, but contains no `npm run smoke:pwa` step.
- `package.json` declares `smoke:pwa` as `node scripts/check-pwa-installability.js`.
- `scripts/check-pwa-installability.js` validates manifest fields, 192/512/maskable declarations, PNG dimensions, RGBA/alpha-corner contracts, manifest link and install-app wiring.
- Existing frontend CI check for SHA `337c9ba22a4b97f9bd8d48f09b695105a954f43f` was PASS in run `37878305222`, but the workflow source confirms it does not execute the PWA smoke command.

Impact:
A green frontend CI does not enforce the PWA-specific installability contract. Invalid icon alpha/matte, missing assets, or broken install-app wiring can regress without this gate.

Minimal patch boundary:
Add `npm run smoke:pwa` to `.github/workflows/validate.yml` after `npm ci` and before build. This is within the existing W0 PWA cycle; do not implement a competing app branch.

### P1 — two root-scope Service Worker registrations remain

Evidence:
- `public/index.html` has an inline registration for `/sw.js?v=20261007-pwa-splash-r5` with scope `/`.
- `src/index.js` registers `/sw.js?v=<release bundle hash>` with the same scope `/`.
- `src/index.js` derives the version from hashed static JS/CSS asset URLs.
- The two registrations use different script URLs for the same scope, creating avoidable update checks and cache-version churn.

This finding was already recorded by W2 on 2026-10-08 in `worklogs/20261008-0219-w2-pwa-utm-audit.md`; it is confirmed still present, not claimed as a new issue. Keep the fix within the active W0/W2 lifecycle scope.

### Asset header verification

Fetched current main assets and read PNG IHDR:
- `public/pwa-icon-192.png`: 192x192, bit depth 8, color type 6 (RGBA), non-interlaced.
- `public/pwa-icon-512.png`: 512x512, bit depth 8, color type 6 (RGBA), non-interlaced.
- `public/logo512-maskable.png`: 512x512, bit depth 8, color type 6 (RGBA), non-interlaced.

All three file paths resolve from current main. Alpha-corner values, full PNG integrity and the complete `smoke:pwa` result remain UNVERIFIED because no repository command runner is available through this connector.

## Runtime / mobile status

No real HTTPS runtime or Chrome Android install test was run. Hamburger/logo behavior at 320/360/390/430 px remains owned by the active W0/W3/W4 mobile-nav cycle. Do not mark runtime verified from source inspection or CI alone.

Current coordination state says the icons are still absent; that statement is stale relative to the inspected main SHA. Update the global PWA gate to: assets present with matching IHDR dimensions; alpha/smoke/runtime still unverified; CI currently omits smoke:pwa.

## Files changed in application

None.

## Tests

- Static source inspection: completed.
- PNG IHDR verification: completed for all three assets.
- `npm run smoke:pwa`: NOT EXECUTED.
- Jest/build/Lighthouse/mobile viewport/browser install tests: NOT EXECUTED in this audit.
- Production/runtime: NOT VERIFIED.

## Git

- Application branch/commit/PR: none; no application code changed.
- Coordination branch: `coord/aux-02-w2-pwa-audit-20261010`.
- Coordination claim: `claims/active/20261010-1010-aux-02-w2-pwa-ci-registration-audit.md`.
- Assignment status update was blocked by connector safety checks; W2 assignment file remains unchanged on main and requires W00 reconciliation.

## Economic impact

This gate protects mobile acquisition and repeat attendance: PWA install/update failures can reduce return visits and make tickets/QR less dependable on mobile. No conversion lift is claimed without runtime and funnel data.

## Next action

1. W00/W1/W2: run `npm run smoke:pwa` in the active W0 cycle and inspect alpha-corner/maskable results.
2. W00/W2: consolidate Service Worker registration to one authoritative point and extend a regression check to reject duplicate registrations.
3. W00/W4: validate HTTPS control, update/offline behavior and Chrome Android installation; run mobile navigation at 320/360/390/430 px.
4. W00: reconcile stale PWA status in `CURRENT_STATE.md` after evidence is attached.
