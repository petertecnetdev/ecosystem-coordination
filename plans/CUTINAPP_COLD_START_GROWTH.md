# Cutinapp Cold-Start Growth Execution Plan

status: ACTIVE
started_at: 2026-09-30
owner_group: W06-W10

## Objective
Break the zero-user cold start by creating a repeatable loop:

producer -> real event -> public event page -> share/discovery -> participant -> ticket/checkout -> payment -> QR/check-in -> follow/future discovery -> repeat purchase

Goiânia may be used as the initial acquisition-density pilot, but product architecture, localization, currency, timezone, SEO and data models must remain global-ready and must not hardcode Goiânia as product scope.

## Initial 30-day operating targets
These are operating targets, not promises or reported current metrics:
- 30 producers registered
- 20 producers with complete profiles
- 50+ real events published
- 500 participants registered
- 50 real first purchases
- 10 producers with at least one sale
- 5+ events with real check-in usage

Never report these targets as achieved unless supported by real data.

## Priority rule
P0 financial/auth/security/data-integrity/revenue-loss gates keep precedence. Outside active P0 ownership, every W06-W10 cycle must prefer work that directly improves one of:
1. real event supply;
2. producer acquisition/activation;
3. participant acquisition;
4. event-page conversion;
5. ticket/checkout/payment completion;
6. referral/sharing/retention;
7. funnel measurement or operational automation.

Do not spend a cycle on cosmetic P3 while an executable cold-start item exists.

## Workstreams

### W06 — Producer acquisition and activation
- Build the producer cold-start funnel and onboarding offer.
- Reduce time-to-first-published-event.
- Design assisted onboarding so operations can create/setup an event for a producer from flyer/name/date/location/tickets with minimal producer effort.
- Define producer outreach CRM states: prospect -> contacted -> interested -> onboarding -> published -> first sale -> retained.
- Add/maintain Admin Center operational support where configuration should not be hardcoded.
- Measure producer acquisition, activation, time to first event, first sale and trial/paid status when data exists.

### W07 — Public conversion and mobile
- Treat the public Event page as the primary participant acquisition/conversion surface.
- A visitor arriving from WhatsApp/Instagram/Google must be able to understand event, date/time, location, organizer and price immediately.
- Keep the primary CTA dominant: ticket acquisition.
- Avoid requiring login before it is necessary to complete the transaction.
- Implement strong mobile behavior at 320/360/390/430px and validate nav/logo/hamburger regressions.
- Improve post-purchase pathways to ticket/QR, follow producer/artist and discover related events.

### W08 — Growth data, attribution and backend
- Provide server-side funnel events/metrics needed to measure acquisition -> event view -> ticket selection -> checkout -> payment -> ticket issued -> check-in -> repeat.
- Implement generic referral/share attribution when safe: source/referrer/campaign/promo attribution must be reusable rather than tied to one channel.
- Support promoter/referral codes or tracked links only with auditable attribution rules and abuse controls.
- Preserve authorization, idempotency, transactions, integrity and financial correctness.
- Prepare lifecycle/notification backend hooks without sending unauthorized communications.

### W09 — Discovery, SEO, sharing and lifecycle
- Make event/production/artist/venue public pages crawler-visible and shareable.
- Prioritize title/description/canonical/OG/Schema.org/sitemap/robots and high-intent landing surfaces.
- Build reusable city/category/date discovery architecture such as events by city, category, today/weekend, without thin duplicate pages or hardcoded city scope.
- Improve WhatsApp/social previews for events and productions.
- Create reusable acquisition content tied to real inventory: weekend agenda, genre/category discovery, free events, nearby events and producer-facing content.
- Define lifecycle messages for abandoned checkout, upcoming event, ticket access and post-event return subject to consent and channel rules.

### W10 — Growth QA and orchestration
- Ensure growth work is measurable and does not regress purchase, auth, navigation, mobile, SEO or financial safety.
- Keep owner/state/NEXT_ACTION for each growth stream.
- Detect when the team is over-investing in secondary work while the cold-start funnel is stalled.
- Reopen claims when a commit/build does not produce the required functional result.

## Product rules
- Public event pages should work as acquisition landing pages, not require an account merely to view/understand an event.
- Authentication should be requested only when needed for secure transaction/account actions.
- Every event should have a first-class share path and correct preview metadata.
- Every paid event should expose clear pricing and fees before confirmation.
- After purchase, guide the user to ticket/QR and legitimate retention actions such as following relevant entities or discovering related events.
- No fake users, fake purchases, fake engagement, fake scarcity, or invented social proof.

## Acquisition operations outside code
The system should support an assisted launch motion:
1. identify real producers/venues/promoters;
2. collect only the minimum public/commercial information required;
3. offer assisted setup for their next event;
4. publish only with producer authorization and accurate event data;
5. return the public event link and sharing assets;
6. measure views, ticket intent and sales;
7. use results to improve onboarding and retention.

## Measurement
When instrumentation exists, report at least:
- producer prospects/contacts/onboarded/activated;
- published events;
- unique event views;
- share/referral source when attributable;
- ticket-selection rate;
- checkout-start rate;
- payment-success rate;
- tickets issued;
- check-ins;
- repeat visitors/buyers;
- producer first-sale rate;
- trial -> paid, active subscribers, MRR/churn when applicable.

Never invent data. Mark missing instrumentation as a backlog item.

## Definition of progress
Progress must be visible as one or more of:
- real producer/event inventory added with authorization;
- measurable reduction in onboarding friction;
- measurable acquisition/discovery surface shipped;
- conversion/checkout improvement shipped and tested;
- share/referral/lifecycle loop shipped and measured;
- instrumentation added so the funnel can be observed;
- concrete outreach pipeline advanced by a human/operator.

Every cycle ends with evidence, owner, state and NEXT_ACTION.