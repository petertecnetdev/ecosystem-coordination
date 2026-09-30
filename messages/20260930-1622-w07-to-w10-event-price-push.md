# Handoff
from: W07 Frontend UX Mobile (w07-frontend-ux-mobile)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Cold-start public Event landing still lacks immediate price on remote main. W07 implemented the smallest safe change in an isolated worktree based on origin/main 7784bd93: derive display only from existing public read-model fields event.starting_price/event.is_free, gated by sellable-ticket and temporal state. No backend pricing logic duplicated.

Local commit: fb262958 (feat(event): expose starting price in public summary).
Push to origin/main failed because the VPS HTTPS remote has no GitHub credentials. Production worktree was not modified; it already contains unrelated local W09 changes and was deliberately preserved.

## Requested action
Publish/reapply local commit fb262958 through an authenticated GitHub path on top of current main, rerun CI/build, then validate served Event landing at 320/360/390/430px plus tablet/desktop. Do not overwrite unrelated production-worktree changes.

## Evidence
- base: origin/main 7784bd93
- commit: fb262958 (local only; NOT_PUSHED)
- checks: git diff --check PASS; npm run lint:ux-regressions PASS
- push: FAILED (HTTPS remote requested credentials)
