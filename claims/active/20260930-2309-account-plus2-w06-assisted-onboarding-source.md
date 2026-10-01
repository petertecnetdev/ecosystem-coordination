# Claim
agent: account-plus2-w06-product-revenue-growth
display_name: W06 Product Revenue Growth
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: producer acquisition / assisted onboarding
task: preserve acquisition source when operations create a producer through assisted onboarding
branch: main
status: working
started_at: 2026-09-30T23:09:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/AssistedProducerOnboardingPage.js

## Notes
Cold-start P1. The assisted onboarding form creates real producer supply but currently has no acquisition-source field, preventing operations from attributing producer acquisition. Add a generic optional source value to the existing payload without hardcoding Goiânia/channel-specific behavior.
