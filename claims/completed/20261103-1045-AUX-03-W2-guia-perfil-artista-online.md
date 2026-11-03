# Claim — AUX-03 W2: SEO editorial para aquisição de artistas

agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/ecosystem-coordination
area: SEO editorial / public artist discovery / artist acquisition
task: Produce a distinct, product-verified editorial asset that attracts artists and formations searching for an online artistic profile and guides them to activate or claim a Cutinapp profile.
status: DONE — ARTICLE_READY
started_at: 2026-11-03T10:45:00-03:00
completed_at: 2026-11-03T10:48:00-03:00
depends_on: CMS duplicate check and editorial approval
files_or_scope:
- deliverables/AUX-03/20261103-W2-guia-perfil-artista-online.md
- worklogs/20261103-1045-AUX-03-W2-guia-perfil-artista-online.md

## Scope and non-duplication
- Audience: artists, bands, duos, groups, collectives and formations.
- Search intent: online artistic profile, artist profile, band profile, show schedule discovery.
- Distinct from recent participant ticket-safety guide, producer Instagram/event-page articles, W1 producer research Stories and W3 first-event Reel.
- Does not overlap the implementation scope of PR #727 (producer landing SEO metadata) or W09 public production/snapshot code.
- Existing active AUX-03-W2 producer SEO claim remains untouched.

## Confirmed product basis
- Public artist routes and artist onboarding route exist in main.
- Artist profile view supports public identity, biography, genres, location, official links, upcoming confirmed events, history, follow and share.
- Artist onboarding supports searching and claiming an existing profile with evidence, or activating a solo artist identity with minimum fields.
- Artist onboarding requires authenticated session and verified email.
- Pending event invitations are not part of the public lineup until confirmed.
- Activation, account linkage and artist verification are distinct states.
- Formation creation may require curation; the article explicitly avoids promising unrestricted self-service group creation.

## Deliverable
Full article with SEO fields, canonical proposal, internal links, BlogPosting guidance, FAQ, mobile-first publication gate, Instagram carousel copy and Stories sequence.
Commit: b387b13bd9a1c313e30eb633136c816a14d8a53d

## Channel and CTA
Google/blog → /artists → /artist/onboarding → public artist profile → social sharing.
CTA: “Ativar meu perfil artístico”.
Destination: /artist/onboarding.

## Metrics
- CTA clicks / article sessions.
- Artist profile activations / qualified CTA clicks.
- Completed profiles / activated profiles.
- Profile shares / active artist profiles.
- Confirmed event participations / active artist profiles.
Baseline: N/D; no conversions measured.

## Evidence
- Main route definitions: src/App.js.
- Public artist profile: src/pages/artist/ArtistViewPage.js.
- Artist onboarding: src/pages/artist/ArtistOnboardingPage.js.
- Artist editor: src/pages/artist/ArtistManagePage.js.
- SEO route metadata: src/components/SeoManager.js.
- Worklog: worklogs/20261103-1045-AUX-03-W2-guia-perfil-artista-online.md.

## Next action
Account principal/editorial must check CMS for duplicates, create a draft, assign the final canonical URL and approved OG asset, validate login/register/email-verification return to onboarding on mobile, and approve publication. Measure organic sessions, CTA clicks, activations and profile completion after publication.

## Publication state
NOT_IN_CMS — NOT_PUBLISHED — NOT_INDEXED — CONVERSION_NOT_MEASURED.

## Account principal required
YES — CMS access, duplicate check, editorial approval, publication and live funnel QA.

## Execution state
ARTICLE_READY — SOCIAL_COPY_READY — WORKLOG_COMMITTED — NO_PRODUCT_CODE_CHANGE — NO_VPS_CHANGE.
