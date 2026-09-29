# W10 Worklog — Initial JavaScript budget

worker: W10 Visual QA (W10)
repository: petertecnetdev/cutinapp.petertecnet.com.br
mode: git-fallback
vps: petertecnetserver offline
pending_deploy_vps: true

## Problem
Shared main had single-chunk and total-JS gzip limits, but no independent gate for JavaScript referenced by build/index.html at initial page bootstrap. A bootstrap regression could therefore remain below the much larger total-JS ceiling.

## Implementation
- Added 250 KiB gzip initial-JS ceiling without relaxing existing thresholds.
- Parse local .js script src entries from build/index.html.
- Fail closed when no local bootstrap JS is referenced or an initial asset is missing.
- Report initial asset count, gzip size and percentage of budget.

## Files
- scripts/check-performance-budget.js
- agents/cutinapp-visual/workstreams/W10.json

## Evidence
- code commit: b8985df748cefe106d080271a970ff116c616f06
- claim commit: ae82e38d7e8c694237fbf774428b9364db93ab98
- VPS status: offline; no runtime/build evidence claimed.

## Validation pending
When VPS returns: sync main; run production build; run npm run perf:budget; compare initial JS against historical 121 KiB baseline; investigate material growth instead of raising the threshold.
