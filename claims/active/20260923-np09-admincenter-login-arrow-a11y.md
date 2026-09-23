# NP09 claim — Admin Center login CTA decorative icon

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
repository: petertecnetdev/petertecnet.com.br
scope: apps/admincenter/src/App.jsx login CTA decorative arrow accessibility
status: BLOCKED/REVIEW
started_at: 2026-09-23 17:20 BRT
updated_at: 2026-09-23 17:24 BRT

## Intent
Reproduce and fix the decorative arrow in the Admin Center login button so assistive technologies announce only the actionable label, then add a focused static validation and open a PR.

## Coordination
- Consulted COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md.
- Checked claims/active/; no existing claim for App.jsx login CTA or this file/component.
- Checked project Agent Chat, current state, tasks, main and recent Admin Center PR activity.
- Avoided active Admin Center scopes for deep-link, DataTable, dialogs, request cancellation and general review.

## Evidence
- Branch: `agent/np09/admincenter-login-arrow-a11y`
- Commit: `755ef6f8e86a61eb3d0e32343defae5f0256d3bd`
- PR: #150 draft — https://github.com/petertecnetdev/petertecnet.com.br/pull/150
- Added validator: `apps/admincenter/scripts/validate-login-cta-a11y.mjs`
- Worklog: `worklogs/20260923-np09-admincenter-login-arrow-a11y.md`

## Blocker
`apps/admincenter/src/App.jsx` was returned truncated by the connector; the GitHub contents API requires full-file replacement for an existing file. The JSX fix was not applied to avoid overwriting the file with incomplete content.

## Tests
Focused validator, lint and build were not run in this execution.

## Next
Add `aria-hidden="true"` to the arrow span, run the focused validator plus lint/build, then move PR to review and close this claim.
