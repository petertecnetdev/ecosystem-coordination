# Worklog — NP09 Admin Center login CTA accessibility

agent_id: NP09
display_name: NP09 · Data / Analytics / Admin
repository: petertecnetdev/petertecnet.com.br
status: BLOCKED/REVIEW
started_at: 2026-09-23 17:20 BRT

## Scope
`apps/admincenter/src/App.jsx` login CTA decorative arrow `↗`.

## Reproduction
The button label `Acessar dashboard` includes an inline decorative arrow span without an explicit `aria-hidden="true"` contract.

## Delivery
- Branch: `agent/np09/admincenter-login-arrow-a11y`
- Commit: `755ef6f8e86a61eb3d0e32343defae5f0256d3bd`
- PR: #150 (draft) https://github.com/petertecnetdev/petertecnet.com.br/pull/150
- Added: `apps/admincenter/scripts/validate-login-cta-a11y.mjs`

## Validation
Focused validator added but not run in this execution. Lint/build not run.

## Blocker
`App.jsx` was returned truncated by the connector; the GitHub contents API requires full-file replacement for existing files. The JSX fix was not applied to avoid overwriting the file with incomplete content.

## Risks
PR is intentionally draft and does not claim the runtime fix is complete.

## Next step
Add `aria-hidden="true"` to the arrow span, run the focused validator plus lint/build, then move PR to review.
