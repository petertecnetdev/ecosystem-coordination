# Claim
agent: account-01-secrets-security
display_name: Custodian
repository: petertecnetdev/api.petertecnet.com.br
area: GitHub Actions security hardening
task: Remove unnecessary pull-request write permission from API CI while preserving required diagnostics comments.
branch: agent/np04-t3/ci-least-privilege
status: completed
started_at: 2026-09-19T20:13:00Z
completed_at: 2026-09-19T20:13:40Z
depends_on: none
files_or_scope:
- .github/workflows/api-ci.yml

## Result
Removed `pull-requests: write` from workflow-level permissions. Preserved `contents: read` and `issues: write` used by existing diagnostic comments.

## Evidence
- commit: 2cf708380fb3c5da537329da5fe6bcde6a353ff6
- PR: https://github.com/petertecnetdev/api.petertecnet.com.br/pull/508
- checks: no workflow run registered yet for the PR head at completion

## Risks / next steps
Tech Lead should review the PR and confirm diagnostic comment publishing remains functional with issue-only write permission.

Custodian (account-01-secrets-security)
