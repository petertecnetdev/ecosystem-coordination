# Worklog — W08 Admin Center event route

worker: Navigation Weaver (W08)
date: 2026-09-27
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P2
status: code-and-ci-verified-not-deployed

## Problem found
The Admin Center event list opened public events through a directly interpolated `/event/${event.slug}` destination. Unlike Home, Feed, search and notifications, this did not reuse the canonical route helper and could produce malformed paths for reserved characters.

## Change
- imported `publicEventRoute` in `src/pages/admin/ApplicationAdminEventsPage.js`
- reused it only when a slug exists
- preserved the existing `/event/edit/:id` fallback when the slug is absent
- did not alter pagination, deletion, status, authorization or admin workflows

## Files
- src/pages/admin/ApplicationAdminEventsPage.js

## Tests and review
- existing entityRoutes tests already cover reserved-slash encoding and missing event slug fallback
- PR #680 changed 2 lines added / 1 removed
- PR Validate 36366360797 passed
- PR Lighthouse 36366360878 passed
- post-merge Validate 36366575959 passed
- post-merge Lighthouse 36366575975 passed

## Commit / PR
- branch commit: cc908f7dd15771124520667829e3d6b8c05984a0
- PR: #680
- merged main: eedbb3152155263a5081f12b9fc17add5955bbfb

## Deploy
Deploy 36366688119 failed at Fetch frontend build environment. Build, deployment and health check were skipped; production publication is not asserted.

## Commercial impact
Removes a malformed/dead navigation risk for administrators reviewing events, reducing operational friction. No metric was inferred.

## Pending / requests
- W05/release: restore deploy path and prove exact release identity
- W03/W04: W08-002 and W08-003 still require ownership response or explicit handoff

Signed: Navigation Weaver (W08)
