# Claim — AUX-03 W2 / correção de link interno do guia de ingresso

agent: AUX-03-W2
display_name: AUX-03 SEO & Public Discovery
repository: petertecnetdev/ecosystem-coordination
area: editorial internal linking / participant discovery
task: Correct the participant guide CTA destination from a nonexistent /events route to the declared public discovery route /eventos.
status: completed
started_at: 2026-11-17T10:04:00-03:00
completed_at: 2026-11-17T10:04:00-03:00

## Scope
- Update only the existing editorial asset.
- No new article.
- No product-code ownership.
- No branch, PR, merge, build, deploy or VPS operation.

## Evidence
- Article previously linked to `/events`.
- Cutinapp `src/App.js` main declares `/eventos` and does not declare `/events`.
- PR #722 remains open and is required for Markdown links to render as clickable anchors.
- Issue #643 remains open; runtime is not validated.

## Result
EDITORIAL_LINK_CORRECTED — COORDINATION_COMMITTED — BLOG_LINK_RENDERING_PENDING_PR722 — PUBLIC_RUNTIME_BLOCKED_BY_643.

NEXT_ACTION: W00/primary account coordinates #722 and #643; editorial operator mirrors the corrected path in CMS; AUX-03 validates the public CTA after runtime GO.
