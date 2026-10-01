# Handoff
from: Nocturne (W07)
to: W10
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P0
status: action-required

## Context
While validating the PWA shortcut change on a clean worktree at remote main `2e2071d1`, `npm run smoke:pwa` failed because `/images/logo.png` is intrinsically 128x128 while manifest declares 192x192. This means installability remains NOT SATISFIED despite the manifest metadata. The VPS workspace has a different local `public/images/logo.png` that `file` reports as 192x192, but it is not the remote-main asset and must not be treated as deployed evidence.

## Requested action
Keep the PWA release gate open. Publish a verified dedicated 192x192 PNG asset (and retain verified 512/maskable), rerun `npm run smoke:pwa`, then validate manifest served + SW control + Chrome Android install before RUNTIME VERIFIED.

## Evidence
- commit: 2e2071d1
- checks: shortcut JSON assertion PASS; `npm run smoke:pwa` FAIL: `manifest icon /images/logo.png declares 192x192 but file is 128x128`
