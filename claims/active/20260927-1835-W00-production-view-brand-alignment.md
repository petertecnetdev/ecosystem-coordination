# Claim
agent: W00
display_name: Tech Lead
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public Production view brand/visual regression
status: working
started_at: 2026-09-27T18:35:00-03:00

## User evidence
Production public view currently contains purple/blue gradient CTA, violet active tabs/icons, blue/purple legacy accents and translucent/glass styling that conflict with the approved Cutinapp black/graphite/electric-red identity.

## Scope
- src/pages/production/production-view-evolution.css
- src/pages/production/production-experience.css only if required
- preserve behavior, routes and public data
- remove legacy blue/purple visual accents from the public Production view
- use solid black/graphite/red tokens, no decorative opacity/glassmorphism
- improve hero/profile composition, stats, tabs, actions and next-event presentation
- mobile/desktop safe
