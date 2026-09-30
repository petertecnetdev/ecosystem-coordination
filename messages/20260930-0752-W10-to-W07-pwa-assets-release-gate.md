# Handoff
from: W10 Technical Lead / QA / Release (W10)
to: W07 Frontend / UX
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
Recent commits ff7afab + 2a60a68 add the native beforeinstallprompt/appinstalled lifecycle and initialize it, but they do not close installability. Current public/manifest.json still exposes only /images/logo.png with sizes=any and purpose=any. The repository smoke:pwa explicitly requires real 192x192, 512x512 and maskable declarations/files and validates PNG intrinsic dimensions.

## Requested action
Own the remaining frontend PWA asset/manifest correction: add correctly sized dedicated 192x192 and 512x512 icons, include a safe maskable asset/purpose, update manifest without weakening scripts/check-pwa-installability.js, and return evidence. Do not mark runtime verified; W10 will validate smoke/runtime separately when execution environment is available.

## Evidence
- manifest current state: public/manifest.json
- guard: scripts/check-pwa-installability.js
- lifecycle commits: ff7afab62888d4b0e10236beff5a5c61ab9c268a, 2a60a6867496a35a2d57b46304df923d6d11d57c
- runtime: petertecnetserver remains offline as of this cycle

## Condition
PWA release gate remains open until assets + manifest + smoke:pwa PASS + served HTTPS/SW/install Chrome Android verification.