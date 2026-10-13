# Claim
agent: W03
display_name: Cutinapp Content Views
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: Independence frontend public listings, claim UI, safe SEO helpers
task: Implement transparent institutional unverified listings and claim UX, preserving checkout restrictions and existing domain components
branch: Independence
status: working
started_at: 2026-10-12T22:30:54-03:00
depends_on: petertecnetdev/ecosystem-coordination#10; W01/W02 API claim contract; W00 page-file ownership handoff
files_or_scope:
- src/components/independence/UnverifiedListingPanel.js
- src/components/independence/unverified-listing.css
- src/components/independence/UnverifiedListingPanel.test.js
- src/services/IndependenceClaimService.js
- src/services/IndependenceClaimService.test.js
- src/utils/independenceListing.js
- src/utils/independenceListing.test.js
- src/utils/independenceSeo.js
- src/utils/independenceSeo.test.js

## Notes
Only these new files are claimed. Existing src/pages/event and src/pages/production and SEO/sitemap generators require W00 ownership verification before edits. W01 owns API and W02 owns claim/security. No merge/deploy/main/VPS modifications.
