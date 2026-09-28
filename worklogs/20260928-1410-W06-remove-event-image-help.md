# W06 Worklog — event image help cleanup

worker: W06
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P2
status: BUILD_VERIFIED_PENDING_PUSH_RUNTIME

## Problems found
- Event creation still rendered the persistent message: “Qualquer imagem pode ser ajustada. A Cutinapp converte para 1024 × 1536 px (2:3) antes do envio. JPG, PNG ou WebP, até 5 MB.”
- The message duplicated editor behavior and occupied valuable top-of-form space.
- Live `/var/www/cutinapp.petertecnet.com.br` remains on `w09/production-seo-prerender@823c5769` with W09 uncommitted changes.
- VPS `main` worktree is ahead of `origin/main`; HTTPS push still does not complete.

## Points worked
- W06-009: remove redundant persistent event image help while preserving the media pipeline.

## Files modified
- `src/pages/event/EventCreatePage.js`
- `src/utils/eventPoster.js`

## Implementation
- Removed `imageHelp={EVENT_POSTER_HINT + ...}` from the create-event surface.
- Removed the now-unused `EVENT_POSTER_HINT` import/export.
- Did not alter `EVENT_POSTER_WIDTH=1024`, `EVENT_POSTER_HEIGHT=1536`, ratio validation, normalization, crop/editor, compression, or supported MIME validation.

## Tests
- `git diff --check`: PASS.
- Exact message grep after edit: no match.
- 1024/1536 constants verified intact.
- `npm run build`: PASS, exit 0; SEO snapshots generated.

## Commit / push
- Local VPS main commit: `91067e47 fix(media): remove redundant event image help`.
- Push attempted with bounded timeout; Git HTTPS transport did not complete. Remote synchronization remains pending.

## VPS evidence / deploy
- Implementation and production build executed on VPS main worktree `/tmp/w10-vps-main-20260928`.
- Runtime was not replaced because the live tree is actively owned by W09 and contains uncommitted work; no reset/checkout/destructive overwrite performed.

## Pending
- Synchronize VPS main commits to GitHub when transport is available.
- After W09 releases the live tree, deploy/switch safely and verify the create-event surface in runtime.

## Requests
- request_for=W09/W05: finish/synchronize live worktree ownership before runtime release from main.
