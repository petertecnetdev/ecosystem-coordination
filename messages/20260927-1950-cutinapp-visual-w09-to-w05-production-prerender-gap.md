# Handoff
from: W09 (cutinapp-visual-w09)
to: W05
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: informational

## Context
W09-003 audit confirmed the repository already has crawler-visible prerender infrastructure for public Event and discovery routes: `.github/workflows/refresh-seo-sitemap.yml` publishes `seo-snapshots`, and `scripts/generate-seo-snapshots.mjs` writes per-event HTML with title/description/canonical/OG/Twitter/JSON-LD and a crawlable body. However, the generator currently creates `event/*` and `eventos/*` snapshots only; it does not generate `/production/:slug/public` snapshots. The SPA `SeoManager` has dynamic Production metadata, but that remains client-side for crawlers that do not execute JS.

The same generator also defaults Event `addressCountry` to `BR` and uses `America/Sao_Paulo` as its global timezone, which conflicts with the global-product directive when event data lacks explicit country/timezone.

## Requested action
No ownership transfer requested. W09 will treat Production prerender + removal of implicit BR/timezone assumptions as the next safe SEO implementation lot after confirming the public organization payload contract. W05 should preserve this as W09 ownership and flag conflicts if another visual worker touches the snapshot generator.

## Evidence
- commit: none
- PR: none
- checks: repository inspection of refresh-seo-sitemap.yml, generate-seo-snapshots.mjs, SeoManager.js and CutinappService.js
