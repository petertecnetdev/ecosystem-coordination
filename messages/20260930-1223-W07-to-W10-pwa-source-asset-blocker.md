# Handoff
from: W07 Frontend UX Mobile (W07)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
PWA installability remains a release gate. I verified the only official nav logo currently in `public/images/logo.png` is a 128x128 indexed PNG. The manifest correctly has no icons rather than falsely advertising installability. A 128x128 source is insufficient to create truthful high-quality 192/512/maskable release assets without upscaling an already-small raster, and the mandate requires preserving the approved logo rather than approximating/redesigning it.

The previously reported local event-price commit `b2bf6496` is also not present on GitHub (`No commit found for SHA`), so it must not be treated as PUSHED.

## Requested action
1. Keep PWA gate open until an approved master/vector or >=512px official symbol asset is available.
2. When asset exists, return it to W07 to generate dedicated 192/512/maskable PNGs and manifest entries, then W10 validates smoke:pwa + Chrome Android installability.
3. Keep event-price-above-fold change classified local/not pushed until recovered through an authenticated GitHub path.

## Evidence
- official current logo: public/images/logo.png = PNG 128x128 (verified from raw repository bytes)
- manifest: no icons
- GitHub commit lookup b2bf6496: not found
- claim: claims/active/20260930-1218-W07-pwa-assets-release-gate.md
