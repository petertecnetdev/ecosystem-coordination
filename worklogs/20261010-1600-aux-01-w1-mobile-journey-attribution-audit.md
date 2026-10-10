# AUX-01 W1 — Mobile journey / acquisition attribution audit
Date: 2026-10-10
Priority: P1
Repository main: 337c9ba22a4b97f9bd8d48f09b695105a954f43f

## Result
Static review found that campaign query parameters can be lost between public discovery and signup:
- `EventDiscoverySeoPage.js` links to `/event/:slug` without preserving the current query string.
- `EventPage.js` strips all query keys outside `city`, `uf`, `date`, `kind`, and `page`, which removes UTM parameters.
- `RegisterPage.js` reads acquisition source from navigation state or the current URL query.
- The inspected `telemetry.js` code captures feed and checkout-recovery attribution, but does not parse UTM parameters at app entry.

Expected journey: campaign link -> discover event -> event detail -> register/checkout -> event activation.
Observed statically: discovery navigation can discard the source before registration reads it. Impact is primarily funnel measurement/attribution; no lost sale was demonstrated.

## Priority assessment
- Severity: P1 for acquisition-funnel measurement reliability.
- Frequency: every tagged visit through the affected discovery routes unless attribution is captured elsewhere.
- Impact: medium; source-level signup and downstream conversion reports may be incomplete.
- Difficulty: low-medium; requires a shared, allowlisted session attribution contract and route-level regression tests.

## Coordination
- Read protocol, COMMANDS, CURRENT_STATE, PRIORITIES, BLOCKERS, AUX-01 registry/inbox, active claims and relevant recent worklogs/messages.
- Did not duplicate payout P0, PWA, mobile checkout, wallet QA, QR, event-price, navigation, or existing auth/UTM claims.
- Sent an action-required handoff to the current auth/UTM integration owner and W0.
- No application code changes were made because attribution work is already claimed.
- Live site was inaccessible via the available runtime check; no mobile browser test was possible.
- No tests were run in this static-only cycle. No deploy, VPS operation, pull, merge, or destructive change.

## Next action
Owner should capture allowlisted UTM attribution before route sanitization and test:
1. `/eventos?utm_source=instagram` -> event CTA -> registration;
2. `/event?utm_source=instagram` -> filter update -> registration;
3. query-only changes on RegisterPage;
4. source remains stable through checkout/producer activation without forwarding arbitrary query parameters.

Handoff: `messages/20261010-1600-aux-01-w1-to-w1-integration-qa-event-discovery-utm.md`.
