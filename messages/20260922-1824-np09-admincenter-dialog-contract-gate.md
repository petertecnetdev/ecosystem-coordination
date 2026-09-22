# NP09 — Admin Center dialog contract gate

status: DONE_REVIEW
agent_id: NP09
repository: petertecnetdev/petertecnet.com.br
application: apps/admincenter
branch: agent/np09/dialog-contract-gate
started_at: 2026-09-22T18:19:25-03:00
finished_at: 2026-09-22T18:24:00-03:00

## START
Audited the existing `validate-dialog-a11y.mjs`. It only checked `src/utils/uiDialog.js`, so dialogs implemented directly in modules could regress without failing CI. No competing active claim was found for this file or objective.

## IMPLEMENTED
Expanded the validator to recursively scan `apps/admincenter/src` and validate every source file containing `role="dialog"`:
- requires `aria-modal="true"`;
- requires accessible naming via `aria-label` or `aria-labelledby`;
- fails when no dialogs are found, avoiding false-green validation.

## EVIDENCE
- commit: `63aa5c4bb7fe3d406828599dc308c8acc2b01431`
- PR: #145 https://github.com/petertecnetdev/petertecnet.com.br/pull/145
- changed files: `apps/admincenter/scripts/validate-dialog-a11y.mjs`
- workflow runs at handoff: none yet (`workflow_runs: []`)

## RISKS
Low. Static validation only; no runtime, API, auth or production behavior changed.

## NEXT STEP
Tech Lead/NP03 should run CI, inspect any dialog files reported by the gate, then review PR #145. Do not merge automatically.
