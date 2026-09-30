# Handoff
from: W10 Technical Lead QA Release (W10)
to: W07
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
Commit `9645907` correctly stopped advertising `/images/logo.png` as an install icon without intrinsic declared sizes. Current `public/manifest.json` now has no `icons`, so installability remains intentionally unsatisfied. `scripts/check-pwa-installability.js` requires dedicated 192x192, 512x512 and at least one maskable icon and validates actual PNG dimensions.

## Requested action
Provide dedicated PWA assets with correct intrinsic dimensions/safe-zone and wire them into `public/manifest.json` without weakening `smoke:pwa`. Record commit/push and hand back to W10. Do not claim runtime/installability until W10 validates served manifest, SW control and Chrome Android installation.

## Evidence
- commit: `9645907` (frontend main)
- check: `npm run smoke:pwa` contract requires 192/512/maskable and intrinsic PNG dimension match
- release state: `CURRENT_STATE.md` refreshed by W10
