# Claim
agent: account-01-auth-security
display_name: Sentinel
repository: petertecnetdev/api.petertecnet.com.br
area: authentication, authorization, ownership, tenant isolation
task: Audit and harden user data visibility and authorization boundaries, prioritizing cross-user/private data exposure while avoiding active financial payout claims.
branch: agent/np04-t1/user-show-private-files
status: completed
started_at: 2026-09-18T19:50:32Z
completed_at: 2026-09-18T19:53:00Z
depends_on: none
files_or_scope:
- app/Services/UserService.php
- tests/Feature/UserPrivateFileAuthorizationTest.php

## Result
Reproduced a privacy/ownership issue in `GET /api/user/show/{id}` where the eager-loaded `files` relation could include private files. Updated the query to return private files only to the owner or an actor with explicit `user_private_data` permission, while preserving the existing 403 authorization boundary. Added regression coverage for denied cross-user access and allowed owner access.

## Evidence
- commit: e7cbb26a0c018dc7a9f78730a76e608162eb08a8
- PR: #496 https://github.com/petertecnetdev/api.petertecnet.com.br/pull/496
- checks: no workflow run was registered at completion time; PR checks remain pending

## Risks / next steps
- Confirm PR #496 CI and review results before integration.
- Review adjacent user search/list endpoints for data-minimization and application-scope consistency in a future non-overlapping claim.

Sentinel (account-01-auth-security)
