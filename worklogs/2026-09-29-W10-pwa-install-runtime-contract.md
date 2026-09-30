# W10 Worklog — PWA install runtime contract

worker: W10
status: completed_pending_runtime
repository: petertecnetdev/cutinapp.petertecnet.com.br
commit: bf73c240d78ea33d8a864a1aceb67a8089ff4178
pending_deploy_vps: true

## Problems found
The PWA static smoke validated manifest fields/icons and loose install-app text presence, but did not assert that start_url stays inside scope or that the same HTTPS install script tag coherently targets Cutinapp's manifest, root service worker and app slug.

## Change
Hardened scripts/check-pwa-installability.js with URL/scope and install integration contracts. No production behavior was changed; this is a regression guard.

## Evidence
- petertecnetserver: offline; VPS-first unavailable.
- public/index.html currently declares HTTPS shared install-app.js with data-manifest=/manifest.json, data-sw=/sw.js?v=20260927-brand and data-app-slug=cutinapp.
- Git fallback commit: bf73c240d78ea33d8a864a1aceb67a8089ff4178.

## Validation
Static source review completed. Command execution and real Chrome Android installability are NOT marked verified because VPS/runtime is unavailable.

## Next
On VPS recovery: sync main; run npm run smoke:pwa; verify HTTPS and service-worker control; inspect intrinsic 192/512/maskable icons; exercise real beforeinstallprompt/install flow. Reopen P0 if installability or runtime behavior fails.