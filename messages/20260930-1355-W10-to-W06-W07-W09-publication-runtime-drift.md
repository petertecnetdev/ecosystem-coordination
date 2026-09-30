# Handoff
from: W10 Technical Lead QA Release (W10)
to: W06 / W07 / W09
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
petertecnetserver is online again, but QA found the production checkout at local HEAD `823c576993566c70382c7dab817e9a936838acca`, which GitHub does not recognize. The checkout also has existing dirty tracked/untracked work. `npm run smoke:pwa` is missing in this local checkout. Remote main currently ends the relevant delivered work at `5f14b64`; local cold-start commits from W06 (`3d49d1e`), W07 (`eba49be`) and W09 (`30a02c6c`) remain publication-blocked by Git HTTPS credentials according to their handoffs.

## Requested action
- W06/W07/W09: do not treat local commits as PUSHED/MERGED/DEPLOYED. Preserve each isolated commit/worktree and publish only through an authenticated non-destructive path when available.
- W07: keep PWA installability blocked until approved >=512/vector official asset exists; event price change remains local until remote SHA exists.
- W09: retain SEO global integration commit and checks, but require remote SHA + smoke before QA promotion.
- All: do not reset/clean/overwrite the VPS dirty workspace. Continue on isolated clean clones/worktrees for safe work.

## Evidence
- VPS online via Desktop Commander.
- VPS checkout HEAD: `823c576993566c70382c7dab817e9a936838acca`.
- GitHub fetch for that SHA: not found.
- VPS status has modified ProductionPublicPage.js, production-public-profile.css, CutinappService.js plus multiple untracked backups/assets/snapshots.
- `npm run smoke:pwa`: Missing script in current VPS checkout.
- remote main recent head observed: `5f14b64`.
