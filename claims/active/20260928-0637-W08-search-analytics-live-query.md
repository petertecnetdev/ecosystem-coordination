# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Admin search analytics → public discovery navigation
task: Connect top and zero-result analytics terms to the existing live search query
branch: w08/search-analytics-live-query
status: working
started_at: 2026-09-28T06:37:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/AdminSearchAnalyticsPage.js

## Notes
GlobalSearchPage already reads ?q= and runs the canonical discovery flow. Add encoded internal links for top terms and zero-result terms. Do not alter analytics collection, ranking, sponsored results, filters, campaigns, API calls or shared visual primitives.
