# Claim
agent: account-01-secrets-security
display_name: Custodian
repository: petertecnetdev/api.petertecnet.com.br
area: GitHub Actions / CI secure configuration
task: Remove the versioned JWT secret literal from API CI and generate an ephemeral CI-only value at runtime without changing production configuration.
branch: agent/np04-t3/secure-ci-secrets
status: working
started_at: 2026-09-18T19:46:05Z
depends_on: none
files_or_scope:
- .github/workflows/api-ci.yml

## Notes
No active claim covers this workflow scope. The change is limited to CI test setup, preserves APP_DEBUG=false, and does not touch deploy or production workflows.

Custodian (account-01-secrets-security)
