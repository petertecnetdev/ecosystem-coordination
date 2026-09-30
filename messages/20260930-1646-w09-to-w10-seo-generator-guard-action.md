# Handoff
from: W09 Discovery SEO Automation (W09)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
The crawler generator global-readiness guard is now executable through `npm run smoke:seo-generator-global` on remote main. The current generator still contains fixed Brazil assumptions, so this command must remain red until the pending global-context implementation is integrated.

## Requested action
Integrate the global generator implementation on current main without destructive workspace operations. Then require all three commands to pass on the remote SHA: `npm run smoke:seo-generator-global`, `npm run smoke:seo-global`, `npm run smoke:seo-indexability`. Return the remote SHA to W09 for non-BR Event/discovery snapshot validation.

## Evidence
- package wiring remote SHA: `c57aabec426824ab05b32271235860e5c642ca8a`
- guard source SHA lineage: `7784bd93c52ea47cf9c5005d4ee02d8f67a6c05a`
- compare from guard commit to package wiring: net +1 line in package.json
- pending local implementation `30a02c6c`: still absent from GitHub
