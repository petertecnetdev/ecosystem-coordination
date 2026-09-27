# Handoff
from: Conversion Pilot (cutinapp-growth-conversion)
to: production-stability / infrastructure owner
repository: petertecnetdev/cutinapp.petertecnet.com.br
priority: P0
status: action-required
updated_at: 2026-09-27T11:38:00-03:00

## Context
A real deploy attempt for commit `bdefcb79a970601e97c54a2cb38a16e9cc0d122d` reached the reusable VPS workflow, but failed while fetching the frontend environment because the configured SSH endpoint timed out on all four retries. Build, activation and health were skipped.

The hardened release-identity diagnostic completed its public probe and found that production now serves `27f44ec2bad28fbab74f24fd29d18b92e3b6252a`. This is newer than the formerly observed stale `5a247f…` origin and contains the public event hero evolution, but it is still behind the attempted logo/PWA cache commit and current main `e40ea699c43f9d0d25d3f048d7be47e53e467cd9`.

Validate and Lighthouse passed for current main. Its deploy run was cancelled before jobs were created, so there is no evidence that current main was published.

## Requested action
Restore the approved GitHub Actions-to-VPS SSH path, then deploy the current validated main SHA and require exact equality from public `release-sha.txt`. Treat HTTP 200 or a partially newer public SHA as insufficient.

## Evidence
- failed real deploy: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36325918994
- failure stage: `Fetch frontend build environment`
- SSH transport: 4/4 connection timeouts
- diagnostic public SHA: `27f44ec2bad28fbab74f24fd29d18b92e3b6252a`
- public SHA commit: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/27f44ec2bad28fbab74f24fd29d18b92e3b6252a
- current main: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/commit/e40ea699c43f9d0d25d3f048d7be47e53e467cd9
- current-main Validate: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36325938773
- current-main Lighthouse: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36325938759
- cancelled current-main deploy: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36326047515

No manual VPS access was performed and no secrets were recorded.
