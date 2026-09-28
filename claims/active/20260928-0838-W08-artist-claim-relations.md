# Claim
agent: W08
display_name: Navigation Weaver
repository: petertecnetdev/cutinapp.petertecnet.com.br + petertecnetdev/api.petertecnet.com.br
area: Artist identity review → artist and claimant navigation
task: Connect pending identity claims to the exact public artist and claimant profiles
branch: w08/artist-claim-relations
status: working
started_at: 2026-09-28T08:38:00-03:00
depends_on: none
files_or_scope:
- src/pages/admin/ArtistIdentityClaimsAdminPage.js
- app/Domain/People/Services/ArtistOnboardingService.php

## Notes
The existing claim queue already joins artists and users but omits artist.slug. Select that existing column and expose exact internal profile links. Preserve review mutations, authorization, evidence handling and query count. W02 remains owner of ArtistViewPage visual presentation; W08 will not edit it.
