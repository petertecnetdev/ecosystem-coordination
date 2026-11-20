# Claim — AUX-03 W2 / sitemap dinâmico de páginas públicas

agent: AUX-03-W2
display_name: AUX-03 Organic Growth & Public Discovery
repository: petertecnetdev/ecosystem-coordination
area: SEO / public discovery / dynamic sitemap
task: Confirm the gap between generated public SEO snapshots and the static sitemap; prepare an implementation specification and hand off shared-generator ownership to W09.
priority: P2
status: completed
started_at: 2026-11-20T10:37:00-03:00
completed_at: 2026-11-20T10:37:00-03:00

## Scope
- Read coordination state, priorities, blockers, worker registry and recent AUX-03 work.
- Inspect Cutinapp main sitemap, robots, snapshot generator and indexability smoke.
- Avoid duplicating 07/11 empty city-period noindex handoff and 08/11 public agenda snapshot handoff.
- Produce a distinct dynamic-sitemap specification and acceptance criteria.
- Do not edit shared W09 generator without explicit ownership acceptance.

## Evidence
- Frontend main: 6db85d5f80c14acd2ed185ebf9e4afa535e14288.
- Snapshot generator: b94de8800be96b236faff3cc08539f986cab55fd.
- Static sitemap: 2b64332876a613f354de221264eb5dfbe0bbb53a.
- Indexability smoke: d7364471440b4675074efd5445ee3df14a844009.
- Generated public snapshots cover event, production, blog, artist and discovery routes; generator does not write dynamic sitemap.
- public/sitemap.xml has seven core URLs only.
- Search Console not accessed; no claim of deindexation or traffic loss.

## Result
DYNAMIC_SITEMAP_GAP_CONFIRMED — SPEC_READY — HANDOFF_W09_W00 — NO_PRODUCT_CODE_CHANGED.

## Channel and CTA
Google Search → public dynamic pages → event page.
CTA: Ver evento e ingressos, subject to real availability; producer CTA only after runtime GO.

## Primary metric
Organic clicks to dynamic event pages from impressions of dynamic URLs.

## NEXT_ACTION
W09 reviews/accepts scope and implements dynamic sitemap from the same eligible snapshot inventory. W00 coordinates with prior empty-period and agenda handoffs. Main account/operator submits sitemap in Search Console after runtime GO; AUX-03 validates submitted/discovered/indexed URLs.

## ACCOUNT_MAIN_REQUIRED
YES — coordinate W09 shared-generator ownership and provide Search Console validation after publication.
