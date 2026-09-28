# Worklog — W01 Production owner action hierarchy

agent: ViewForge (W01)
date: 2026-09-27T22:08:00-03:00
repository: petertecnetdev/cutinapp.petertecnet.com.br
scope: authenticated Production public header actions

## Inventory
The reusable public Production header still offered the social Follow control to the production owner while management was reduced to an unlabeled edit icon. That weakens the owner state and mixes social and administrative actions.

## Implementation
- owner now sees a visible `Editar produção` secondary action in the same compact action grid;
- owner no longer receives Follow/Following for their own production;
- anonymous and authenticated non-owner visitors retain the existing follow/unfollow flow;
- regression guard now covers the visible owner edit action and owner/follow branch ordering.

## Files
- `src/pages/production/ProductionPublicPage.js`
- `scripts/check-production-view-regression.js`

## Evidence
- application main: `f4feea62cf3a6f78db11b48226837f7e5904b470` (includes `c6d56238`)
- remote content blobs exactly match locally validated files
- production view guard: 31/31
- overlays: passed
- dialogs: passed
- React stability: passed
- UX/performance guard: passed
- production build: compiled, 18 SEO snapshots
- tests: 138 suites / 851 tests passed
- GitHub Validate Cutinapp #2857: passed
- GitHub Lighthouse CI #769: passed

## Release
Deploy VPS #1751 started after Validate #2857 passed, but failed before build/deploy/health because the GitHub runner could not reach the VPS SSH endpoint. Public HTTPS still served `99fe15cb9b035804f1eee7b5ab6ad336875eeff7` after the failure, so W01-009 is IMPLEMENTED but not runtime VERIFIED.

## Economic impact
A clearer owner management action reduces friction for producers maintaining public pages, while preserving the visitor conversion path for agenda/tickets/follow/share.

## Next action
Restore the release transport, publish `f4feea62` or newer, then validate anonymous, non-owner authenticated and owner states at 390/1366/1920.
