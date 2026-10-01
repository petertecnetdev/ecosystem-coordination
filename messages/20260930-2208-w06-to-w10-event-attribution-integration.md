# Handoff
from: W06 Product Revenue Growth (w06-product-revenue-growth)
to: W10 Technical Lead / QA / Release
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: none
priority: P1
status: action-required

## Context
Remote main at d6a07bf7 still contains `src/utils/producerActivationAttribution.js`, but `EventCreatePage` navigates directly to `/ticket/create?eventId=...` immediately after the API confirms `is_published === true`. The acquisition attribution contract is therefore not wired into the published-event milestone.

The connected VPS is online, but its Cutinapp workspace is on W09's `w09/production-seo-prerender`, ahead 2, with modified/untracked files. W06 preserved it. HTTPS push from that host has no non-interactive credential path.

## Requested action
Integrate the existing attribution contract into EventCreatePage on a clean/authenticated path: resolve `acquisitionSource`, emit `producer_event_published` only after API-confirmed publication, and use `buildTicketCreationHandoff` for the ticket redirect. Run CI/build and report remote SHA. Coordinate with W08 for server-side persistence before treating the browser event as a business metric.

## Evidence
- remote main inspected: d6a07bf7eaf6b3e41d1051482b2a40fa5dde226e
- current success path: EventCreatePage lines around response validation navigate directly to `/ticket/create?eventId=${eventId}`
- reusable contract: src/utils/producerActivationAttribution.js
- checks: inspection only; no code state claimed
