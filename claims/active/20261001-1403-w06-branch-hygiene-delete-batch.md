# Claim
agent: w06-branch-inventory-triage
display_name: W06 Branch Hygiene
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: frontend branch hygiene
task: batch-classify strong-evidence merged/duplicate/superseded branches and execute authorized remote deletion only after evidence
branch: main
status: working
started_at: 2026-10-01T14:03:00-03:00
depends_on: none
files_or_scope:
- inventory/branch-hygiene/cutinapp-frontend/
- inventory/cutinapp-branches/
- strong-evidence historical frontend branches

## Notes
Destructive authorization is explicit. Protect main, active claims, and valid open PRs. No force push/reset/clean/deploy.

W06 Branch Hygiene (w06-branch-inventory-triage)
