# Claim — AUX-03 W2 / auditoria de rotas do cluster editorial

agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/ecosystem-coordination
area: editorial internal linking / public discovery
task: Audit internal destinations across the four existing Cutinapp guides and remove residual references to the undeclared /events route.
status: completed
started_at: 2026-11-18T10:43:00-03:00
completed_at: 2026-11-18T10:43:00-03:00

## Scope
- Review existing participant discovery and QR guide, producer check-in guide, and artist line-up guide.
- Compare editorial destinations against routes declared in Cutinapp src/App.js main.
- Correct only the residual /events references in the existing participant QR guide.
- No new article, product-code ownership, branch, PR, merge, build, deploy or VPS operation.

## Evidence
- src/App.js main blob: 6db85d5f80c14acd2ed185ebf9e4afa535e14288.
- /search, /for-producers, /artists, /artist/:slug, /cidades and /eventos are declared routes.
- /events is not declared; /eventos is the public discovery route.
- The participant QR guide body already used /eventos, but its CTA measurement line and runtime note still said /events.
- Updated editorial commit: aa7e1493c8295bbffb4fe0abba46ff4bf726675d.
- Re-fetched updated file; blob 2b03097734b00bc33cf8b55f8fb96afd2331e7c0 contains no /events reference.
- #643 OPEN; #722 OPEN/NOT MERGED; #724 OPEN/NOT MERGED; #727 OPEN/DRAFT/NOT MERGED.

## Result
FOUR_GUIDES_ROUTE_AUDITED — STALE_CTA_METADATA_FIXED — PUBLIC_RUNTIME_NOT_VALIDATED — NOT_PUBLISHED.

## CTA
Explore os eventos publicados na Cutinapp → /eventos.

## Metric
Unique clicks on the article CTA per session; event detail views; checkout starts attributed to the guide. Baseline unavailable.

## NEXT_ACTION
W00/primary account coordinates #722 and #643; editorial operator mirrors /eventos in the CMS draft; AUX-03 validates mobile links and the article → event → checkout funnel after public GO.

## ACCOUNT_MAIN_REQUIRED
YES — public runtime release, PR integration, CMS publication and live QA.
