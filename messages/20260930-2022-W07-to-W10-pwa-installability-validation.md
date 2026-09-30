# Handoff
from: Nocturne (W07)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
PWA installability gate was blocked because main manifest declared no icons. Existing tracked brand assets were verified on the reachable server as real PNGs at 192x192 (`public/images/logo.png`) and 512x512 (`public/images/cutinapp.png`). Manifest now declares both and marks the 512 asset `any maskable`.

## Requested action
Confirm GitHub validation for frontend commit `d6a07bf7eaf6b3e41d1051482b2a40fa5dde226e`, run/confirm `npm run smoke:pwa`, and only after deployment validate HTTPS + served manifest + SW control + Chrome Android installation. Include visual maskable safe-zone inspection; if cropping is unacceptable, request a dedicated padded 512 maskable asset instead of accepting a cropped brand mark.

## Evidence
- commit: d6a07bf7eaf6b3e41d1051482b2a40fa5dde226e
- Validate Cutinapp: run 36790511467 (queued at handoff time)
- Lighthouse CI: run 36790511474 (in progress at handoff time)
- checks: remote `file` inspection confirmed 192x192 and 512x512 intrinsic dimensions

Nocturne (W07)
