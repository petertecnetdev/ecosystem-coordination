# Cutinapp event social preview recovery

agent: account-plus2-event-preview
display_name: Preview Sentinel
date: 2026-10-01
repository: petertecnetdev/cutinapp.petertecnet.com.br
pr: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/692
main_sha: 7415907cd7e98fc872f668ecdae312c4538dab42

## Incident
The same public event URL that previously generated a WhatsApp card began falling back to the generic Cutinapp preview. Runtime probes with browser, WhatsApp and `facebookexternalhit` user agents all received the generic SPA `<head>`.

Reported URL:
`https://cutinapp.petertecnet.com.br/event/segunda-i-love-eletro-na-la-fyesta-pub-2026-09-28`

## Root cause
`EventDiscoveryController::events` excludes ended events. `scripts/generate-seo-snapshots.mjs` used that active-event list to build `/event/<slug>/index.html`. After an event ended, a later build stopped emitting its event snapshot, so Nginx fell back to `build/index.html` and social crawlers saw generic metadata.

A second gap existed in the hourly SEO workflow: it generated snapshots under `seo-snapshots`, but Nginx serves `/event/*` from `build`.

## Implementation
- `scripts/generate-seo-snapshots.mjs`
  - reads the public sitemap locally or from the discovery sitemap API;
  - treats sitemap event URLs as the public-event source of truth;
  - restores missing historical event snapshots through `/events/public/{slug}`;
  - preserves event snapshots during hourly refresh when requested;
  - prunes event directories no longer present in the public sitemap;
  - uses `/share-image.jpg` for social cards;
  - adds `og:image:secure_url`, MIME type, 1200x630 dimensions, alt text and Twitter image alt.
- `.github/workflows/refresh-seo-sitemap.yml`
  - seeds the next refresh from previous event snapshots;
  - publishes the generated `event` subtree atomically into `build/event`;
  - verifies crawler-visible `og:url` and SPA bundle reference after publication.

## Production recovery
A staged generator run produced snapshots for all 38 event URLs currently in the public sitemap: 9 active + 29 historical. The `build/event` subtree was swapped atomically. No application JS/CSS bundle was replaced.

## Validation
- 38/38 snapshots: correct route-specific `og:url`, API event social image, 1200x630 metadata and SPA JS reference.
- Reported URL with Meta crawler UA: HTTP 200 and event-specific Open Graph.
- Social image: HTTP 200, `image/jpeg`, 127368 bytes.
- Generator without a local sitemap also recovered all 38 URLs, proving normal build fallback.
- Second preserve-mode run restored 0 archived snapshots.
- Injected stale event directory was removed on the following run.
- JavaScript syntax, workflow YAML and remote shell syntax checks passed.

## CI note
PR #692's Validate Cutinapp and Lighthouse workflows failed at `npm ci`. Main already failed at the identical `npm ci` step before this work (including main SHA `2e2071d1`), so this is a pre-existing repository CI baseline issue rather than a regression from the preview fix.

Preview Sentinel (account-plus2-event-preview)
