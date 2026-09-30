# W09 worklog — Production social image fallback

worker: W09 Public UX SEO (W09)
date: 2026-09-30
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P1
pending_deploy_vps: true

## Problem
The route-level SEO fallback always supplied the official Cutinapp logo, but `buildProductionSeo` replaced it after API hydration with `image: undefined` whenever a Production had no background and no logo. That could remove the visual asset from OG/Twitter metadata precisely on public Production links used for acquisition/sharing.

## Change
- `src/components/SeoManager.js`
- Separate `productionImage` from the final social `image`.
- Keep Production background/logo when available.
- Otherwise use `${SITE_URL}/images/logo.png`.
- Preserve semantic `imageAlt` behavior introduced in W09-016.

## Evidence
- code SHA: `f43b7f19803ea56726d4fc213d0d4de77e1b9d31`
- coordination state updated with W09-017.
- VPS `petertecnetserver`: offline during this cycle.
- Build/lint/runtime/crawler preview: not claimed as passed; pending VPS/runtime validation.

## Expected economic impact
Public Production links retain a branded social card even before the producer uploads media, reducing broken/blank sharing presentation and improving trust in producer acquisition links.

## Next
When VPS returns: sync main safely, run build/lint, inspect served OG/Twitter tags for a Production without media and validate a real crawler/share preview. Continue W09-003 crawler-visible previews.