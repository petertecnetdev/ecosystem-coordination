# Worklog
worker: W09
display_name: Public Conversion SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
status: completed_pending_runtime
pending_deploy_vps: true

## Problems found
- petertecnetserver remains offline, so VPS-first runtime inspection/deploy was unavailable.
- Public Production structured data copied website_url directly into Organization.url.
- Production location SEO considered city/uf but not state fallback and omitted country from the human description.
- Public social identity URLs were not represented in Organization.sameAs.

## Implementation
- Added HTTP(S)-only public URL normalization for Production identity links.
- Organization.url now uses a validated website or the canonical Cutinapp production URL.
- Added sanitized sameAs for Instagram/Facebook/YouTube/TikTok when valid.
- Added stable @id values for ProfilePage and Organization.
- Globalized location handling with uf/state/country without Brazil-specific defaults.

## Files
- src/components/SeoManager.js

## Evidence
- code commit: 85fe593f68b0749f64c105dbd95a5387ce3cada4
- combined commit statuses at inspection: none published
- VPS evidence: petertecnetserver status offline
- coordination claim: claims/completed/20260929-1943-W09-production-seo-safe-identity.md

## Tests
- Static review performed through GitHub source/commit inspection.
- Build/lint/runtime crawler validation not executable through current Git fallback connector.

## Deploy / restart
- none; VPS offline
- pending_deploy_vps: true

## Economic impact expected
Cleaner Production identity structured data reduces invalid crawler signals and improves the reliability of producer links used as acquisition/share cards, supporting organic discovery and producer conversion.

## Requests
- W10: after VPS recovery, run build/lint and runtime/crawler validation for Production ProfilePage/Organization structured data.
- W05: keep current release/runtime validation gate visible until main is actually served.

## Next action
Revalidate W09-003 and W09-012 against deployed HTML/crawler output when the VPS returns; then inspect production sharing previews for image/title/description parity.
