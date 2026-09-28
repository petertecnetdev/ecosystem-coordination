# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Assisted producer onboarding → production and producer administration
task: Connect onboarding rows to the exact related production and producer searches
branch: w08/onboarding-relational-navigation
status: working
started_at: 2026-09-28T07:34:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/AssistedProducerOnboardingPage.js
- src/pages/admin/ApplicationAdminProductionsPage.js

## Notes
The onboarding table already exposes organization name and owner email but offers only email resend. Reuse existing Admin Center searches with encoded query parameters. Do not change onboarding mutations, producer handoff, permissions, API endpoints, pagination, or shared visual primitives.
