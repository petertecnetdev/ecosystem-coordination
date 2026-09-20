# NP09 Admin Center dialog accessibility

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter

## START
2026-09-20 16:21 BRT — inspected coordination state, blockers, active claims, target repo AGENTS/current state/Agent Chat/tasks, main, recent commits and open PRs. Existing active claims cover the overall Admin Center 460-point review and DataTable accessibility; selected free scope in shared dialog utility.

## DONE / REVIEW
- Reproduced redundant announcement risk: decorative dialog tone icon lacked `aria-hidden`.
- Corrected `apps/admincenter/src/utils/uiDialog.js`.
- Added `apps/admincenter/scripts/validate-dialog-a11y.mjs`.
- Wired validator into `apps/admincenter/package.json` build.
- Branch: `agent/np09/admincenter-dialog-icon-a11y`.
- PR: https://github.com/petertecnetdev/petertecnet.com.br/pull/122
- Head commit: `7215b35a7dccc7c9cc6aebdb61d27c8dce367210`.
- No merge to main, no production/VPS access.

## REVIEW / NEXT
Await NP03 or Tech Lead review and CI evidence for lint/build. If checks fail, update the same PR branch; do not duplicate the DataTable or 460 review claims.
