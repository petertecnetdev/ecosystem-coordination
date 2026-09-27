# Worklog — ViewForge (W01)

repository: petertecnetdev/cutinapp.petertecnet.com.br
claim: claims/active/20260927-1401-W01-event-production-views.md
priority: P1
status: implemented-awaiting-runtime-validation

## User-prioritized batch
- Re-read the canonical coordination repository and W01/W04/W05 ownership before implementation.
- Re-read application main immediately before integration and preserved concurrent commit `3239477b` rather than overwriting its red/graphite identity work.
- Confirmed the prior failure mode: global `production-public-polish.css` loaded before lazy page CSS, while `production-experience.css` and `production-view-evolution.css` repeatedly redefined the same selectors with `!important`.

## Implementation
- Rebuilt the public Production header with isolated `cut-production-public-profile__*` classes so legacy selectors no longer decide the computed layout.
- Bounded the cover to 220–320px desktop and 190–240px mobile, separated identity from media, aligned logo/title/location/producer and removed the oversized overlay block.
- Reordered actions around the commercial/agenda CTA, kept follow/share secondary and removed Bootstrap blue/purple presentation.
- Consolidated the duplicated four KPI cards into one readable header metric row.
- Added a solid, privacy-aware viewers modal with larger identity/visit metadata and an explicit close control.
- Added route-specific sticky tabs with >=44px targets and a clear red active state.
- Replaced the second oversized event banner with reusable `ProductionNextEventHero` compact-card CSS; flyer uses `object-fit: contain`, with date/location/price and primary/secondary CTAs.
- Added a W01-specific black/red WhatsApp share variant while preserving W04's shared overlay positioning contract.
- The compact next-event component is shared by Public/Create/Edit, improving parity without editing W04 primitives.

## Evidence
- application main commit: `172a0375c5977f482f7fdb9f00a4dd88f91158d4`
- changed: `ProductionPublicPage.js`, `production-public-profile.css`, `ProductionNextEventHero.js`, `ProductionNextEventHero.css`, production regression guard
- production build: compiled successfully; 18 SEO snapshots generated
- tests: 138 suites / 850 tests passed
- guards: production-view 29/29, overlays, dialogs, React stability and UX regressions passed
- source contract: new layout styles contain no `!important`, `rgba()` or decorative gradients
- runtime: cloud browser could not access the local loopback server; 390/1366/1920 production visual evidence remains pending

## Delivery gate
- `Validate Cutinapp #2850`: successful for `172a0375`.
- `Lighthouse CI #762`: successful for `172a0375`.
- `Deploy VPS #1744`: failed; all four SSH attempts from the GitHub-hosted runner timed out.
- Diagnostic job confirmed the configured VPS SSH endpoint was unavailable and public HTTPS still served `99fe15cb9b035804f1eee7b5ab6ad336875eeff7`.
- Result: code is integrated and validated on main, but not published to production; W01-008 remains IMPLEMENTED, not VERIFIED.

## Economic impact
A denser, clearer public Production page exposes agenda/ticket intent earlier, removes off-brand trust friction and keeps visitors navigating into events rather than confronting a second oversized banner.

## Next
1. Confirm CI/deploy and identify public SHA `172a0375` or newer.
2. Validate `/production/la-fyesta-pub/public` anonymously at 390/1366/1920 and inspect authenticated owner/follower state when available.
3. Keep W01-008 IMPLEMENTED until those runtime checks pass; continue Create/Edit header parity afterward.
