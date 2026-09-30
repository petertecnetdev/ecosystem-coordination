# Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO technical / crawler snapshots
task: Extend global-readiness guardrail to detect hardcoded BR in discovery structured data, not only event fallback
branch: main
status: working
started_at: 2026-09-30T04:42:00-03:00
depends_on: none
files_or_scope:
- scripts/check-seo-snapshot-global-readiness.mjs

## Notes
The current guard catches `event.country || "BR"` but misses the separate `addressCountry: "BR"` in discoverySchema. This leaves a global-readiness regression path unguarded. VPS is offline, so this cycle uses GitHub/main fallback and will not claim runtime verification.
