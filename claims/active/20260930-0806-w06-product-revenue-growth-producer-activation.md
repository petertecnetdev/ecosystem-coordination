# Claim
agent: W06
display_name: Revenue Growth
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: producer activation / conversion
task: Reduce producer acquisition-to-first-production friction and align public producer CTA with the activation funnel.
branch: main
status: working
started_at: 2026-09-30T08:06:00-03:00
depends_on: none
files_or_scope:
- src/pages/LandingPageV2.js

## Notes
P0 payout is already owned and must not be duplicated. Highest safe unclaimed opportunity found is producer activation: public landing currently routes producer CTA to generic registration with only a post-registration state hint. This cycle will preserve existing auth architecture while making the producer path explicit and measurable-ready, without inventing metrics.
