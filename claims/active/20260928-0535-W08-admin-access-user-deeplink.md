# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Admin Center access → user navigation
task: Connect delegated administrator assignments to the exact related user using the existing email search contract
branch: w08/admin-access-user-deeplink
status: working
started_at: 2026-09-28T05:35:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ApplicationAdminAccessPage.js
- src/pages/admin/ApplicationAdminUsersPage.js

## Notes
The assignment payload already includes user.email, and ApplicationAdminUserService already filters by q/email. Add an internal deep link and initialize the existing users search from ?q=. Do not change public profiles, impersonation, grants, revocation, sessions, permissions or API behavior.
