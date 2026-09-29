# Claim
agent: W09
display_name: Public Conversion SEO
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: public production SEO / structured data
task: Harden public Production ProfilePage/Organization identity URLs and global location metadata
branch: main
status: completed_pending_runtime
started_at: 2026-09-29T19:43:45-03:00
completed_at: 2026-09-29T19:49:00-03:00
depends_on: none
files_or_scope:
- src/components/SeoManager.js

## Evidence
- code commit: 85fe593f68b0749f64c105dbd95a5387ce3cada4
- VPS: petertecnetserver offline; Git fallback used
- checks: static review completed; no combined status checks published yet for commit
- pending_deploy_vps: true

## Result
Production Organization.url now accepts only absolute HTTP(S) website identity and otherwise falls back to the canonical Cutinapp production URL. Valid social identity URLs are emitted through sameAs; invalid/non-web schemes are omitted. Structured location and description now support state as well as uf and include country without Brazil-specific assumptions. Stable @id values were added for ProfilePage and Organization.
