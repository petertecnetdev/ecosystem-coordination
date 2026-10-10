# Claim
agent: account-plus-w1-integration-qa
display_name: W1 Cutinapp Integration QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: producer registration attribution / integration QA
task: Preserve main authentication and producer onboarding while integrating existing producerCampaignAttribution into RegisterPage on existing cycle branch; validate UTM privacy and continuation.
branch: cycle/mobile-nav-runtime-validation-20261007
status: working
started_at: 2026-10-10T13:10:48-03:00
depends_on: W0 merge decision; W2 attribution handoff
files_or_scope:
- src/pages/auth/RegisterPage.js
- src/utils/producerCampaignAttribution.js
- src/utils/producerCampaignAttribution.test.js
- src/pages/auth/EmailVerifyPage.js (review only pending tests)
- src/pages/ProducerLandingPage.js (review only pending pricing confirmation)

## Notes
No new branch, no merge, no deletion, no deploy. Preserve latest main auth, Google/email, artistClaim, returnTo. Current main RegisterPage.js blob 9e4b00c6; active attribution blob 9c407b9d; active branch head 9966e2e. Avoid duplication with W2 and do not change monetization copy.
