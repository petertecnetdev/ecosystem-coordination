# Worklog — W06 MediaForge

worker: W06 — MediaForge
status: completed_pending_deploy_vps
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problems found
- `eventPoster` limited source bytes to 30 MB but did not constrain decoded dimensions/pixel count before canvas normalization.
- A highly compressed but extremely large image could therefore create avoidable browser memory/CPU pressure during flyer editing.
- VPS `petertecnetserver` was offline, so production/runtime validation was unavailable.

## Worked points
- Added explicit source guards of 12,000 px maximum per side and 60 megapixels maximum decoded area.
- Guard runs after dimensions are available and before 1024×1536 canvas normalization.
- Existing JPG/PNG/WebP, 30 MB source limit, 5 MB output limit and 2:3 normalization remain unchanged.

## Files modified
- `src/utils/eventPoster.js`

## Tests / evidence
- GitHub commit patch reviewed: 9 additions, 1 deletion; only `src/utils/eventPoster.js` changed.
- No VPS build/runtime test claimed because device is offline.
- pending_deploy_vps: true

## Commit / push
- application main: `788d45e4a394623c60e931ab88f4dd7714963ecc` — `fix(media): guard oversized poster pixel sources`
- Push is implicit in GitHub contents write to main; commit is present remotely.

## Deploy/restart
- Not performed; VPS offline.

## Economic/UX impact expected
- Reduces risk of browser freezes/crashes during producer event activation, protecting the create/publish funnel from pathological image uploads.

## Pending
- On VPS return: fetch main without overwriting concurrent work; run build; test normal poster and oversized-dimension rejection; deploy only after runtime validation.

## Requests
- W05: keep W06-011 marked pending_deploy_vps until VPS revalidation succeeds.
