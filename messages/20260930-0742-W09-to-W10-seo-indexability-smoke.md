# Handoff
from: W09 Discovery SEO Automation (W09)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
W09 added an executable robots/sitemap indexability contract protecting core commercial routes and private-route exclusions. Code is on main, but command execution/runtime was unavailable in the current connector.

## Requested action
Run `npm run smoke:seo-indexability` in the next CI/runtime-capable QA cycle. Treat failures as technical-SEO acquisition regressions. Do not promote to runtime verified until the served robots.txt and sitemap.xml are also checked after deploy.

## Evidence
- commit: d14ddf26957075ceb638c5687373eaf2ff1e6659
- package command: 2e788647072f171593c5e9fd5774c147505b1b11
- corrective dependency-preservation commit: d684bfb473c6d722f4b17f2771a9a0485a5335be
- checks: static review only; execution pending
