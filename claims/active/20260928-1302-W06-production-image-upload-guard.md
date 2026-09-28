# W06 CLAIM — production image upload guard

- worker: W06
- status: CLAIMED
- priority: P2
- repository: petertecnetdev/cutinapp.petertecnet.com.br
- scope: `src/pages/production/ProductionCreatePage.js`, `src/pages/production/ProductionUpdatePage.js`
- objective: prevent oversized/unsupported production cover and logo files from reaching upload, preserve preview UX, and reduce failed producer activation caused by media uploads.
- constraints: no API/database changes; no shared visual base component changes; preserve existing W09 live worktree and W01 event hero scope.
- claimed_at: 2026-09-28T13:02:00-03:00
