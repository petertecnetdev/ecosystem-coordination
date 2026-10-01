# Cutinapp Producer Outreach Pipeline

status: ACTIVE
owner: W06 Product Revenue Growth
scope: cold-start producer acquisition and assisted activation

## Objective
Turn real producer prospects into authorized, published event supply and first sales with the least possible producer effort. This operating pipeline supports a local density pilot (including Goiânia when useful) but never makes a city a product-level hardcoded scope.

## Canonical stages
`prospect -> contacted -> interested -> onboarding -> published -> first_sale -> retained`

A record may also be `lost` or `paused`. Stage changes must be timestamped. Do not count a producer in a later stage unless the transition evidence exists.

### prospect
Entry criteria: identifiable real producer, venue or promoter with public/commercial contact path and plausible upcoming-event fit.
Required evidence: public source URL or operator note identifying the organization.
Next action: make a compliant first contact.

### contacted
Entry criteria: an outreach attempt was actually sent/made.
Required fields: `contacted_at`, `channel`, `operator`, `next_action_at`.
Exit: response/interest, explicit decline, or follow-up policy exhausted.

### interested
Entry criteria: producer explicitly indicates interest in Cutinapp or agrees to evaluate assisted setup.
Required fields: `interest_at`, `contact_name_or_role`, `preferred_channel`, `next_action_at`.
Next action: collect the minimum event data needed for assisted onboarding.

### onboarding
Entry criteria: producer authorized setup and supplied enough information to create/complete its Cutinapp presence.
Minimum event packet: producer/brand name, event name, date/time, location, ticket/free-entry model, public flyer/image when authorized, contact for validation.
Required fields: `onboarding_started_at`, `authorization_evidence`, `assigned_operator`, `next_action_at`.
Rule: never publish guessed dates, prices, capacity, venue details or unauthorized creative assets.

### published
Entry criteria: at least one real event is publicly accessible and producer-authorized.
Required evidence: `producer_id`, `event_id`, public event URL, `published_at`.
Next action: return the link/share asset to the producer and configure/verify sellable tickets when applicable.

### first_sale
Entry criteria: backend-confirmed successful real purchase/payment attributable to the producer/event; free registrations do not masquerade as paid sales.
Required evidence: server-side order/payment identifier and `first_sale_at` where policy permits storing the reference.
Next action: help producer use operational value (ticket access/check-in/sales visibility) and prepare retention follow-up.

### retained
Entry criteria: objective repeat-value evidence, such as another authorized event, renewal/paid subscription when applicable, or repeat operational use under a defined retention window.
Required fields: `retained_at`, `retention_signal`.

### lost / paused
`lost`: explicit rejection, invalid fit, unreachable after policy, or disqualifying condition. Record `loss_reason`; do not spam.
`paused`: valid opportunity with a future timing dependency. Record `resume_at`.

## Minimum data contract
Use a generic CRM/entity implementation rather than Cutinapp-only tables if/when persisted in product infrastructure.

Required operational fields:
- `app_slug` (`cutinapp` initially)
- `prospect_type` (`producer`, `venue`, `promoter`)
- `organization_name`
- `country_code`, `region`, `city` as dynamic location fields
- `source_type` and `source_ref` (public URL, referral, inbound, operator research)
- `stage`, `stage_changed_at`
- `preferred_channel` and business contact reference; minimize personal data
- `assigned_operator`
- `next_action_at`, `last_contact_at`
- `producer_id`, `event_id` when linked
- `acquisition_source`, `campaign` when legitimately attributable
- `loss_reason`, `notes` with no secrets/sensitive unnecessary data
- timestamps for each achieved stage

Do not put credentials, private tokens, sensitive personal notes or scraped private data into coordination files.

## Transition rules
1. Every active record must have one owner and one `next_action_at`.
2. `contacted` requires an actual attempt, not an intention to contact.
3. `interested` requires producer response/consent, not operator inference.
4. `onboarding` requires authorization before creating/publishing on the producer's behalf.
5. `published` requires a real public event URL and accurate event data.
6. `first_sale` requires durable backend confirmation; browser telemetry alone is insufficient.
7. `retained` requires a defined repeat-value signal; elapsed time alone is insufficient.
8. Stage regression is allowed when evidence changes, but must preserve history/audit.

## Operating SLA defaults
These are operating defaults, not performance claims:
- new qualified prospect: first action within 1 business day;
- interested producer: onboarding next action within 4 business hours when staffed;
- complete authorized event packet: target assisted setup within 1 business day;
- published event: share link returned to producer immediately after verification;
- first sale: retention/operations follow-up within 1 business day;
- paused opportunities: no contact before `resume_at` unless producer initiates.

## Assisted onboarding playbook
1. Qualify a real producer/venue/promoter and record public source.
2. Contact with a concise value proposition: Cutinapp can assist setup of the next event and return a ready-to-share event page.
3. On explicit interest, request only the minimum event packet.
4. Create/link the producer account and event through authorized product/Admin Center workflows; do not bypass permissions.
5. Producer validates event facts and commercial terms.
6. Publish and verify public page, ticket configuration, pricing/fees and share preview.
7. Return the public link and sharing asset.
8. Observe server-side views/intent/checkout/payment only where instrumentation exists.
9. After first real sale/use, follow up around operational value and the next event/trial-to-paid path.

## Metrics contract
Report counts only from evidence-backed records:
- prospects created;
- contacted producers;
- interested producers;
- onboarding started;
- producers with first event published;
- median/percentile time from interest to published event when timestamps exist;
- producers with first real sale;
- first-sale time from publication;
- retained producers;
- stage conversion rates with denominator and period;
- trial -> paid, active subscriptions, MRR/churn only from billing truth.

Never substitute targets for actuals. Never infer payment success from client-side navigation.

## Admin Center / backend requirements
Recommended generic implementation path for W08/Admin Center when capacity is available:
- reusable `growth_leads`/CRM domain keyed by `app_id` or `app_slug`, not a Cutinapp-only schema;
- immutable stage-transition history;
- authorization by operator role/app scope;
- searchable pipeline by stage, owner, next action and dynamic location;
- idempotent linkage to existing user/production/event entities;
- activity log for contact attempts and consent/authorization evidence references;
- server-side milestone hooks for event published, first successful payment and retention signals;
- dashboard derived from durable data, never hardcoded counters.

## Cold-start queue policy
When no P0/P1 release gate is available to W06, work the queue in this order:
1. interested producers waiting for onboarding;
2. onboarding records blocked before publication;
3. published paid events without verified sellable ticket setup;
4. published events needing share handoff;
5. qualified prospects awaiting first contact;
6. contacted prospects whose compliant follow-up is due;
7. first-sale producers due retention follow-up.

## Success criterion
This pipeline is successful when an operator can identify the next producer action without manual archaeology, each stage is evidence-backed, assisted onboarding reduces work to a small verified event packet, and the system can eventually calculate acquisition -> publication -> first-sale -> retention from durable records.
