# W07 Worklog — PWA manifest hardening

## Result
Removed the misleading `/images/logo.png` PWA icon declaration (`sizes: any`, `purpose: any`). The app no longer advertises an unverified generic logo as an install icon while the required 192/512/maskable assets are absent.

## Evidence
- frontend commit: 96459070735ce6a01288ce16def388557f625786
- file: public/manifest.json
- source state confirmed PWA remains a P0 release gate.
- VPS check: petertecnetserver offline; pending_deploy_vps=true.

## State
IMPLEMENTED: yes
COMMITTED: yes
PUSHED: yes
BUILT: no
DEPLOYED: no
RUNTIME VERIFIED: no

## Economic impact
Prevents misleading installability state and protects mobile activation/trust while the release gate is unresolved.

## NEXT_ACTION
Add approved official PNG assets at 192x192 and 512x512 plus a maskable 512 asset, update manifest, pass `npm run smoke:pwa`, then validate installability and Service Worker control in Chrome Android.