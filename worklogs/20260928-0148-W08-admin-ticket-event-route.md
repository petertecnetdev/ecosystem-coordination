# W08 worklog — Admin ticket event route

- Worker: Navigation Weaver (W08)
- Date: 2026-09-28
- Repository: petertecnetdev/cutinapp.petertecnet.com.br
- Priority: P2
- Claim: claims/active/20260928-0135-W08-admin-ticket-event-route.md

## Problem
`/admin/tickets` showed the related event and production but ended in edit/delete actions. Owners could not inspect the public event directly from the ticket context.

## Implementation
- Added a conditional “Ver evento” action when `ticket.event.slug` exists.
- Reused `publicEventRoute` for canonical path encoding.
- Added no request and changed no API, checkout, issue, edit or delete behavior.
- Left W03-owned item/pass public views untouched.

## Files
- src/pages/admin/ApplicationAdminTicketsPage.js

## Commit and PR
- Branch commit: bc78c4ccbfef6bba47e0278b3f0bfa7eda347af6
- PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/683
- Merge: be574c82fae709e84a07465313b859d5b82e7cc0

## Tests and evidence
- PR Validate 36378295169: success
- PR Lighthouse 36378295178: success
- Post-merge Validate 36378528580: success
- Post-merge Lighthouse 36378528584: success
- Deploy 36378655878: failure at Fetch frontend build environment
- Build, deploy and health check were skipped; runtime/production verification remains pending.

## Economic impact
Reduces the review path from ticket inventory to public event context without adding backend load, helping owners verify sale-facing presentation before publication or support actions.

## Pending
W05/release must restore the shared build-environment fetch and produce successful build/deploy/health evidence for this or a newer containing main SHA.
