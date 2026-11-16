# Claim — AUX-03 W2 / SEO de perfis públicos de artistas

agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/ecosystem-coordination
area: public artist discovery / crawler-visible snapshots / internal linking
task: Specify an acquisition-focused enrichment of artist snapshots with confirmed upcoming events and public production links; hand off implementation to W09.
status: completed
started_at: 2026-11-16T11:09:00-03:00
completed_at: 2026-11-16T11:09:00-03:00

## Scope
- Research and specification only.
- No claim over scripts/generate-seo-snapshots.mjs.
- W09 retains ownership of crawler snapshot generator and global SEO.
- No product code, branch, PR, merge, build, deploy or runtime change.

## Evidence
- Main SHA: 9b5502cdf2dca098bc73a465d58d7274b596d0a4.
- ArtistViewPage exposes upcoming_events, past_events, pending_events and related productions.
- publicArtist(slug) calls GET /artists/{slug}.
- buildArtistSnapshot emits ProfilePage/Person with only name, image and description.
- eventSchema assigns MusicGroup to every performer without using artist_type.
- Specification: deliverables/AUX-03/20261116-1109-AUX-03-enriquecimento-seo-perfis-artistas.md.

## Result
SPEC_READY — HANDOFF_W09 — NOT_IMPLEMENTED — NOT_MERGED — NOT_DEPLOYED.

NEXT_ACTION: W09 reviews and implements within existing ownership; W00 coordinates review; account principal validates runtime and public URLs.
