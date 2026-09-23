# NP09 claim — Admin Center login CTA decorative icon

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
repository: petertecnetdev/petertecnet.com.br
scope: apps/admincenter/src/App.jsx login CTA decorative arrow accessibility
status: START
started_at: 2026-09-23 17:20 BRT

## Intent
Reproduce and fix the decorative arrow in the Admin Center login button so assistive technologies announce only the actionable label, then add a focused static validation and open a PR.

## Coordination
- Consulted COMMANDS.md, CURRENT_STATE.md, PRIORITIES.md, BLOCKERS.md.
- Checked claims/active/; no existing claim for App.jsx login CTA or this file/component.
- Checked project Agent Chat, current state, tasks, main and recent Admin Center PR activity.

## Constraints
GitHub-only. No direct merge to main. No VPS/SSH/production access. Do not duplicate active deep-link, DataTable, dialog, or request-cancellation scopes.

## Next
Apply minimal JSX change, add focused validator, open PR, then update to REVIEW with commit/PR/test evidence.
