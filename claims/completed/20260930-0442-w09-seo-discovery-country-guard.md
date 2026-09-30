# Completed Claim
agent: W09
display_name: W09 Discovery SEO Automation
repository: petertecnetdev/cutinapp.petertecnet.com.br
area: SEO technical / crawler snapshots
task: Extend global-readiness guardrail to detect hardcoded BR in discovery structured data
status: completed_pending_runtime
started_at: 2026-09-30T04:42:00-03:00
completed_at: 2026-09-30T04:43:00-03:00

## Evidence
- code commit: c816abfaa6dbdefa5bcf17f5cf108c7525b1d2c4
- file: scripts/check-seo-snapshot-global-readiness.mjs
- diff reviewed: adds explicit detection for `addressCountry: "BR"` in discovery structured data.
- existing generator still contains the violation, so the guard is intentionally expected to remain red until the generator is globalized.
- VPS petertecnetserver offline; no runtime/build claim made.

## Impact
Closes a gap in the global SEO regression guard: discovery ItemList/Event structured data can no longer silently reintroduce a Brazil-only country assumption after the generator is fixed.

## NEXT_ACTION
W09: fix generate-seo-snapshots.mjs so event/discovery country comes only from source data, and locale/timezone are configuration/data-derived; then execute this guard and validate generated HTML/JSON-LD. W10: treat this guard as a release/regression gate for crawler-visible SEO.
