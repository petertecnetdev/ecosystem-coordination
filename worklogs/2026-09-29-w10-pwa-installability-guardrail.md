# W10 Worklog — PWA installability guardrail

worker: W10 Visual QA (W10)
date: 2026-09-29
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
status: completed_pending_runtime
pending_deploy_vps: true

## Problems found
- Production VPS `petertecnetserver` is offline, preventing functional Chrome Android/runtime validation.
- PWA installability prerequisites existed across manifest/index/service worker but had no deterministic repository guardrail; regressions could reach main unnoticed.
- Static repository evidence confirms manifest fields and icon declarations, but does not prove intrinsic icon dimensions, service-worker control under HTTPS, `beforeinstallprompt`, or actual Android install behavior.

## Implementation
- Added `scripts/check-pwa-installability.js`.
- Added `npm run smoke:pwa`.
- Guard validates manifest JSON, name/short_name/start_url/scope/display, 192x192 + 512x512 + maskable declarations, local icon existence, manifest link, root service-worker file/registration, and shared install-app manifest wiring.

## Files
- scripts/check-pwa-installability.js
- package.json

## Evidence
- public/manifest.json currently has `start_url: /`, `scope: /`, `display: standalone`, 192x192 and 512x512 declarations and a maskable purpose.
- public/index.html links `/manifest.json`, loads shared `install-app.js`, and registers `/sw.js`.
- public/sw.js exists.
- code commits: cdd1caec22c929a14aa97c5aa1912b677db2c045, 3c00794b4612e50f1e6ce6501a7ec3f10633347e
- claim coordination commits: ee683034096a8148ecdc8ae788d4f1210d2e0da8, ab398f8d9584c6192453e9d2ed6b395590788eb5, c5ea9852533fe1432dcea3a664e1dc31a58097cf

## Tests
- Static review only; GitHub connector has no command runner.
- VPS/runtime tests not executed because petertecnetserver is offline.

## Economic/quality impact
Reduces risk of losing mobile acquisition/activation when a manifest, icon reference, service-worker registration or install integration silently regresses.

## Next
On VPS recovery: sync main; run `npm run smoke:pwa`; verify HTTPS + active service-worker control; inspect icon intrinsic dimensions and maskable safe zone; exercise real Chrome Android installability and `beforeinstallprompt`; only then mark PWA VERIFIED. If Chrome still refuses installation, REOPEN P0 with browser evidence and fix the failing runtime prerequisite rather than showing misleading install instructions.