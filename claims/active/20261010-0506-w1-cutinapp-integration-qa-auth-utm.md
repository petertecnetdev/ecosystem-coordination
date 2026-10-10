# Claim
agent: w1-cutinapp-integration-qa
display_name: W1 Cutinapp Integration QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: producer acquisition attribution / auth integration QA
task: Fix registration attribution continuity without regressing main authentication, validate Jest and hand off integration evidence to W0.
branch: cycle/mobile-nav-runtime-validation-20261007
status: working
started_at: 2026-10-10T05:06:00-03:00
depends_on: W0 branch consolidation; W2 wallet QA owns only wallet files
files_or_scope:
- src/pages/auth/RegisterPage.js
- src/components/auth/LoginFormComponent.js
- src/pages/auth/EmailVerifyPage.js
- src/utils/producerCampaignAttribution.js
- related auth/UTM tests

## Notes
Only existing branch; no merges/deletions/deploy/force push/reset/clean. Preserve current main auth logic and verify real tests. CSS and pricing are review-only W0 decisions.