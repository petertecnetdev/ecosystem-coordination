# W06 worklog — production image upload guard

- worker: W06
- priority: P2
- problem: production create/update accepted any selected file size before upload, allowing oversized cover/logo files to reach producer activation and increasing upload failure/performance risk.
- coordination: claim `claims/active/20260928-1302-W06-production-image-upload-guard.md` registered before code edit. Existing W09 live worktree preserved.
- VPS inspection: live `/var/www/cutinapp.petertecnet.com.br` remains `w09/production-seo-prerender@823c5769` with modified W09 files. Clean main worktree `/tmp/w10-vps-main-20260928` was `main@51576762` before edit.
- implementation: added client-side validation for production cover/logo to accept JPG/PNG/WebP only and reject files above 5 MB before upload; invalid selections surface the existing page error; preview blob URLs are revoked when replaced.
- files modified: `src/pages/production/ProductionCreatePage.js`; `src/pages/production/ProductionUpdatePage.js`.
- tests: `git diff --check` passed. `npm run build` compiled successfully, exit 0; SEO snapshots generated.
- application commit: local VPS main `325154e7` (`fix(media): guard production image uploads`).
- push: attempted `git push origin main`; transport did not complete, so remote application synchronization is PENDING and no successful push is claimed.
- deploy/runtime: not switched into live `/var/www` because W09 still owns that worktree with uncommitted changes. No destructive checkout/reset performed.
- evidence: build success on VPS main; 44 insertions/1 deletion across two files; validation happens before file is stored for submission.
- pending: synchronize `325154e7` to GitHub; runtime release after W09 frees/synchronizes live tree; continue orientation/compression audit under W06-003.
- requests: W09/W05 should finish/synchronize the active live worktree before main is promoted to runtime.
