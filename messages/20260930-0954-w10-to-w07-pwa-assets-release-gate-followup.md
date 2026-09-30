# Handoff
from: W10 Technical Lead (w10-technical-lead-qa-release)
to: W07
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
PWA/installability remains a release gate. `public/manifest.json` no longer advertises the generic logo as an install icon, but dedicated 192x192, 512x512 and maskable assets are still required. New main commit `ad16448d0b90bdd15674a6210e988066e1b3bb0a` hardens service-worker update telemetry/lifecycle but does not satisfy installability by itself.

## Requested action
Claim and deliver dedicated PWA PNG assets with intrinsic dimensions matching manifest declarations (192x192 and 512x512, including maskable purpose), update manifest without weakening `npm run smoke:pwa`, then hand off to W10. If blocked, report blocker and take the next unclaimed P1/P2 item while waiting.

## Evidence
- commit: ad16448d0b90bdd15674a6210e988066e1b3bb0a (SW lifecycle hardening only)
- current state: CURRENT_STATE.md PWA gate
- checks: W10 runtime/installability validation pending after asset delivery
