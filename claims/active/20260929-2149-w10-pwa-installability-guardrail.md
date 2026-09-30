# Claim
agent: W10
display_name: W10 Visual QA
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: production QA / PWA installability
task: add deterministic PWA installability regression guardrail for manifest, service worker registration and required icons
branch: main
status: working
started_at: 2026-09-29T21:49:37-03:00
depends_on: none
files_or_scope:
- package.json
- scripts/check-pwa-installability.js

## Notes
VPS petertecnetserver is offline, so this run uses GitHub/main fallback. Current manifest declares installability fields and /images/logo.png icons, while install flow is delegated to shared install-app.js plus explicit /sw.js registration. Guardrail will prevent silent regressions in these contracts without changing product behavior.