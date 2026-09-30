# Worklog — W09
worker: W09 Discovery SEO Automation
date: 2026-09-30T07:42:00-03:00
priority: P1
repository: petertecnetdev/cutinapp.petertecnet.com.br

## Problem
robots.txt and sitemap.xml are acquisition-critical but had no executable contract preventing accidental removal of commercial routes, wrong canonical origin, duplicate/query sitemap URLs, private-route leakage, or loss of the Sitemap directive.

## Implementation
Added scripts/check-seo-indexability.mjs and exposed npm run smoke:seo-indexability. The guard protects six core public routes, canonical sitemap origin, private-route exclusions, duplicate URLs and query/hash leakage.

## Evidence
- d14ddf26957075ceb638c5687373eaf2ff1e6659 — guard implementation
- 2e788647072f171593c5e9fd5774c147505b1b11 — package command
- d684bfb473c6d722f4b17f2771a9a0485a5335be — corrective commit restoring the existing source-map-loader version after an update-file typo; final dependency state preserved
- current public/robots.txt advertises https://cutinapp.petertecnet.com.br/sitemap.xml and includes the protected private prefixes
- current public/sitemap.xml contains /, /for-producers, /eventos, /productions, /artists and /blog
- command execution/runtime unavailable in connector; no false test/build/deploy/runtime claim

## Impact
Protects organic acquisition and commercial indexability from silent robots/sitemap regressions. It does not replace the pending dynamic snapshot global-readiness fix.

## State
IMPLEMENTED: yes
COMMITTED: yes
PUSHED: yes (GitHub contents API on main)
MERGED: main updated directly
BUILT: not verified
DEPLOYED: not verified
RUNTIME VERIFIED: no

## NEXT_ACTION
Execute npm run smoke:seo-indexability in CI/runtime. Then fix generate-seo-snapshots.mjs timezone/locale/country/organizer root causes, run smoke:seo-global, generate a non-BR snapshot and hand crawler-visible validation to W10.
