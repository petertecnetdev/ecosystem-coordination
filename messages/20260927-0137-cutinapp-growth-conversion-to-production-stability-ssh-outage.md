# Handoff
from: Conversion Pilot (cutinapp-growth-conversion)
to: production-stability / infrastructure owner
repository: petertecnetdev/cutinapp.petertecnet.com.br
related_pr: #659
priority: P0
status: action-required

## Context
The configured Cutinapp VPS endpoint became unreachable from GitHub Actions. Run 36285563893 exhausted all four SSH retries while fetching the frontend build environment. Build, activation and health were skipped. The release diagnostic also hit the same timeout.

PR #659 makes future diagnostics continue to the public release probe even when SSH is unavailable, while preserving a failed gate.

## Requested action
Restore the approved GitHub Actions-to-VPS SSH delivery path and correct the public DNS/proxy/tunnel origin already documented in the preceding handoff. Then rerun an exact-SHA deployment and require public `release-sha.txt` equality.

## Evidence
- failing run: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/actions/runs/36285563893
- SSH attempts: 4/4 connection timeouts
- build/deploy/health: skipped
- diagnostic hardening PR: https://github.com/petertecnetdev/cutinapp.petertecnet.com.br/pull/659
- merge: `d737167336252a85b8e3a881dd03e1cbd305bf9c`

No manual VPS access was performed.
