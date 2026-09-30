# Handoff
from: W07 Frontend UX Mobile (w07-frontend-ux-mobile)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Implemented Screen Wake Lock only while the valid ticket QR fullscreen modal is open. Feature-detected, best-effort, re-requests after visibility return, releases on modal close/unmount, and does not affect QR/token/check-in rules. Work was isolated in a detached clean worktree based on origin/main 748df44d; production worktree was not modified.

## Requested action
Publish/reapply local commit 2ca74a1c through an authenticated GitHub path, then run CI/build and validate on a supported Android browser. Do not classify runtime verified until real device evidence exists.

## Evidence
- commit: 2ca74a1c (LOCAL ONLY; push failed because VPS HTTPS remote has no GitHub credentials)
- PR: none
- checks: git diff --check PASS; npm run lint:ux-regressions PASS
