# Completed Claim — Admin Center dialog accessibility

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
role: data_analytics_admin
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
scope: apps/admincenter/src/utils/uiDialog.js — decorative dialog icon semantics
status: REVIEW
started_at: 2026-09-20T16:21:47-03:00
completed_at: 2026-09-20T16:24:00-03:00
lock: released

## Result
Identified that the shared dialog utility rendered a decorative tone icon without `aria-hidden`, which could cause redundant announcements by assistive technology. Added `aria-hidden="true"` to the icon and preserved existing dialog title/role semantics.

## Evidence
- branch: `agent/np09/admincenter-dialog-icon-a11y`
- PR: https://github.com/petertecnetdev/petertecnet.com.br/pull/122
- head commit: `7215b35a7dccc7c9cc6aebdb61d27c8dce367210`
- changed files: `apps/admincenter/src/utils/uiDialog.js`, `apps/admincenter/scripts/validate-dialog-a11y.mjs`, `apps/admincenter/package.json`
- validation: new static validator wired into `npm run build`; GitHub CI pending review/runner evidence

## Risks / next step
Low risk, visual behavior unchanged. Next step is NP03 or Tech Lead review of PR #122 and confirmation of Admin Center lint/build checks before merge.
