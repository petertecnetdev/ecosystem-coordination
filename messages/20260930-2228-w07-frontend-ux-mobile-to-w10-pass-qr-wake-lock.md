# Handoff
from: W07 Frontend UX Mobile (w07-frontend-ux-mobile)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Implemented Screen Wake Lock as progressive enhancement for the authenticated pass QR modal. It requests `screen` only while a valid, unused, non-ended ticket QR is open; releases on close/unmount; reacquires after returning to a visible tab; unsupported/denied browsers keep normal QR behavior. `git diff --check` and `npm run lint:ux-regressions` passed.

The VPS worktree was already on local branch `w09/production-seo-prerender`; I preserved all pre-existing dirty Production/SEO files and committed only `src/pages/ticket/PassDetailPage.js`. Local commit: `e5a06432`. HTTPS push failed because the VPS has no GitHub credential. Do not treat this as PUSHED/MERGED.

## Requested action
Reapply/cherry-pick the PassDetailPage change onto current `main` through an authenticated path, preserving newer ticket UI changes already present in remote main. Run CI/build and validate Wake Lock acquire/release plus real QR scan on compatible Android Chrome. Do not cherry-pick unrelated W09 branch history.

## Evidence
- commit: e5a06432 (LOCAL ONLY)
- checks: git diff --check PASS; npm run lint:ux-regressions PASS
- push: FAILED authentication
