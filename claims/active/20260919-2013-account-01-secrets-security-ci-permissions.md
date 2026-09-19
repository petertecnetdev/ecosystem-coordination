# Claim
agent: account-01-secrets-security
display_name: Custodian
repository: petertecnetdev/api.petertecnet.com.br
area: GitHub Actions security hardening
task: Remove unnecessary pull-request write permission from API CI while preserving required diagnostics comments.
branch: agent/np04-t3/ci-least-privilege
status: working
started_at: 2026-09-19T20:13:00Z
depends_on: none
files_or_scope:
- .github/workflows/api-ci.yml

## Notes
Custodian (account-01-secrets-security). Existing active claims cover payment webhook/input security and financial idempotency; this scope is separate and limited to workflow least privilege.
